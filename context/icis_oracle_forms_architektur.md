# ICIS Oracle Forms Architektur - Interpretation

**Quelle-Diagramm**: `diagrams/icis_oracle_forms_architektur.svg`  
**Autor**: Fatih Acikgöz  
**Datum**: 05.05.2022  
**Typ**: Detail-Schaubild (Detaillierte Architekturdarstellung)

## Übersicht

Das Diagramm zeigt die **aktuelle Oracle Forms Architektur** des ICIS-Systems. Diese Architektur repräsentiert den Legacy-Zustand, der im Rahmen der WGV-Modernisierung teilweise abgelöst werden soll.

## Architektur-Komponenten

### 1. Client Layer
- **Forms Java Client**: Oracle Forms Client-Anwendung, die in Java läuft

### 2. Application Server Layer
Die mittlere Schicht besteht aus mehreren Komponenten:
- **[ weblogic-server ]**: WebLogic Server als Application Server
- **[ forms-runtime ]**: Oracle Forms Runtime-Umgebung
- **[ icis-forms ]**: ICIS-spezifische Forms-Anwendung
- **[ Oracle-FSAL ]**: Oracle Forms Server Application Layer

### 3. Oracle Forms Architektur (Java VM)
Die klassische Oracle Forms 3-Schichten-Architektur **innerhalb des Middle-Tiers**:
- **UI Presentation**: Darstellungsschicht für Benutzeroberflächen
- **Application Logic**: Ausführung der Geschäftslogik (Forms-Trigger, Program Units)
  - ⚠️ **Führt aus**: PL/SQL-Code **in den Forms** (Trigger, Program Units aus FMB-Dateien)
  - **Quelle**: Oracle Forms Services Architecture Dokumentation (14.1.2)
- **Data Manager**: Datenzugriff und -verwaltung
  - ⚠️ **WICHTIG**: Der Data Manager ist Teil des **Middle-Tiers** (Application Server)
  - **Aufgabe**: Sendet SQL-Queries und Aufrufe zu **Database Stored Procedures** via SQL Net
  - **Verwaltet**: Cursor, Fetch-Operationen, Client-seitige Transaktionszustände

**Hinweis zur 3-Tier-Architektur**: Die drei Layer "UI Presentation", "Application Logic", "Data Manager" sind **nicht** drei separate Tiers, sondern interne Komponenten des **Middle-Tiers** (Forms Runtime Process).

### 4. Database Layer
- **SQL Engine**: Verarbeitet SQL-Statements (SELECT, INSERT, UPDATE, DELETE)
- **PL/SQL Engine**: Datenbank-seitige PL/SQL-Ausführung
  - ⚠️ **WICHTIG**: Der PL/SQL Engine ist Teil des **Database-Tiers** (läuft IN der Oracle Database)
  - **Aufgabe**: Führt **Database Stored Procedures, Functions, Packages** AUS
  - **Empfängt**: SQL/PL/SQL-Aufrufe vom Data Manager (Middle-Tier)
  - **Gibt zurück**: Ergebnisse (Result Sets, OUT-Parameter) an Data Manager
- **Datenbank ICIS**: Die zentrale ICIS-Datenbank

### 5. Datenbank-Komponenten
Die Datenbank enthält:
- **Datenbank-Tabellen**: Persistente Datenspeicherung
- **Packages**: PL/SQL-Packages mit Geschäftslogik
- **Views**: Datenbank-Views
- **FMX-Dateien**: Kompilierte Forms-Module

### 6. Service Procedures
Das Diagramm zeigt verschiedene Service-Procedure-Abkürzungen:
- **BSP, BSV**: Wahrscheinlich Business Service Procedures/Views
- **DSP, DSV**: Wahrscheinlich Data Service Procedures/Views
- **GSP**: Wahrscheinlich General Service Procedures
- **TSP**: Wahrscheinlich Transaction Service Procedures

## Kommunikation

- **Http Request**: Kommunikationsprotokoll zwischen Client und Application Server
- **SQL Net**: Oracle Datenbank-Netzwerkprotokoll zwischen Application Server und Datenbank

## Relevanz für die Modernisierung

Diese Architektur zeigt den **aktuellen Zustand (Legacy)**, der modernisiert werden soll:

