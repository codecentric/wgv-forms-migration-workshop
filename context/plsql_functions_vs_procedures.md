# PL/SQL Functions vs. Procedures

## Übersicht

In PL/SQL (und SQL allgemein) sind Functions und Procedures beide gespeicherte Programmeinheiten, haben aber wichtige Unterschiede. Dieses Dokument trennt **Sprachspezifikation** (MUST/MUST NOT) von **Best Practices** (SHOULD).

## Sprachspezifikation (Harte Regeln)

### Function - Spezifikationsregeln

- **MUST** einen Return-Typ in der Signatur deklarieren: `RETURN datatype`
- **MUST** mindestens ein `RETURN`-Statement ausführen
- **CAN** in SQL-Ausdrücken aufgerufen werden (Fähigkeit, keine Pflicht)
- **CAN** DML-Operationen (INSERT/UPDATE/DELETE) ausführen - *nicht verboten durch Spezifikation*

### Procedure - Spezifikationsregeln

- **MUST NOT** einen RETURN-Typ haben
- **CAN** OUT oder IN OUT Parameter haben (optional)
- **CANNOT** direkt in SQL-Ausdrücken aufgerufen werden (Einschränkung)
- **CAN** DML-Operationen (INSERT/UPDATE/DELETE) ausführen
- **CAN** nichts tun - leere Procedures sind valide

### Beispiel: Technisch valide, aber schlechte Praxis

```sql
-- VALIDE aber SCHLECHTE PRAXIS: Function mit Side Effects
CREATE OR REPLACE FUNCTION bad_function(p_id NUMBER)
RETURN NUMBER
IS
BEGIN
  -- Function macht INSERT - legal aber schreckliche Praxis!
  INSERT INTO audit_log VALUES (p_id, SYSDATE);
  COMMIT; -- Auch legal aber sehr schlecht!
  RETURN 1;
END;

-- VALIDE: Procedure die nichts macht
CREATE OR REPLACE PROCEDURE empty_procedure
IS
BEGIN
  NULL; -- Macht nichts - vollkommen legal!
END;
```

## Best Practices (Konventionen, nicht erzwungen)

Diese sind **Konventionen**, keine Sprachregeln:

- **Functions SHOULD**: Side-effect-frei sein, kein DML, deterministisch
- **Procedures SHOULD**: Aktionen ausführen (DML, Business-Logik)

### Warum "No Side Effects" für Functions?

Weil Functions in SQL-Queries verwendet werden können und der **SQL Optimizer** Annahmen trifft:
- Kann die Function mehrfach aufrufen oder Ergebnisse cachen
- Kann sie gar nicht aufrufen, wenn das Ergebnis nicht benötigt wird
- Ausführungsreihenfolge ist unvorhersehbar

```sql
-- Wenn diese Function Side Effects hat (INSERT), wie oft wird sie ausgeführt?
SELECT vertrag_id, bad_function(vertrag_id)
FROM vertrag
WHERE bad_function(vertrag_id) > 0;  -- 2x pro Row? 1x? Unvorhersehbar!
```

## RETURN Value vs. OUT Parameter - Technischer Unterschied

### RETURN Value (nur Functions)

```sql
CREATE FUNCTION get_premium(p_id NUMBER) RETURN NUMBER IS
BEGIN
  RETURN 100.50; -- Einzelner skalarer Wert
END;

-- Verwendung:
DECLARE
  v_result NUMBER;
BEGIN
  v_result := get_premium(123);  -- Assignment
END;
```

### OUT Parameter (Procedures und Functions)

```sql
CREATE PROCEDURE get_contract_info(
  p_id IN NUMBER,
  p_premium OUT NUMBER,        -- Erster Output
  p_status OUT VARCHAR2,       -- Zweiter Output
  p_customer OUT customer_rec  -- Komplexer Typ als Output
) IS
BEGIN
  p_premium := 100.50;
  p_status := 'ACTIVE';
  p_customer := some_record;
  -- Kein RETURN Statement
END;

-- Verwendung:
DECLARE
  v_prem NUMBER;
  v_stat VARCHAR2(20);
  v_cust customer_rec;
BEGIN
  get_contract_info(123, v_prem, v_stat, v_cust);  -- Pass by reference
  -- v_prem, v_stat, v_cust sind jetzt befüllt
END;
```

### Unterschiede im Detail

| Aspekt | RETURN | OUT Parameter |
|--------|--------|---------------|
| **Anzahl** | Genau einer | Mehrere erlaubt |
| **Erlaubte Typen** | Jeder einzelne Wert | Jeder Typ, inkl. Collections/Records |
| **Syntax** | `v := func()` | `proc(in, out1, out2)` |
| **Verfügbar in** | Nur Functions | Beide (aber Procedures können kein RETURN haben) |
| **Funktionsweise** | Value copy | Reference/Pointer Modifikation |

## Code-Beispiele

### PL/SQL Function

```sql
-- Berechnet und gibt einen Wert zurück
CREATE OR REPLACE FUNCTION calculate_premium(
  p_vertrag_id IN NUMBER
) RETURN NUMBER
IS
  v_premium NUMBER;
BEGIN
  SELECT praemie INTO v_premium
  FROM vertrag
  WHERE vertrag_id = p_vertrag_id;
  
  RETURN v_premium * 1.19; -- mit Steuer
END;

-- Kann in SQL verwendet werden:
SELECT vertrag_id, calculate_premium(vertrag_id) as total_premium
FROM vertrag;
```