### Was bleibt unverändert:
- ✅ **Database PL/SQL Engine**: Die Geschäftslogik in Database PL/SQL bleibt erhalten (Database-Tier)
- ✅ **Datenbank ICIS**: Oracle DB und Datenmodell bleiben unverändert
- ✅ **Packages/Service-SPs**: Die Service-Stored Procedures (BSP, DSP, GSP, TSP) werden weiterhin genutzt

### Was wird ersetzt:
- ❌ **Forms Java Client**: Wird durch moderne Web-Frontends (React/Angular) ersetzt
- ❌ **UI Presentation & Application Logic**: Werden durch neue Frontend- und Integration-Layer ersetzt
- ❌ **Forms Runtime & ICIS-Forms**: Oracle Forms wird schrittweise abgelöst
- ❌ **Data Manager**: Wird durch REST API-Schicht (Integration Layer) ersetzt
- ❌ **Forms PL/SQL** (Trigger, Program Units): Geschäftslogik wird migriert zu:
  - Frontend (React/Angular) für UI-Logik
  - Integration Layer (Spring Boot) für Orchestrierung
  - Eventuell neue Database Stored Procedures (falls Business-Logik)

### Neue Komponenten (geplant):
- **Integration Layer**: REST API-Schicht (Spring Boot oder Oracle ORDS) zwischen Frontend und PL/SQL
  - **Ersetzt**: Data Manager (übernimmt Rolle des Datenzugriffs)
  - **Kommuniziert mit**: PL/SQL Engine (wie zuvor Data Manager)
- **Modern Frontend**: React/Angular-basierte Webanwendungen
- **AI Integration**: AI Gateway für Conversational UI und AI-Agents

### Warum die Tier-Unterscheidung wichtig ist für die Modernisierung:

**Verständnis der Migration (mit PL/SQL-Typen)**:
```
Legacy (3-Tier):
Client (Forms) 
  → Middle (Forms Runtime)
      ├─ Forms PL/SQL (Trigger, Program Units) ← WIRD MIGRIERT
      └─ Data Manager → Database (DB PL/SQL Engine) ← BLEIBT

Modern (3-Tier bleibt!):
Client (React/Angular) 
  → Middle (Spring Boot API)
      ├─ Business Logic (Java) ← ERSETZT Forms PL/SQL
      └─ REST API → Database (DB PL/SQL Engine) ← BLEIBT!
```

**Kritische Erkenntnisse**:
1. **Database PL/SQL bleibt** (Database-Tier): Stored Procedures (BSP, DSP, GSP, TSP) werden weiter genutzt
2. **Forms PL/SQL wird migriert** (Middle-Tier → verschiedene Ziele):
   - UI-Logik → Frontend (React/Angular)
   - Business-Logik → Spring Boot Services
   - Validierungslogik → Frontend + Backend (je nach Bedarf)
3. **Data Manager wird ersetzt**: Spring Boot REST API (Middle-Tier) übernimmt Rolle
4. **3-Tier-Struktur bleibt erhalten**: Nur Technologien ändern sich, nicht die Architektur-Pattern

**Workshop-Relevanz (Tag 2)**:
- **Diskussion Integrationsschicht**: "Wie ersetzen wir den Data Manager durch REST APIs?"
- **Wiederverwendbarkeit**: "Database PL/SQL Engine bleibt → Stored Procedures (BSP, DSP, etc.) können weiter genutzt werden"
- **Forms PL/SQL Migration**: "Wo migrieren wir Forms-Trigger hin? Frontend, Backend, oder Database?"
- **Deployment**: "Middle-Tier wird von WebLogic zu Kubernetes migriert, Database-Tier bleibt"

**Migrations-Entscheidungen (Tag 1 & 2)**:
- **Forms PL/SQL-Analyse**: Welche Trigger enthalten UI-Logik (→ Frontend) vs. Business-Logik (→ Backend)?
- **Code-Reuse-Strategie**: Können Forms Program Units zu Database Stored Procedures werden?
- **Testbarkeit**: Forms PL/SQL war oft schwer testbar → moderne Architektur verbessert dies

---

## Quellen & Verifizierung

### Offizielle Oracle-Dokumentation