### PL/SQL Procedure

```sql
-- Führt eine Aktion aus
CREATE OR REPLACE PROCEDURE update_vertrag_status(
  p_vertrag_id IN NUMBER,
  p_new_status IN VARCHAR2,
  p_success OUT NUMBER  -- OUT Parameter statt RETURN
)
IS
BEGIN
  UPDATE vertrag
  SET status = p_new_status,
      updated_at = SYSDATE
  WHERE vertrag_id = p_vertrag_id;
  
  p_success := SQL%ROWCOUNT; -- Anzahl aktualisierter Rows
  COMMIT;
END;

-- Muss als Standalone Statement aufgerufen werden:
DECLARE
  v_success NUMBER;
BEGIN
  update_vertrag_status(123, 'ACTIVE', v_success);
END;
```

## WGV ICIS Kontext

Wenn die Dokumentation **"Service-Stored Procedures"** erwähnt, sind damit wahrscheinlich gemeint:
- **Procedures**, die Business-Logik kapseln (Vertrag anlegen, Prämie berechnen, etc.)
- Diese werden über die **Integration Layer** (Spring Boot oder ORDS) exponiert
- Die REST API wird diese Procedures über JDBC/SimpleJdbcCall aufrufen

### Typische WGV Service Procedure

```sql
-- Typische WGV Service Procedure
CREATE OR REPLACE PROCEDURE PKG_VERTRAG.create_vertrag(
  p_vertragsnummer IN VARCHAR2,
  p_versicherungssumme IN NUMBER,
  p_vertrag_id OUT NUMBER,  -- Gibt generierte ID zurück
  p_error_code OUT NUMBER,  -- Gibt Status-Code zurück
  p_error_msg OUT VARCHAR2  -- Gibt Fehlermeldung zurück
) IS
BEGIN
  -- Business Logic mit DML
  INSERT INTO vertrag (
    vertragsnummer,
    versicherungssumme,
    created_at
  ) VALUES (
    p_vertragsnummer,
    p_versicherungssumme,
    SYSDATE
  )
  RETURNING vertrag_id INTO p_vertrag_id;
  
  p_error_code := 0;
  p_error_msg := 'SUCCESS';
  COMMIT;
EXCEPTION
  WHEN OTHERS THEN
    p_error_code := SQLCODE;
    p_error_msg := SQLERRM;
    ROLLBACK;
END;
```

**Beachte:**
- **Procedure** (nicht Function) - weil sie DML + COMMIT macht
- **Mehrere OUT Parameter** - gibt ID, Status-Code und Fehlermeldung zurück
- Dies ist **korrekte Verwendung** gemäß Spezifikation und Best Practices

### Spring Boot Integration Layer Beispiel

```java
// Aufruf einer PL/SQL Procedure aus Java
SimpleJdbcCall jdbcCall = new SimpleJdbcCall(jdbcTemplate)
    .withCatalogName("PKG_VERTRAG")
    .withProcedureName("CREATE_VERTRAG")
    .declareParameters(
        new SqlParameter("p_vertragsnummer", Types.VARCHAR),
        new SqlParameter("p_versicherungssumme", Types.NUMERIC),
        new SqlOutParameter("p_vertrag_id", Types.NUMERIC),
        new SqlOutParameter("p_error_code", Types.NUMERIC),
        new SqlOutParameter("p_error_msg", Types.VARCHAR)
    );

Map<String, Object> result = jdbcCall.execute(
    Map.of(
        "p_vertragsnummer", "V-2026-001234",
        "p_versicherungssumme", 500000.00
    )
);

Integer vertragId = (Integer) result.get("p_vertrag_id");
Integer errorCode = (Integer) result.get("p_error_code");
String errorMsg = (String) result.get("p_error_msg");

if (errorCode != 0) {
    throw new BusinessException(errorMsg);
}
```

## Zusammenfassung

### Harte Spezifikationsregeln (MUST)

| Feature | Function | Procedure |
|---------|----------|-----------|
| **RETURN-Typ deklarieren** | MUST | MUST NOT |
| **RETURN-Statement** | MUST (mindestens 1x) | MUST NOT |
| **In SQL-Statements verwendbar** | CAN (erlaubt) | CANNOT (verboten) |
| **OUT Parameter** | CAN (optional) | CAN (optional) |
| **DML Operations** | CAN (aber nicht empfohlen) | CAN (normal) |

### Best Practices (SHOULD)

| Aspekt | Function | Procedure |
|--------|----------|-----------|
| **Primärer Zweck** | Berechnungen | Business-Operationen |
| **Side Effects** | Idealerweise keine | Ja (DML-Operationen) |
| **COMMIT/ROLLBACK** | Nicht empfohlen | Üblich |
| **Verwendung** | In SQL-Expressions | Als Standalone Calls |

### Fazit für WGV-Projekt

Für das WGV-Projekt werden wahrscheinlich hauptsächlich **Procedures** aufgerufen, da sie Business-Operationen ausführen (Verträge anlegen, Policen aktualisieren, etc.), nicht nur Werte berechnen.

Die Integration Layer (Spring Boot oder Oracle ORDS) wird diese Service-Stored Procedures als REST APIs exponieren.