**Primärquelle**: Oracle Forms Services Architecture (14.1.2)
- URL: https://docs.oracle.com/en/middleware/developer-tools/forms/14.1.2/working-forms/oracle-forms-services-architecture.html
- Datum der Verifizierung: 2026-04-16
- Relevante Zitate:
  - "For each Oracle Forms session, there is one Oracle Forms Runtime process on the application server."
  - "It also manages the database connection; queries and updates data; **runs any PL/SQL in the form; executes triggers**"
  - Forms Runtime Process hat "dual role": Server (für Client) und Client (für Database)

**Wichtige Klarstellung basierend auf Oracle-Dokumentation**:
- ✅ **Forms PL/SQL** (Trigger, Program Units) wird im **Forms Runtime Process** ausgeführt (Middle-Tier)
- ✅ **Database PL/SQL** (Stored Procedures, Packages) wird im **Database PL/SQL Engine** ausgeführt (Database-Tier)

Diese Unterscheidung ist kritisch für das Verständnis der ICIS-Architektur und die Planung der Modernisierung.

---

**Letzte Aktualisierung**: 2026-04-16  
**Verifiziert gegen**: Oracle Forms Services Architecture Documentation 14.1.2  
**Status**: Korrigiert basierend auf offizieller Oracle-Dokumentation

## Architektur-Muster

Das Diagramm zeigt eine klassische **3-Tier Oracle Forms Architektur**:

### Die drei Tiers (physische Schichten):

1. **Client Tier** (Thin Client):
   - Forms Java Client (läuft im Browser mit Java Plugin)
   - Nur Darstellung (Rendering), keine Geschäftslogik
   - Kommunikation mit Middle-Tier via HTTP

2. **Middle Tier** (Application Server):
   - WebLogic Application Server
   - Forms Runtime (Forms Services)
   - **Interne 3 Layer** (alle laufen im Middle-Tier):
     - UI Presentation
     - Application Logic (Forms-Trigger, FMB-Logik)
     - Data Manager (sendet SQL/PL/SQL-Calls an Datenbank)
   - Kommunikation mit Database-Tier via SQL Net

3. **Database Tier**:
   - Oracle Database
   - **SQL Engine** (verarbeitet SQL-Statements)
   - **PL/SQL Engine** (führt Stored Procedures aus)
   - Datenbank-Tabellen, Packages, Views

### Wichtige Klarstellung: Data Manager vs. PL/SQL Engine

| Komponente | Tier | Aufgabe |
|------------|------|---------|
| **Data Manager** | Middle-Tier | **Sendet** SQL/PL/SQL-Calls, verwaltet Cursor client-seitig |
| **PL/SQL Engine** | Database-Tier | **Führt aus** Stored Procedures, Functions, Packages |

**Kommunikationsfluss (mit beiden PL/SQL-Typen)**:
```
Forms Client 
  → (HTTP) → 
Forms Runtime Process (Middle-Tier)
  → UI Presentation 
    → Application Logic
      ├─→ Führt Forms PL/SQL aus (Trigger, Program Units) ← Forms PL/SQL Engine
      └─→ Data Manager 
          → (SQL Net / JDBC) → 
          Oracle Database (Database-Tier)
            → Database PL/SQL Engine ← Database PL/SQL Engine
              → Führt Stored Procedure aus (BSP, DSP, GSP, TSP)
                → Ergebnis zurück an Data Manager
```

**Wichtig**: 
- **Forms PL/SQL** (Trigger) läuft im **Forms Runtime** (Middle-Tier)
- **Database PL/SQL** (Stored Procedures) läuft im **Database Server** (Database-Tier)

### Architektur-Einordnung

Diese Architektur ist typisch für Oracle Forms Anwendungen aus den 2000er Jahren und repräsentiert eine bewährte, aber veraltete Technologie, die nun modernisiert werden soll.

---

## Häufige Missverständnisse

### ❌ Missverständnis 1: "UI Presentation, Application Logic, Data Manager sind drei Tiers"

**Falsch!** Diese drei sind **interne Layer des Middle-Tiers** (alle laufen in der Forms Runtime im Application Server).

**Richtig**: Es gibt nur **3 Tiers**: Client, Middle (mit internen Layern), Database.

---

### ❌ Missverständnis 2: "Alle PL/SQL-Ausführung ist im Database-Tier"

**Falsch!** Es gibt **zwei verschiedene PL/SQL-Ausführungsumgebungen**:

**Richtig - PL/SQL läuft in ZWEI Tiers**:

| PL/SQL-Code | Wo gespeichert | Wo ausgeführt | Tier |
|-------------|----------------|---------------|------|
| **Forms PL/SQL** (Trigger, Program Units) | FMB-Datei | Forms Runtime Process | **Middle-Tier** |
| **Database PL/SQL** (Stored Procedures, Packages) | Oracle Database | Oracle Database PL/SQL Engine | **Database-Tier** |

**Quelle**: Oracle Forms Services Architecture Documentation 14.1.2:
> "It [Forms Runtime Process] also manages the database connection; queries and updates data; **runs any PL/SQL in the form; executes triggers**"

**Wichtig für ICIS-Modernisierung**:
- Forms-Trigger (z.B. WHEN-BUTTON-PRESSED) laufen im **Middle-Tier**
- Service Stored Procedures (BSP, DSP, GSP, TSP) laufen im **Database-Tier**

---

### ❌ Missverständnis 3: "Data Manager führt alle PL/SQL aus"

**Falsch!** Der Data Manager hat eine spezifische Rolle.

**Richtig - Data Manager's Aufgaben**:
- ✅ Führt **Forms PL/SQL** aus (Trigger, Program Units) → im Forms Runtime Process (Middle-Tier)
- ✅ **Sendet Aufrufe** zu Database Stored Procedures → an PL/SQL Engine (Database-Tier)
- ✅ Verwaltet Cursor, Fetch-Operationen, Client-seitige Transaktionen

**Analogie**: 
- Forms Runtime (inkl. Data Manager) = Koch (kocht selbst + bestellt Zutaten von Lieferant)
- Database PL/SQL Engine = Lieferant (liefert Zutaten auf Bestellung)

---

### ❌ Missverständnis 4: "Es gibt nur einen PL/SQL Engine"

**Falsch!** Es gibt zwei separate PL/SQL-Execution-Engines:

**Richtig**:
1. **Forms PL/SQL Engine** (Teil des Forms Runtime Process, Middle-Tier)
2. **Database PL/SQL Engine** (Teil der Oracle Database, Database-Tier)

**Beweis**: 
- Wenn Sie Oracle Database stoppen → Database PL/SQL Engine stoppt, aber Forms kann weiterhin Forms-Trigger ausführen (solange keine DB-Calls)
- Wenn Sie nur Application Server stoppen → Forms PL/SQL Engine stoppt, Database PL/SQL Engine läuft weiter

---

### ✅ Korrekte Tier-Zuordnung (Zusammenfassung)

| Komponente | Tier | Läuft auf Server | PL/SQL-Typ |
|------------|------|------------------|------------|
| Forms Java Client | Client-Tier | Client-Maschine (Browser) | - |
| WebLogic Server | Middle-Tier | Application Server | - |
| Forms Runtime Process | Middle-Tier | Application Server | - |
| UI Presentation | Middle-Tier | Application Server (in Forms Runtime) | - |
| Application Logic | Middle-Tier | Application Server (in Forms Runtime) | **Forms PL/SQL** ✅ |
| Data Manager | Middle-Tier | Application Server (in Forms Runtime) | - |
| **Forms Trigger** (z.B. WHEN-BUTTON-PRESSED) | **Middle-Tier** | **Application Server** (in Forms Runtime) | **Forms PL/SQL** ✅ |
| **Forms Program Units** (Prozeduren/Funktionen im FMB) | **Middle-Tier** | **Application Server** (in Forms Runtime) | **Forms PL/SQL** ✅ |
| SQL Engine | Database-Tier | Datenbank-Server | - |
| **Database PL/SQL Engine** | **Database-Tier** | **Datenbank-Server** | **Database PL/SQL** ✅ |
| **Stored Procedures** (BSP, DSP, GSP, TSP) | **Database-Tier** | **Datenbank-Server** (ausgeführt vom DB PL/SQL Engine) | **Database PL/SQL** ✅ |
| **Packages** | **Database-Tier** | **Datenbank-Server** (ausgeführt vom DB PL/SQL Engine) | **Database PL/SQL** ✅ |
| Datenbank-Tabellen | Database-Tier | Datenbank-Server | - |

**Legende**:
- **Forms PL/SQL**: PL/SQL-Code in FMB-Dateien (Trigger, Program Units) - ausgeführt im Middle-Tier
- **Database PL/SQL**: PL/SQL-Code in der Datenbank (Stored Procedures, Packages) - ausgeführt im Database-Tier
