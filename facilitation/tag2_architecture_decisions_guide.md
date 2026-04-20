# Tag 2: Architecture & Technology Decisions - Facilitator Guide

**Workshop**: WGV ICIS Modernisierung  
**Zielgruppe**: Architekten, Developer, (optional: Nutzer wenn neugierig - wird aber technisch)  
**Dauer**: ~6.5 Stunden (ohne Pausen) = 7-8 Stunden Arbeitstag  
**Ansatz**: Strukturierte Technologiebewertung + Kollaboratives Architektur-Design

---

## Zielsetzung

Am Ende von Tag 2 haben wir:

✅ **Verfeinerter MVP-Scope** mit 3-5 validierten Masken  
✅ **Service-Stored-Procedure-Katalog** für MVP-Masken (Signaturen dokumentiert)  
✅ **Technologie-Entscheidungen** (ADR-Format):
   - Integration Layer: Spring Boot / ORDS / Hybrid  
   - Deployment: VMs / Docker / Kubernetes / Azure Container Apps  
   - AI Integration Pattern: MCP / Spring AI / Direct / Hybrid  
✅ **Architektur-Diagramm** (Draft) der Zielarchitektur  
✅ **Identifizierte Risiken** und offene technische Fragen  

**Output für Tag 3**: Technologiestack ist definiert, Architektur validiert → Frontend-Framework-Wahl und AI-Driven Dev Workshop können starten

---

## Zeitplan Übersicht - Tag 2

| Zeit | Aktivität | Dauer | Miro Frame | Type |
|------|-----------|-------|------------|------|
| 09:00-09:30 | Recap Tag 1 & Scope-Verschärfung | 30 min | - | Discussion |
| 09:30-10:45 | Service/Stored Procedures Präsentation (WGV) | 1h 15min | ⚠️ **Missing** | INPUT + structured Q&A |
| ☕ **Pause** | | 15 min | - | - |
| 11:00-12:00 | Technische Machbarkeitsanalyse MVP-Masken | 1h | ⚠️ **Missing** | CAPTURE |
| 12:00-13:00 | **Mittagspause** | 1h | - | - |
| 13:00-14:00 | Integration Layer Vergleich & Entscheidung | 1h | Frame 8 + 9 | INPUT + CAPTURE |
| 14:00-14:45 | Deployment-Optionen Vergleich & Entscheidung | 45 min | Frame 10 + 11 | INPUT + CAPTURE |
| ☕ **Pause** | | 15 min | - | - |
| 15:00-16:00 | AI-Integration Patterns Diskussion | 1h | Frame 13 | INPUT + CAPTURE |
| 16:00-17:00 | Architektur-Diagramm (kollaborativ) | 1h | Frame 12 | CAPTURE |

**Gesamtzeit**: 6h 30min + 1h 30min Pausen = **8 Stunden**

**⚠️ Timing-Risiken**:
- Service/SP-Präsentation könnte überlaufen (viele Fragen)
- Architektur-Diagramm könnte zu Diskussionen führen
- **Mitigation**: Parking Lot rigoros nutzen, Timeboxing strikt

---

## ⚠️ WICHTIG: Miro Board Lücken

Die aktuelle Miro Board 3 Struktur hat **keine Frames** für:
1. **Service/Stored Procedures Analyse** (1h 15min im Agenda)
2. **Technische Machbarkeitsanalyse** (1h im Agenda)

**Empfehlung vor Workshop**:
- **Option A**: Neue Frames hinzufügen (Frame 7a, 7b zwischen Tag 1 und Tag 2)
- **Option B**: In Frame 9 (Integration Layer Decision) integrieren
- **Option C**: Als Notebook/Dokument extern führen, Ergebnisse in Miro referenzieren

**Für diese Anleitung**: Gehe ich davon aus, dass wir **zusätzliche Capture-Bereiche** schaffen (siehe Templates unten).

---

## ⚠️ WICHTIG: Activity Order Deviation from Committed Agenda

**TO VERIFY WITH COLLEAGUES & CLIENT:**

This guide **does not follow** the exact activity order from the committed agenda (`2026-04-15_Entwurf_Agenda_v3.md`).

**Committed Agenda Order (Lines 32-50):**
1. Recap Tag 1 & Verschärfung des Scopes (30 min)
2. Vorstellung bestehender Services / Stored Procedures (1h 15min)
3. Technische Machbarkeitsanalyse (1h)
4. **Integration von AI ins System** (1h) ← **Position 4**
5. **Diskussion von Ansätzen für die Integrationsschicht** (1h) ← **Position 5**
6. Diskussion von Deploymentansätzen (45min)
7. Entwurf eines möglichen Architekturdiagramms (1h)

**This Guide's Order:**
1. Recap Tag 1 & Scope-Verschärfung (30 min)
2. Service/Stored Procedures Präsentation (1h 15min)
3. Technische Machbarkeitsanalyse (1h)
4. **Integration Layer Vergleich & Entscheidung** (1h) ← **Position 4 (swapped)**
5. **Deployment-Optionen** (45min) ← **Position 5 (swapped)**
6. **AI-Integration Patterns Diskussion** (1h) ← **Position 6 (swapped)**
7. Architektur-Diagramm (1h)

**Rationale for Deviation (to discuss):**
- Logical flow: Discuss Integration Layer → Deployment → AI Integration (builds on infrastructure decisions)
- AI Integration discussion benefits from knowing deployment context (e.g., where will MCP server run?)
- Alternative: Follow committed agenda exactly, discuss AI integration earlier

**Decision Required:**
- [ ] Keep this order (logical flow) - **requires client approval**
- [ ] Revert to committed agenda order (AI before Integration Layer)

**Total Duration:** Both orders = 6h 30min (unchanged)

---

## Aktivität 1: Recap Tag 1 & Scope-Verschärfung

**Dauer**: 30min  
**Ziel**: Gemeinsames Verständnis validieren, MVP-Scope final bestätigen

### Vorbereitung

**Materialien**:
- Tag 1 Outputs (aus Miro Board 2):
  - Frame 3: Domain Map
  - Frame 7: Initial Scope Decision (3-5 MVP-Masken)
- Beamer/Screen-Share für Miro

### Ablauf

#### Phase 1: Tag 1 Key Outputs Review (15min)

**Facilitator zeigt**:
1. **Domain Map** (Frame 3):
   - "Wir haben X Bounded Contexts identifiziert: [Namen vorlesen]"
   - "Wichtigste externe Integrationen: [SAP, COR Life, GDV, DMS]"

2. **MVP-Scope** (Frame 7):
   - "Wir haben uns auf diese 3-5 Masken für MVP geeinigt:"
   - Für jede Maske: Name, Begründung, erwartetes Risiko

**Frage an Teilnehmer**:
> "Gibt es nach einer Nacht Schlaf **Änderungswünsche** am Scope?"

**Parking Lot**: 
- Falls größere Diskussionen → "Notieren wir, kommen wir nach Machbarkeitsanalyse zurück"

#### Phase 2: Tag 2 Zielsetzung (5min)

**Erklärung**:
> "Heute entscheiden wir **WIE** wir technisch umsetzen:
> - **Welche Technologien** für Integration Layer und Deployment?
> - **Wie** integrieren wir AI?
> - **Was** ist die Zielarchitektur (Draft)?"

**Erwartungsmanagement**:
- "Wir treffen **Entscheidungen**, keine perfekten Lösungen"
- "ADRs dokumentieren **Rationale**, nicht nur Ergebnis"
- "Offene Fragen landen im **Parking Lot** für Post-Workshop"

#### Phase 3: Scope-Validierung gegen Service-Stored Procedures (10min)

**Übergang zur nächsten Aktivität**:
> "Bevor wir Entscheidungen treffen: **Welche Service-Stored Procedures** brauchen unsere MVP-Masken? WGV wird uns das jetzt zeigen."

**Vorbereitung für SP-Analyse**:
- Miro Frame / Template für SP-Katalog öffnen (siehe Aktivität 2)
- WGV bittet, Bildschirm zu teilen (falls sie live aus Oracle zeigen)

### Output

✅ **Bestätigter MVP-Scope** (3-5 Masken)  
✅ **Gemeinsames Verständnis** der Tag 1 Outputs  
✅ **Klare Tag 2 Ziele** kommuniziert  

---

## Aktivität 2: Service/Stored Procedures Präsentation & Analyse

**Dauer**: 1h 15min  
**Ziel**: Service-Stored-Procedure-Katalog für MVP-Masken erstellen (Signatur-Level, kein Code-Deep-Dive)

### Vorbereitung

**Materialien**:
- **Template: Service-Stored-Procedure-Katalog** (siehe unten)
- WGV hat Zugriff auf Oracle DB / Dokumentation vorbereitet
- Miro Capture-Bereich oder Google Sheets geteilt

**Vorab-Klärung mit WGV** (idealerweise vor Workshop):
- Haben sie eine **Liste der Service-Stored Procedures** pro Maske?
- Gibt es **Dokumentation** (Kommentare, README)?
- Können sie **live in die DB schauen** oder zeigen sie Screenshots?

### Ablauf

#### Phase 1: Einführung Service-Stored Procedures (10min)

**WGV präsentiert** (oder codecentric erklärt aus Architektur-Dokumentation):

**Kontext** (basierend auf `/context/icis_oracle_forms_architektur.md`):
> "ICIS nutzt **Service-Stored Procedures** als Geschäftslogik-Schicht:
> - **BSP** (Business Service Procedures): Kern-Geschäftslogik
> - **DSP** (Data Service Procedures): Datenzugriff, CRUD
> - **GSP** (Generic Service Procedures): Wiederverwendbare Utilities
> - **TSP** (Transaction Service Procedures): Transaktionssteuerung"

**Frage an WGV**:
> "Stimmt diese Kategorisierung noch? Gibt es weitere SP-Typen?"

**Wichtig für Migration**:
- Diese SPs sind **stabile Schnittstellen**
- Wir rufen sie aus Integration Layer (Spring Boot / ORDS) auf
- **Keine Änderungen am PL/SQL-Code** geplant

#### Phase 2: Strukturierte Analyse pro MVP-Maske (60min)

**Für jede der 3-5 MVP-Masken** (~12-15min pro Maske):

**Template-Fragen** (Facilitator führt durch):

##### 2a) Maske identifizieren

**Frage**:
> "Welche Maske analysieren wir jetzt? [Name aus Frame 7]"

**Notieren**:
- Masken-Name
- Bounded Context (aus Tag 1 Domain Map)
- Zweck (1-Satz-Beschreibung)

##### 2b) Service-Stored Procedures identifizieren

**Frage**:
> "Welche **Service-Stored Procedures** ruft diese Maske auf?"

**WGV zeigt** (idealerweise):
- Liste der SP-Namen
- In welchem Package? (z.B. `PKG_VERTRAG`, `PKG_SCHADEN`)

**Notieren** (Tabelle):
| SP-Name | Package | Typ (BSP/DSP/GSP/TSP) | Zweck (1 Satz) |
|---------|---------|----------------------|----------------|
| GET_VERTRAG | PKG_VERTRAG | DSP | Lädt Vertragsdaten nach ID |
| SAVE_VERTRAG | PKG_VERTRAG | BSP | Speichert/Updated Vertrag mit Validierung |

**Facilitator-Hinweis**:
- "Wir brauchen **keine Code-Details**, nur die **Signatur**"
- "Falls unklar: Parking Lot, später mit Doku nacharbeiten"

##### 2c) Signatur-Level-Analyse

**Für 2-3 wichtigste SPs pro Maske** (die anderen nur Namen erfassen):

**Frage**:
> "Was sind die **Parameter** (IN/OUT) dieser SP?"

**Beispiel-Struktur** (WGV zeigt oder erklärt):
```sql
PROCEDURE GET_VERTRAG (
  p_vertrag_id   IN  NUMBER,
  p_vertrag_data OUT SYS_REFCURSOR  -- oder Record Type
);

PROCEDURE SAVE_VERTRAG (
  p_vertrag_data IN  T_VERTRAG_REC,  -- Custom Type
  p_erfolg       OUT BOOLEAN,
  p_fehler_msg   OUT VARCHAR2
);
```

**Notieren**:
| Parameter | Typ | IN/OUT | Beschreibung |
|-----------|-----|--------|--------------|
| p_vertrag_id | NUMBER | IN | Primärschlüssel |
| p_vertrag_data | SYS_REFCURSOR | OUT | Vertragsdaten als Cursor |

**Facilitator fragt**:
- "Gibt es **Custom Types** (Records, Tables)?" → Wichtig für REST-API-Mapping
- "Wie werden **Fehler** zurückgegeben?" → OUT-Parameter? Exception? Return Code?
- "Gibt es **Transaktionssteuerung** (COMMIT/ROLLBACK in SP oder außerhalb)?"

##### 2d) Abhängigkeiten & Komplexität

**Frage**:
> "Ruft diese SP **andere SPs** auf? Hat sie **externe Abhängigkeiten** (andere Packages, externe Systeme)?"

**Notieren**:
- Abhängigkeiten: [Liste von anderen SPs, Packages]
- Externe Calls: [z.B. "Ruft GDV-Schnittstelle", "Schreibt in DMS"]

**Komplexitäts-Einschätzung** (WGV Einschätzung):
| SP-Name | Komplexität (1-5) | Begründung |
|---------|-------------------|------------|
| GET_VERTRAG | 2 | Einfacher SELECT |
| SAVE_VERTRAG | 4 | Komplexe Validierung, mehrere Tabellen |

**Skala**:
- 1 = Einfach (single table CRUD)
- 3 = Mittel (mehrere Tabellen, einfache Logik)
- 5 = Komplex (verschachtelte Aufrufe, externe Systeme, komplexe Regeln)

##### 2e) Integrations-Kandidat: ORDS vs. Spring Boot?

**Frage** (nach Erfassung aller SPs einer Maske):
> "Ist diese Maske ein **ORDS-Kandidat** (einfache CRUD-SPs) oder brauchen wir **Spring Boot** (Orchestrierung, komplexe Logik)?"

**Kriterien**:
- **ORDS-Kandidat**: 
  - Nur DSPs (Data Service Procedures)
  - Keine Orchestrierung zwischen SPs
  - Standard REST-Mapping (GET = SELECT, POST = INSERT, etc.)
  
- **Spring Boot-Kandidat**:
  - BSPs mit komplexer Logik
  - Mehrere SP-Aufrufe müssen orchestriert werden
  - Custom Error Handling nötig
  - AI-Integration geplant (MCP Server)

**Notieren** (pro Maske):
- Integration Layer Empfehlung: [ORDS / Spring Boot / Hybrid]
- Begründung: [1 Satz]

#### Phase 3: Zusammenfassung & Gaps (5min)

**Facilitator fasst zusammen**:
> "Wir haben **X Service-Stored Procedures** für MVP-Masken identifiziert:
> - Y sind einfach (ORDS-Kandidaten)
> - Z sind komplex (Spring Boot empfohlen)"

**Offene Fragen** (Parking Lot):
- "Welche SPs haben **keine Dokumentation**?" → Post-Workshop: Doku anfordern
- "Gibt es **Custom Types**, für die wir Mapping brauchen?" → Später mit Entwicklern klären
- "Welche SPs rufen **externe Systeme**?" → Risiko für MVP, möglicherweise Mocking nötig

### Output

📋 **Service-Stored-Procedure-Katalog** mit:
- ~10-30 SPs dokumentiert (abhängig von MVP-Masken-Komplexität)
- Signaturen (IN/OUT Parameter) für wichtigste SPs
- Komplexitäts-Einschätzung
- Integration Layer Empfehlung pro Maske (ORDS / Spring Boot)

📊 **Statistik**:
- X% einfache SPs → ORDS-Kandidaten
- Y% komplexe SPs → Spring Boot-Kandidaten

**Verwendung**: Basis für Aktivität 4 (Integration Layer-Entscheidung)

---

## Template: Service-Stored-Procedure-Katalog

```markdown
# Service-Stored-Procedure-Katalog - WGV ICIS MVP

**Datum**: 29.04.2026 (Tag 2 Workshop)

## Maske 1: [Name]

**Bounded Context**: [z.B. Vertragsverwaltung]  
**Zweck**: [1-Satz-Beschreibung]  
**Integration Layer Empfehlung**: [ORDS / Spring Boot / Hybrid]

### Service-Stored Procedures

| SP-Name | Package | Typ | Zweck | Komplexität (1-5) | Abhängigkeiten | Notizen |
|---------|---------|-----|-------|-------------------|----------------|---------|
| GET_VERTRAG | PKG_VERTRAG | DSP | Lädt Vertragsdaten | 2 | - | ORDS-Kandidat |
| SAVE_VERTRAG | PKG_VERTRAG | BSP | Speichert Vertrag | 4 | PKG_VALIDATION, PKG_TARIF | Spring Boot (Orchestrierung) |
| VALIDATE_VERTRAG | PKG_VALIDATION | GSP | Validiert Vertragsdaten | 3 | - | Wiederverwendbar |

### Detaillierte Signaturen (Top 3 SPs)

#### GET_VERTRAG

```sql
PROCEDURE GET_VERTRAG (
  p_vertrag_id   IN  NUMBER,
  p_vertrag_data OUT SYS_REFCURSOR
);
```

**Parameter**:
| Name | Typ | IN/OUT | Beschreibung |
|------|-----|--------|--------------|
| p_vertrag_id | NUMBER | IN | Vertrag Primärschlüssel |
| p_vertrag_data | SYS_REFCURSOR | OUT | Result Set mit Vertragsdaten |

**Fehlerbehandlung**: Exception bei ungültiger ID

**Custom Types**: Keine

---

#### SAVE_VERTRAG

```sql
PROCEDURE SAVE_VERTRAG (
  p_vertrag_rec IN  T_VERTRAG_REC,  -- Custom Record Type
  p_erfolg      OUT BOOLEAN,
  p_fehler_msg  OUT VARCHAR2
);
```

**Parameter**:
| Name | Typ | IN/OUT | Beschreibung |
|------|-----|--------|--------------|
| p_vertrag_rec | T_VERTRAG_REC | IN | Vertragsdaten (Custom Type) |
| p_erfolg | BOOLEAN | OUT | TRUE bei Erfolg |
| p_fehler_msg | VARCHAR2 | OUT | Fehlermeldung (falls Fehler) |

**Custom Type Definition** (T_VERTRAG_REC):
```sql
TYPE T_VERTRAG_REC IS RECORD (
  vertrag_id    NUMBER,
  kunde_id      NUMBER,
  police_nr     VARCHAR2(50),
  beginn_datum  DATE,
  -- ... weitere Felder
);
```

**Abhängigkeiten**:
- Ruft PKG_VALIDATION.VALIDATE_VERTRAG auf
- Ruft PKG_TARIF.CALCULATE_BEITRAG auf

**Transaktionssteuerung**: SP führt COMMIT aus (!)

**Fehlerbehandlung**: OUT-Parameter p_erfolg + p_fehler_msg

---

## Maske 2: [Name]

[... analog ...]

---

## Zusammenfassung

| Kategorie | Anzahl SPs |
|-----------|------------|
| **Gesamt** | 15 |
| Einfach (Komplexität 1-2) | 6 (40%) |
| Mittel (Komplexität 3) | 5 (33%) |
| Komplex (Komplexität 4-5) | 4 (27%) |

**Integration Layer Empfehlung**:
- **ORDS**: Masken mit nur einfachen DSPs → 2 Masken
- **Spring Boot**: Masken mit BSPs und Orchestrierung → 3 Masken

**Offene Fragen** (Parking Lot):
- [ ] Dokumentation für SP XYZ fehlt → Post-Workshop anfordern
- [ ] Custom Type Mapping für T_VERTRAG_REC klären → Mit Entwickler-Team
- [ ] Mocking-Strategie für externe System-Calls → Technische Spike
```

---

## Aktivität 3: Technische Machbarkeitsanalyse MVP-Masken

**Dauer**: 1h  
**Ziel**: MVP-Scope validieren anhand technischer Machbarkeit, Risiken identifizieren

### Vorbereitung

**Materialien**:
- Tag 1 Output: MVP-Scope (Frame 7 - 3-5 Masken)
- Aktivität 2 Output: Service-SP-Katalog
- Machbarkeits-Matrix Template (siehe unten)

**Teilnehmer-Rollen**:
- **WGV Architekten/Entwickler**: Technische Einschätzung
- **codecentric**: Moderieren, kritische Fragen stellen

### Ablauf

#### Phase 1: Machbarkeits-Kriterien erklären (10min)

**Facilitator erklärt**:
> "Wir prüfen jede MVP-Maske gegen **6 Kriterien**:
> 1. **Service-SP-Verfügbarkeit**: Sind alle nötigen SPs vorhanden und dokumentiert?
> 2. **Komplexität**: Ist die technische Komplexität für MVP geeignet?
> 3. **Abhängigkeiten**: Wie viele Abhängigkeiten zu anderen Masken/Systemen?
> 4. **Daten-Verfügbarkeit**: Gibt es Testdaten? Produktionsdaten nutzbar?
> 5. **Externe Integrationen**: Ruft die Maske externe Systeme auf (GDV, SAP, DMS)?
> 6. **Forms-PL/SQL-Migration**: Wie viel Forms-PL/SQL-Logik muss in Frontend/Backend migriert werden?"

**Skala**:
- 🟢 **Grün**: Geringes Risiko, machbar
- 🟡 **Gelb**: Mittleres Risiko, Mitigation möglich
- 🔴 **Rot**: Hohes Risiko, nicht für MVP geeignet

#### Phase 2: Analyse pro MVP-Maske (40min, ~8min pro Maske)

**Für jede Maske** (aus Frame 7):

##### Schritt 1: Kontext (1min)

**Facilitator**:
> "Maske: [Name]. Bounded Context: [X]. Zweck: [Y]."

##### Schritt 2: Kriterium-für-Kriterium-Bewertung (6min)

**1. Service-SP-Verfügbarkeit**

**Frage**:
> "Haben wir alle nötigen Service-SPs identifiziert (aus Aktivität 2)? Gibt es fehlende SPs oder undokumentierte?"

**Bewertung**:
- 🟢 Grün: Alle SPs vorhanden, dokumentiert
- 🟡 Gelb: 1-2 SPs fehlen oder undokumentiert → nacharbeiten
- 🔴 Rot: Viele SPs fehlen, unklar welche gebraucht werden

**2. Komplexität**

**Frage**:
> "Basierend auf SP-Katalog: Ist die Gesamtkomplexität für MVP geeignet?"

**Bewertung**:
- 🟢 Grün: Überwiegend einfache/mittlere SPs (Komplexität 1-3)
- 🟡 Gelb: Mix aus einfach und komplex, machbar mit Aufwand
- 🔴 Rot: Sehr komplexe SPs (Komplexität 4-5), hohes Risiko

**3. Abhängigkeiten**

**Frage**:
> "Wie viele Abhängigkeiten hat diese Maske zu anderen Masken, Packages, Kontexten?"

**Bewertung**:
- 🟢 Grün: Isoliert, wenige Abhängigkeiten (1-2)
- 🟡 Gelb: Moderate Abhängigkeiten (3-5), managebar
- 🔴 Rot: Viele Abhängigkeiten (6+), Kaskaden-Effekt

**4. Daten-Verfügbarkeit**

**Frage**:
> "Haben wir **Testdaten** für diese Maske? Können wir mit **Produktionsdaten** (anonymisiert) arbeiten?"

**Bewertung**:
- 🟢 Grün: Testdaten vorhanden, gut dokumentiert
- 🟡 Gelb: Testdaten müssen erstellt werden, aber machbar
- 🔴 Rot: Keine Testdaten, Produktionsdaten nicht nutzbar (Datenschutz)

**5. Externe Integrationen**

**Frage**:
> "Ruft die Maske **externe Systeme** auf (SAP, COR Life, GDV, DMS)? Wenn ja, welche?"

**Bewertung**:
- 🟢 Grün: Keine externen Calls oder nur lesend
- 🟡 Gelb: Externe Calls, aber Mock-bar für MVP
- 🔴 Rot: Kritische externe Calls, schwer zu mocken (z.B. Zahlungstransaktionen)

**6. Forms-PL/SQL-Migration**

**Frage**:
> "Wie viel **Forms-PL/SQL** (Triggers, Program Units) muss in Frontend oder Backend migriert werden?"

**Kontext** (aus `/context/icis_oracle_forms_architektur.md`):
- Forms-PL/SQL läuft im **Middle-Tier** (Forms Runtime)
- Muss nach Frontend (Validierung, UI-Logik) oder Backend (Orchestrierung) migriert werden

**Bewertung**:
- 🟢 Grün: Wenig Forms-PL/SQL (<100 LOC), überwiegend UI-Logik
- 🟡 Gelb: Moderater Anteil (100-500 LOC), mischte Logik
- 🔴 Rot: Viel Forms-PL/SQL (>500 LOC), komplexe Business Logic

**Notizen**: Welche Trigger-Typen? (WHEN-BUTTON-PRESSED, POST-QUERY, etc.)

##### Schritt 3: Gesamtbewertung & Risiko-Score (1min)

**Facilitator berechnet Risiko-Score**:
- 🟢 Grün = 1 Punkt
- 🟡 Gelb = 2 Punkte
- 🔴 Rot = 3 Punkte

**Gesamtscore**: Summe aller 6 Kriterien (Min: 6, Max: 18)

**Kategorisierung**:
- **6-9 Punkte**: ✅ **MVP-geeignet** (Quick Win)
- **10-13 Punkte**: ⚠️ **MVP-möglich mit Risiken** (Mitigation nötig)
- **14-18 Punkte**: ❌ **Nicht für MVP** (zu risikoreich, Phase 2)

**Diskussion**:
> "Gesamtscore: X Punkte. **Bleibt diese Maske im MVP** oder verschieben wir sie in Phase 2?"

#### Phase 3: Scope-Anpassung & Priorisierung (10min)

**Facilitator zeigt Übersicht** (alle 3-5 Masken):

| Maske | SP-Verfügb. | Komplexität | Abhängigk. | Daten | Externe | Forms-PL/SQL | Score | MVP? |
|-------|-------------|-------------|------------|-------|---------|--------------|-------|------|
| Maske A | 🟢 | 🟢 | 🟢 | 🟢 | 🟢 | 🟡 | 7 | ✅ Ja |
| Maske B | 🟡 | 🟡 | 🟢 | 🟢 | 🟡 | 🟡 | 11 | ⚠️ Mit Mitigation |
| Maske C | 🔴 | 🔴 | 🔴 | 🟡 | 🔴 | 🔴 | 17 | ❌ Nein → Phase 2 |

**Fragen an Gruppe**:
1. "Wollen wir Maske C **ersetzen** durch eine einfachere?" (Referenz: Tag 1 Frame 7 - Backlog)
2. "Für Maske B mit Score 11: Welche **Mitigationen** sind nötig?"
   - Beispiele: Mock für externes System, SP-Dokumentation nacharbeiten, Forms-PL/SQL-Analyse vertiefen

**Entscheidung dokumentieren**:
- **Finaler MVP-Scope**: 3-5 Masken mit Scores 6-13
- **Ausgeschlossene Masken**: In Phase 2 verschoben (mit Begründung)
- **Mitigationen**: Aktionen pro Maske (Owner, Deadline)

### Output

✅ **Validierter MVP-Scope** mit technischer Machbarkeit bestätigt  
✅ **Risiko-Matrix** pro Maske (6 Kriterien bewertet)  
✅ **Mitigation-Plan** für Gelb-bewertete Masken  
✅ **Parking Lot**: Technische Fragen für Post-Workshop  

---

## Template: Machbarkeits-Matrix

```markdown
# Technische Machbarkeitsanalyse - MVP-Masken

**Datum**: 29.04.2026 (Tag 2)

## Bewertungs-Skala

- 🟢 **Grün** (1 Punkt): Geringes Risiko
- 🟡 **Gelb** (2 Punkte): Mittleres Risiko, Mitigation möglich
- 🔴 **Rot** (3 Punkte): Hohes Risiko

**Score-Kategorien**:
- 6-9: ✅ MVP-geeignet
- 10-13: ⚠️ MVP mit Risiken
- 14-18: ❌ Nicht für MVP

---

## Maske 1: [Name]

| Kriterium | Bewertung | Begründung | Mitigation (falls Gelb/Rot) |
|-----------|-----------|------------|------------------------------|
| **1. Service-SP-Verfügbarkeit** | 🟢 | Alle SPs vorhanden | - |
| **2. Komplexität** | 🟡 | Mix einfach/komplex | SP-Dokumentation verbessern |
| **3. Abhängigkeiten** | 🟢 | Nur 2 Abhängigkeiten | - |
| **4. Daten-Verfügbarkeit** | 🟢 | Testdaten vorhanden | - |
| **5. Externe Integrationen** | 🟡 | Ruft DMS auf | Mock DMS für MVP |
| **6. Forms-PL/SQL-Migration** | 🟡 | ~200 LOC, WHEN-BUTTON Triggers | AI-Analyse + manuelle Review |

**Gesamtscore**: 10 Punkte (⚠️ MVP mit Risiken)

**Entscheidung**: ✅ **Bleibt im MVP** mit folgenden Mitigationen:
- [ ] SP-Dokumentation für SAVE_XYZ vervollständigen (Owner: WGV, Deadline: KW20)
- [ ] DMS-Mock implementieren (Owner: codecentric, Deadline: Phase 0)
- [ ] Forms-PL/SQL analysieren mit Claude Code (Owner: codecentric, Tag 3)

**Risiken**:
- DMS-Integration könnte komplexer sein als erwartet → Plan B: Manuelle Dokumenten-Upload

---

## Maske 2: [Name]

[... analog ...]

---

## Zusammenfassung

| Maske | Score | Status | Nächste Schritte |
|-------|-------|--------|------------------|
| Maske A | 7 | ✅ MVP | Keine Blocker |
| Maske B | 10 | ⚠️ MVP mit Mitigation | DMS-Mock, SP-Doku |
| Maske C | 11 | ⚠️ MVP mit Mitigation | Testdaten erstellen |
| ~~Maske D~~ | 17 | ❌ Phase 2 | Zu komplex, viele Abhängigkeiten |

**Finaler MVP-Scope**: 3 Masken (A, B, C)

**Ersetzte Masken**: Maske D ersetzt durch **Maske E** (aus Tag 1 Backlog, Score 8)

**Offene technische Fragen** (Parking Lot):
- [ ] Wie mocken wir GDV-Schnittstelle für Maske B? → Technische Spike
- [ ] Custom Type Mapping T_VERTRAG_REC → Java POJO? → Mit Entwickler-Team klären
```

---

## Aktivität 4: Integration Layer - Vergleich & Entscheidung

**Dauer**: 1h (45min Vergleich + 15min Entscheidung)  
**Ziel**: Technologie-Entscheidung für Integration Layer: Spring Boot / Oracle ORDS / Hybrid

**Miro Frames**: Frame 8 (INPUT - Comparison) + Frame 9 (CAPTURE - Decision)

### Vorbereitung

**Materialien**:
- **Frame 8**: Integration Layer Comparison Table (pre-populated)
- **Frame 9**: Decision Template (empty)
- Reference: `/context/oracle_forms_migration_options_reference.md` (Flynn Jones article)
- SP-Katalog (Aktivität 2 Output)

**Pre-populated Comparison** (Frame 8 - bereits in Miro vorbereitet):
- Siehe `miro_board_structure.md` Frame 8 (lines 361-407)

### Ablauf

#### Phase 1: Comparison Table Walkthrough (15min)

**Facilitator präsentiert Frame 8**:

> "Wir haben **3 Optionen** für Integration Layer:
> 1. **Spring Boot**: Java-basiert, volle Kontrolle, AI-Integration
> 2. **Oracle ORDS**: Auto-generiert REST aus SPs, schnell, aber Oracle-locked
> 3. **Hybrid**: ORDS für einfache CRUD, Spring Boot für Komplexität"

**Durch Tabelle gehen** (Zeile für Zeile):

**Kriterium: Flexibilität**
- Spring Boot: ★★★★★ - "Java-Ecosystem, alle Frameworks nutzbar"
- ORDS: ★★☆☆☆ - "Oracle-spezifisch, REST-only"
- Hybrid: ★★★★☆ - "ORDS für einfache, Spring für komplexe"

**Kriterium: PL/SQL Integration**
- Spring Boot: ★★★☆☆ - "JDBC, manuelles Type-Mapping"
- ORDS: ★★★★★ - "Auto-generiert aus SP-Signaturen"
- Hybrid: ★★★★☆ - "Best of both"

... (durch alle Kriterien)

**Fragen an Teilnehmer**:
> "Welche Kriterien sind für WGV am **wichtigsten**?"
> - Vendor Lock-In-Vermeidung?
> - Schnelle Entwicklung?
> - AI-Integration?
> - Team Skills vorhanden?

#### Phase 2: WGV-Spezifische Faktoren (20min)

**Basierend auf Aktivität 2 (SP-Katalog)**:

**Frage**:
> "Von unseren MVP-Masken: **Wie viele sind ORDS-Kandidaten** (einfache DSPs) vs. **Spring Boot-Kandidaten** (Orchestrierung)?"

**Facilitator zeigt Statistik** (aus SP-Katalog):
- X% einfache SPs → ORDS spart Entwicklungszeit
- Y% komplexe SPs → Spring Boot nötig

**Diskussion**:

**Pro ORDS**:
- "Für einfache CRUD-Masken ist ORDS **schneller**"
- "Weniger Code zu schreiben = weniger Bugs"
- "WGV bleibt in Oracle-Ecosystem (DB + ORDS + APEX möglich)"

**Contra ORDS**:
- "Vendor Lock-In: Schwer zu migrieren wenn WGV später Oracle verlassen will"
- "AI-Integration (MCP) schwierig in ORDS"
- "Custom Business Logic schwer zu implementieren"

**Pro Spring Boot**:
- "Volle Kontrolle über API-Design"
- "AI-Integration (Spring AI, MCP Server) einfach"
- "Cloud-agnostic (Azure, AWS, GCP)"
- "Große Java-Community, viele Entwickler verfügbar"

**Contra Spring Boot**:
- "Mehr Entwicklungsaufwand (mehr Code)"
- "Custom Type-Mapping für PL/SQL Records/Tables nötig"

**Pro Hybrid**:
- "Pragmatisch: ORDS wo es passt, Spring Boot wo nötig"
- "Schrittweise Migration: Start mit ORDS, später zu Spring Boot erweitern"

**Contra Hybrid**:
- "Zwei Technologien = zwei Teams Skills nötig"
- "Komplexität in Architektur (zwei API-Gateways?)"

#### Phase 3: Recommendation from codecentric (10min)

**codecentric gibt Empfehlung** (basierend auf Context):

**Empfehlung: Hybrid-Ansatz mit Spring Boot-Fokus**

**Rationale**:
1. **MVP Start**: Spring Boot für alle MVP-Masken (einheitliche Architektur)
2. **Später**: ORDS für einfache CRUD-Masken in Phase 2+ (Effizienz)
3. **AI-Integration**: Spring Boot bietet Spring AI für MCP-Server
4. **Vendor Lock-In**: Vermeidbar durch Spring Boot als Hauptschicht

**Architektur-Vorschlag**:
```
Frontend (React/Angular)
    │
    ▼
[Spring Boot Integration Layer]  ← Haupt-Gateway
    │
    ├─→ Spring Boot Services (Komplex, AI, Orchestrierung)
    │       │
    │       ▼
    │   [PL/SQL SPs direkt via JDBC]
    │
    └─→ [Oracle ORDS] (Optional für einfache CRUD in Phase 2+)
            │
            ▼
        [PL/SQL SPs via Auto-REST]
```

**Vorteil**:
- Einheitliches Frontend (ruft immer Spring Boot)
- Spring Boot kann intern entscheiden: Direkt PL/SQL (JDBC) oder ORDS delegieren
- Flexibel für spätere Erweiterung

#### Phase 4: Decision Documentation (15min)

**Facilitator öffnet Frame 9** (Decision Template):

**Felder ausfüllen** (gemeinsam mit Gruppe):

**1. Gewählte Technologie**:
- ☐ Spring Boot
- ☐ Oracle ORDS
- ☑ Hybrid (Spring Boot + ORDS)

**2. Begründung** (Textfeld):
> "Wir starten mit **Spring Boot** für MVP-Masken, da:
> - AI-Integration (MCP) benötigt wird
> - Vendor Lock-In vermieden werden soll
> - Komplexe Orchestrierung nötig ist (basierend auf SP-Katalog)
> 
> **ORDS** wird evaluiert für Phase 2+ einfache CRUD-Masken zur Effizienzsteigerung."

**3. Trade-Offs akzeptiert** (Textfeld):
> "Wir verzichten auf:
> - Schnellere Entwicklung durch ORDS Auto-Generation (kurzfristig mehr Aufwand)
> - Einfachheit einer Single-Technology-Lösung (nehmen Hybrid-Komplexität in Kauf)
> 
> Wir gewinnen dafür:
> - Flexibilität, Cloud-Portabilität, AI-Integration"

**4. Risiken & Mitigationen**:
| Risiko | Mitigation |
|--------|------------|
| Team hat wenig Spring Boot-Erfahrung | Training in Phase 0, Pairing mit codecentric |
| PL/SQL Custom Type-Mapping komplex | Spike in Phase 0 für häufigste Types, Code-Generator evaluieren |
| ORDS später hinzufügen = Architektur-Änderung | Spring Boot API-Gateway-Pattern vorsehen (Routing zu ORDS möglich) |

**5. Nächste Schritte**:
- [ ] Spring Boot Boilerplate erstellen (Phase 0, Owner: codecentric)
- [ ] PL/SQL Type-Mapping Spike (Phase 0, 2 Tage, Owner: WGV + codecentric)
- [ ] ORDS Evaluierung für Phase 2 (Phase 1 Ende, Owner: WGV)

**ADR-Hinweis**:
> "Diese Entscheidung wird nach Workshop als **ADR (Architecture Decision Record)** formalisiert und ins Repository committed."

### Output

✅ **Technologie-Entscheidung**: Spring Boot (Hybrid mit ORDS-Option später)  
✅ **Dokumentierte Begründung** (Frame 9)  
✅ **ADR-Vorlage** für Post-Workshop  
✅ **Nächste Schritte** mit Owners  

---

## Aktivität 5: Deployment-Optionen - Vergleich & Entscheidung

**Dauer**: 45min (30min Vergleich + 15min Entscheidung)  
**Ziel**: Deployment-Strategie festlegen: VMs / Docker / Kubernetes / Azure Container Apps

**Miro Frames**: Frame 10 (INPUT - Comparison) + Frame 11 (CAPTURE - Decision)

### Vorbereitung

**Materialien**:
- **Frame 10**: Deployment Comparison Table (pre-populated)
- **Frame 11**: Decision Template (empty)

**Pre-populated Comparison** (Frame 10 - bereits in Miro vorbereitet):
- Siehe `miro_board_structure.md` Frame 10 (lines 452-486)

### Ablauf

#### Phase 1: Comparison Table Walkthrough (15min)

**Facilitator präsentiert Frame 10**:

> "Wir vergleichen **4 Deployment-Optionen**:
> 1. **VMs (klassisch)**: Wie heute, virtualisierte Server
> 2. **Docker (Docker Compose)**: Containerisierung ohne Orchestrierung
> 3. **Kubernetes (AKS)**: Full Orchestration, Auto-Scaling
> 4. **Azure Container Apps**: Managed Container Service (zwischen Docker und K8s)"

**Durch Tabelle gehen** (verkürzt, da ähnlich zu Aktivität 4):

**Key Differences highlighten**:
- **Komplexität**: VMs < Docker < Azure Container Apps < Kubernetes
- **Cloud-Portabilität**: VMs/Docker/K8s (überall) vs. Azure Container Apps (nur Azure)
- **Ops-Aufwand**: Azure Container Apps < VMs < Docker < Kubernetes

#### Phase 2: WGV-Spezifische Faktoren (10min)

**Fragen an WGV**:

**1. Bestehende Infrastruktur**:
> "Wo läuft ICIS heute? VMs? On-Premise oder Cloud?"

**2. Team Skills**:
> "Hat Ihr Ops-Team **Kubernetes-Erfahrung**? Docker-Erfahrung?"

**3. Cloud-Strategie**:
> "Ist **Azure** strategisch festgelegt oder sind Sie cloud-agnostic?"

**4. Skalierungs-Anforderungen**:
> "Brauchen Sie **Auto-Scaling** für 900 Masken? Oder ist Last relativ konstant?"

**Typische Antworten & Implikationen**:

| Antwort | Implikation |
|---------|-------------|
| "Wir laufen heute auf VMs, Team kennt das" | → VMs oder Docker (geringer Sprung) |
| "Wir haben Azure-Commitment" | → Azure Container Apps (managed) |
| "Wir wollen cloud-agnostic bleiben" | → Docker oder Kubernetes |
| "Wir haben kein Ops-Team" | → Azure Container Apps (managed) |

#### Phase 3: Recommendation from codecentric (5min)

**codecentric Empfehlung** (kontextabhängig):

**Szenario A: WGV hat Azure-Commitment + wenig DevOps-Team**
→ **Empfehlung: Azure Container Apps**

**Rationale**:
- Managed Service (wenig Ops-Aufwand)
- Containerisierung (modern, portabel innerhalb Azure)
- Auto-Scaling (für wachsende Last)
- Einfacher als Kubernetes, moderner als VMs

**Szenario B: WGV will cloud-agnostic + hat DevOps-Skills**
→ **Empfehlung: Docker + Kubernetes (später)**

**Rationale**:
- Start mit Docker Compose (einfach für MVP)
- Später Migration zu Kubernetes (wenn Skalierung nötig)
- Cloud-agnostic (Azure, AWS, GCP, on-prem)

**Szenario C: WGV will minimale Änderung**
→ **Empfehlung: Docker auf VMs**

**Rationale**:
- VMs wie heute (vertrautes Deployment)
- Docker-Container für Modernität (CI/CD, Isolation)
- Geringer Lernaufwand

#### Phase 4: Decision Documentation (15min)

**Facilitator öffnet Frame 11** (analog zu Frame 9):

**Felder ausfüllen**:

**1. Gewählte Technologie**:
[Checkbox-Auswahl basierend auf Diskussion]

**Beispiel** (Szenario A):
- ☐ VMs (klassisch)
- ☐ Docker (Docker Compose)
- ☐ Kubernetes (AKS)
- ☑ **Azure Container Apps**

**2. Begründung**:
> "Azure Container Apps bietet:
> - Managed Service (geringer Ops-Aufwand für WGV-Team)
> - Containerisierung (moderne Architektur, CI/CD-ready)
> - Auto-Scaling (für wachsende Nutzung)
> - Azure-Integration (passt zu bestehender WGV-Strategie)"

**3. Trade-Offs**:
> "Wir verzichten auf:
> - Cloud-Portabilität (locked zu Azure)
> - Volle Kontrolle (wie bei Kubernetes)
> 
> Wir gewinnen:
> - Einfachheit, weniger Ops-Aufwand, schneller Start"

**4. Risiken & Mitigationen**:
| Risiko | Mitigation |
|--------|------------|
| Vendor Lock-In (Azure) | Container-Images bleiben portabel (Docker), notfalls Migration zu AKS |
| Azure Container Apps ist relativ neu | Evaluierung in Phase 0, Fallback: AKS |
| Team hat keine Container-Erfahrung | Training, codecentric Support |

**5. Nächste Schritte**:
- [ ] Azure Container Apps Proof-of-Concept (Phase 0, 3 Tage, Owner: codecentric)
- [ ] Deployment-Pipeline Design (CI/CD via Azure DevOps, Phase 0)
- [ ] Networking-Konzept (Load Balancer, VNet, Oracle DB-Zugriff)

### Output

✅ **Deployment-Entscheidung**: [Azure Container Apps / Kubernetes / Docker]  
✅ **Dokumentierte Begründung** (Frame 11)  
✅ **ADR-Vorlage** für Post-Workshop  
✅ **Nächste Schritte** mit Owners  

---

## Aktivität 6: AI-Integration Patterns - Diskussion & Entscheidung

**Dauer**: 1h  
**Ziel**: Entscheiden wie AI ins System integriert wird: MCP Server / Spring AI / Direct / Hybrid

**Miro Frame**: Frame 13 (INPUT + CAPTURE hybrid)

### Vorbereitung

**Materialien**:
- **Frame 13**: AI Integration Patterns (4 patterns pre-drawn)
- Tag 1 Output: AI Features Brainstorm (Frame 6)

**Pre-populated Patterns** (Frame 13 - in Miro vorbereitet):
- Siehe `miro_board_structure.md` Frame 13 (lines 558-607)

### Ablauf

#### Phase 1: AI Integration Patterns Erklärung (20min)

**Facilitator erklärt 4 Patterns**:

**Pattern 1: MCP Server (Model Context Protocol)**

**Diagramm** (in Miro):
```
Frontend → Spring Boot → [MCP Server] → LLM (Claude/GPT)
                              │
                              └→ Tools (DB Access, File Access, etc.)
```

**Vorteile**:
- ✓ Standard Protocol (Anthropic-backed)
- ✓ Tool Access (AI kann Datenbank abfragen, Funktionen aufrufen)
- ✓ RBAC (Rollenbasierte Zugriffskontrolle auf Tools)

**Nachteile**:
- ✗ Zusätzliche Komponente (mehr Komplexität)
- ✗ Noch relativ neu (weniger Community-Support)

**Use Case**: AI-Agents mit Tool-Zugriff (z.B. "Suche Verträge für Kunde X")

---

**Pattern 2: Spring AI Integration**

**Diagramm**:
```
Frontend → [Spring Boot + Spring AI] → LLM API (OpenAI/Anthropic)
               │
               └→ Oracle DB (via JDBC)
```

**Vorteile**:
- ✓ Unified mit Backend (alles in Spring Boot)
- ✓ Java Ecosystem (nutzt bestehende Spring-Skills)
- ✓ Einfaches API-Wrapping

**Nachteile**:
- ✗ Tighter Coupling (AI-Logik in Backend)
- ✗ Weniger Tool-Flexibilität als MCP

**Use Case**: Einfache AI-Features (Textgenerierung, Zusammenfassungen)

---

**Pattern 3: Direct LLM Calls (Frontend)**

**Diagramm**:
```
Frontend → [LLM API direkt] (OpenAI/Anthropic)
```

**Vorteile**:
- ✓ Einfach, schnell zu prototypen
- ✓ Kein Backend nötig (für reine Chat-Features)

**Nachteile**:
- ✗ Kein RBAC (jeder User = gleiche Rechte)
- ✗ Security-Risiko (API-Keys im Frontend exponiert)
- ✗ Kein Tool-Access (kann nicht auf DB zugreifen)

**Use Case**: Nur für MVP-Prototypen, nicht Production

---

**Pattern 4: Hybrid**

**Diagramm**:
```
Frontend
  │
  ├─→ Spring Boot + Spring AI → LLM (einfache Features)
  │
  └─→ Spring Boot → MCP Server → LLM + Tools (komplexe Agents)
```

**Vorteile**:
- ✓ Flexibilität (richtiges Tool für richtigen Job)
- ✓ Schrittweise Einführung (Start mit Spring AI, später MCP)

**Nachteile**:
- ✗ Höhere Architektur-Komplexität

**Use Case**: Wenn sowohl einfache Chat-Features als auch komplexe Agents gebraucht werden

#### Phase 2: WGV AI-Features Review (15min)

**Facilitator öffnet Frame 6** (AI Features Brainstorm von Tag 1):

**Frage**:
> "Welche AI-Features haben wir gestern identifiziert? Welche brauchen **Tool-Access** (DB, Masken) vs. nur **LLM-Chat**?"

**Kategorisierung** (Beispiele):

| AI-Feature (aus Frame 6) | Tool-Access? | Empfohlenes Pattern |
|--------------------------|--------------|---------------------|
| Vertragszusammenfassung | Nein (nur Text) | Spring AI |
| "Finde alle Verträge für Kunde X" | Ja (DB-Zugriff) | MCP Server |
| Schadensfallbeschreibung generieren | Nein (nur Text) | Spring AI |
| "Welche Masken muss ich für Adressänderung öffnen?" | Ja (Workflow-Wissen) | MCP Server |
| Chatbot für FAQ | Nein (nur Textkorpus) | Spring AI oder Direct |

**Ergebnis**:
- X% Features brauchen **kein Tool-Access** → Spring AI ausreichend
- Y% Features brauchen **Tool-Access** → MCP Server nötig

#### Phase 3: RBAC-Anforderungen (10min)

**Frage**:
> "Sollen **alle Nutzer** die gleichen AI-Features nutzen oder gibt es **Rollen**?"

**Beispiel-Diskussion**:
- **Sachbearbeiter**: Darf AI Vertragsdaten abfragen
- **Externe Partner**: Darf AI nur für FAQ nutzen (kein DB-Zugriff)
- **Admin**: Darf AI-Agents für Reporting nutzen

**Wenn RBAC nötig** → **MCP Server** ist Pflicht (Spring AI hat kein RBAC)

#### Phase 4: Hosting-Entscheidung (10min)

**Frage**:
> "Wo hosten wir LLMs?"

**Optionen**:
- ☐ **Cloud (Azure OpenAI, Anthropic Claude)**: Einfach, managed, Kosten pro Token
- ☐ **On-Premise (selbst gehostet)**: Datenschutz, keine externe Calls, hoher Aufwand
- ☐ **Hybrid**: Sensitive Daten on-prem, andere Cloud

**WGV-Faktoren**:
- Datenschutz-Anforderungen (Versicherungsdaten sensibel?)
- Compliance (BaFin, DSGVO)
- Kosten-Budget

**Typische Empfehlung**:
- **Start mit Cloud** (Azure OpenAI für MVP) → schnell, einfach
- **Später evaluieren**: On-Premise wenn Compliance/Kosten problematisch

#### Phase 5: Entscheidung dokumentieren (5min)

**Facilitator füllt Frame 13 CAPTURE-Bereich**:

**Gewähltes Pattern**:
[Beispiel]
> **Pattern 4: Hybrid**
> - Spring AI für einfache Text-Features (Zusammenfassungen, FAQ)
> - MCP Server für Tool-basierte Agents (DB-Zugriff, Workflow-Unterstützung)

**RBAC-Anforderungen**:
> - Sachbearbeiter: Voller DB-Zugriff via MCP Tools
> - Partner: Nur FAQ-Chatbot (Spring AI, kein Tool-Access)
> - Admin: Reporting-Agents (MCP mit erweiterten Tools)

**Hosting**:
> ☑ Cloud (Azure OpenAI für MVP)
> ☐ On-Premise
> ☐ Hybrid
> 
> **Rationale**: Schneller Start, Compliance mit WGV IT klären in Phase 0

**Nächste Schritte**:
- [ ] MCP Server Proof-of-Concept (Phase 0, Owner: codecentric)
- [ ] RBAC-Konzept ausarbeiten (Phase 0, Owner: WGV + codecentric)
- [ ] Azure OpenAI Account setup (Phase 0, Owner: WGV IT)

### Output

✅ **AI-Integration Pattern**: [MCP / Spring AI / Hybrid]  
✅ **RBAC-Anforderungen** dokumentiert  
✅ **Hosting-Entscheidung**: Cloud / On-Prem / Hybrid  
✅ **Nächste Schritte** mit Owners  

---

## Aktivität 7: Architektur-Diagramm (kollaborativ)

**Dauer**: 1h  
**Ziel**: Draft der Zielarchitektur erstellen (Foundation + kollaboratives Zeichnen)

**Miro Frame**: Frame 12 (CAPTURE - large whiteboard area)

### Vorbereitung

**Materialien**:
- **Frame 12**: Whiteboard mit Foundation/Skeleton (siehe unten)
- Miro Shapes Library (Rechtecke, Pfeile, Icons)
- Alle Entscheidungen von Aktivität 4-6:
  - Integration Layer: [Spring Boot / ORDS / Hybrid]
  - Deployment: [Docker / K8s / Azure Container Apps]
  - AI Integration: [MCP / Spring AI / Hybrid]

**Foundation/Skeleton** (pre-drawn in Miro Frame 12):
- Siehe separate Datei `tag2_architecture_diagram_foundation.md`

### Ablauf

#### Phase 1: Foundation Walkthrough (10min)

**Facilitator zeigt vorbereitetes Skeleton**:

> "Wir haben ein **Architektur-Skeleton** vorbereitet mit 4 Layern:
> 1. **Frontend Layer**: Browser, React/Angular (Details morgen)
> 2. **Integration Layer**: Spring Boot / ORDS (heute entschieden)
> 3. **Database Layer**: Oracle DB + PL/SQL (bleibt unverändert)
> 4. **External Systems**: SAP, COR Life, GDV, DMS, etc."

**Zeigen des Skeletons** (in Miro):
```
┌─────────────────────────────────────────────────────────┐
│  FRONTEND LAYER                                         │
│  [Browser - React/Angular - TBD Tag 3]                  │
└─────────────────────┬───────────────────────────────────┘
                      │ HTTPS / REST
┌─────────────────────▼───────────────────────────────────┐
│  INTEGRATION LAYER                                      │
│  [Spring Boot / ORDS / Hybrid - heute entschieden]     │
│  [AI Gateway - MCP / Spring AI - heute entschieden]    │
└─────────────────────┬───────────────────────────────────┘
                      │ JDBC / REST
┌─────────────────────▼───────────────────────────────────┐
│  DATABASE LAYER                                         │
│  [Oracle Database + PL/SQL Service-Stored Procedures]  │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│  EXTERNAL SYSTEMS                                       │
│  [SAP] [COR Life] [GDV] [DMS] [SIP Server] ...         │
└─────────────────────────────────────────────────────────┘
```

#### Phase 2: Kollaboratives Zeichnen (40min)

**Facilitator koordiniert** (Schritt für Schritt):

##### Schritt 1: Integration Layer detaillieren (15min)

**Basierend auf Aktivität 4 Entscheidung**:

**Wenn Spring Boot gewählt**:
> "Zeichnen wir die **Spring Boot-Komponenten**:
> - API Gateway (Routing, Authentication)
> - REST Controllers (pro Bounded Context?)
> - Service Layer (Orchestrierung)
> - JDBC Layer (PL/SQL Calls)"

**WGV + codecentric zeichnen gemeinsam**:
```
┌─────────────────────────────────────────────────────────┐
│  INTEGRATION LAYER (Spring Boot)                        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  ┌──────────────────┐                                   │
│  │  API Gateway     │  (Routing, Auth, Rate Limiting)  │
│  └────────┬─────────┘                                   │
│           │                                             │
│  ┌────────▼─────────┬──────────────┬─────────────┐     │
│  │ Vertrag-Service  │ Schaden-Svc  │ Partner-Svc │     │
│  │ (REST Controller)│              │             │     │
│  └────────┬─────────┴──────┬───────┴─────┬───────┘     │
│           │                │             │             │
│  ┌────────▼────────────────▼─────────────▼───────┐     │
│  │        JDBC Connection Pool                   │     │
│  └────────┬──────────────────────────────────────┘     │
│           │                                             │
└───────────┼─────────────────────────────────────────────┘
            │
            ▼ JDBC
    [Oracle Database]
```

**Fragen während Zeichnen**:
- "Haben wir **einen Service pro Bounded Context** (aus Tag 1)?" → Ja empfohlen
- "Wo ist **Authentication**?" → API Gateway (OAuth2 / Azure AD?)
- "Wie trennen wir **MVP-Masken** von späteren Phasen?" → Versionierung (v1, v2?)

##### Schritt 2: AI-Komponenten hinzufügen (10min)

**Basierend auf Aktivität 6 Entscheidung**:

**Wenn MCP Server + Spring AI Hybrid**:

> "Wo platzieren wir **AI-Komponenten**?"

**Zeichnen**:
```
┌─────────────────────────────────────────────────────────┐
│  INTEGRATION LAYER                                      │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  ┌──────────────────┐       ┌─────────────────┐        │
│  │  Spring Boot API │◄──────┤   MCP Server    │        │
│  │  Gateway         │       │  (AI Agents +   │        │
│  └──────────────────┘       │   RBAC)         │        │
│           │                 └────────┬────────┘        │
│           │                          │                 │
│           ▼                          ▼                 │
│  ┌──────────────────┐       ┌─────────────────┐        │
│  │  Business        │       │  LLM API        │        │
│  │  Services        │       │  (Azure OpenAI) │        │
│  └──────────────────┘       └─────────────────┘        │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

**Verbindungen zeichnen**:
- MCP Server → Oracle DB (für Tool-Access)
- MCP Server → LLM API
- Spring Boot → MCP Server (für AI-Features)

##### Schritt 3: Deployment Layer hinzufügen (10min)

**Basierend auf Aktivität 5 Entscheidung**:

**Wenn Azure Container Apps gewählt**:

> "Wie wird das Ganze **deployed**?"

**Zeichnen** (Deployment View):
```
┌─────────────────────────────────────────────────────────┐
│  AZURE CLOUD                                            │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │  Azure Container Apps                            │   │
│  │  ┌──────────────┐  ┌──────────────┐             │   │
│  │  │ Frontend     │  │ Spring Boot  │             │   │
│  │  │ Container    │  │ Container    │             │   │
│  │  └──────────────┘  └──────────────┘             │   │
│  │  ┌──────────────┐                               │   │
│  │  │ MCP Server   │                               │   │
│  │  │ Container    │                               │   │
│  │  └──────────────┘                               │   │
│  └───────────────────┬──────────────────────────────┘   │
│                      │                                  │
│  ┌───────────────────▼──────────────────────────────┐   │
│  │  Azure Virtual Network                           │   │
│  │  (Private Communication)                         │   │
│  └───────────────────┬──────────────────────────────┘   │
│                      │                                  │
└──────────────────────┼──────────────────────────────────┘
                       │
                       ▼ Private Endpoint
            ┌──────────────────────┐
            │  Oracle Database     │
            │  (On-Prem or Azure?) │
            └──────────────────────┘
```

**Fragen**:
- "Wo läuft Oracle DB?" → On-Prem? Azure VM? Managed?
- "Wie wird **Netzwerk-Zugriff** geregelt?" → VPN? Private Endpoint?

##### Schritt 4: Externe Systeme & Integrationen (5min)

**Basierend auf Tag 1 Domain Map (Frame 3)**:

> "Welche **externen Systeme** müssen wir anbinden?"

**Aus Architektur-Dokumentation** (`architektur_schaubild_icis_gesamt.md`):
- SAP (Finance)
- COR Life (Lebensversicherung)
- GDV (Branchenstandard)
- DMS (Imagemaster)
- SIP Server (Telefonie)

**Zeichnen**:
```
Spring Boot Integration Layer
    │
    ├─→ [SAP] (via REST? SOAP?)
    ├─→ [COR Life] (via ?)
    ├─→ [GDV MQ Series] (via JMS?)
    ├─→ [DMS Imagemaster] (via REST?)
    └─→ [SIP Server] (via SIP Protocol)
```

**Fragen**:
- "Welche Protokolle?" → WGV erklärt
- "Brauchen wir **Anti-Corruption Layer**?" (aus Tag 1 Context Map)

#### Phase 3: Annotations & Open Questions (10min)

**Facilitator fügt Annotations hinzu** (Miro Sticky Notes):

**Entscheidungen markieren** (grüne Stickies):
- ✅ "Spring Boot als Integration Layer"
- ✅ "Azure Container Apps für Deployment"
- ✅ "MCP Server für AI Agents"

**Offene Fragen markieren** (gelbe Stickies):
- ❓ "Oracle DB: On-Prem oder Azure Migration?"
- ❓ "GDV MQ Series: Wie anbinden? JMS Adapter?"
- ❓ "Frontend Framework: React vs. Angular (Tag 3)"

**Risiken markieren** (rote Stickies):
- ⚠️ "Netzwerk-Latenz Oracle DB → Azure (wenn getrennt)"
- ⚠️ "SAP Integration: Alter SOAP-Service, möglicherweise deprecated"

### Output

✅ **Architektur-Diagramm (Draft)** mit:
- 4 Layern (Frontend, Integration, Database, External)
- Detaillierte Integration Layer (Spring Boot + AI)
- Deployment View (Azure Container Apps)
- Externe System-Integrationen
- Annotations (Entscheidungen, Offene Fragen, Risiken)

📸 **Screenshot/Export**: Miro Frame 12 als PDF/PNG exportieren für Dokumentation

🚧 **Status**: **Draft** - wird in Phase 0 verfeinert

---

## End of Day 2: Wrap-Up & Review

**Dauer**: 15-20min (optional, falls Zeit übrig)

### Recap der Outputs

**Facilitator fasst zusammen**:

> "Heute haben wir **entschieden**:
> 1. ✅ **MVP-Scope**: 3-5 Masken validiert (technisch machbar)
> 2. ✅ **Service-SP-Katalog**: X SPs dokumentiert
> 3. ✅ **Integration Layer**: [Spring Boot / ORDS / Hybrid]
> 4. ✅ **Deployment**: [Azure Container Apps / K8s / Docker]
> 5. ✅ **AI Integration**: [MCP / Spring AI / Hybrid]
> 6. ✅ **Architektur-Diagramm**: Draft steht
> 
> **Morgen (Tag 3)**: Frontend-Framework, AI-Driven Development Workshop, Roadmap"

### Offene Fragen Review

**Parking Lot durchgehen** (sammeln für Post-Workshop):

**Kategorien**:
- **Für Phase 0 klären**: [z.B. Oracle DB Hosting, GDV-Integration]
- **Für WGV IT klären**: [z.B. Azure Account, Compliance-Anforderungen]
- **Technische Spikes**: [z.B. PL/SQL Type-Mapping, MCP PoC]

### Hausaufgaben (optional)

**Falls WGV Informationen nachreichen soll**:
- [ ] SP-Dokumentation vervollständigen (für undokumentierte SPs)
- [ ] Oracle DB Hosting klären (On-Prem vs. Azure)
- [ ] Testdaten-Zugänge organisieren

---

## Post-Workshop: ADR Formalisierung

**Nach Tag 2** (codecentric Aufgabe):

Für jede Technologie-Entscheidung (Aktivität 4, 5, 6):
- **ADR erstellen** (Architecture Decision Record)
- **Format** (Markdown):

```markdown
# ADR-001: Integration Layer - Spring Boot

**Status**: Accepted  
**Datum**: 29.04.2026  
**Entscheider**: WGV Architekten + codecentric Team  

## Context

Wir müssen entscheiden, welche Technologie wir für die Integration Layer zwischen Frontend und Oracle Database nutzen.

## Decision

Wir nutzen **Spring Boot** (mit Option für ORDS in Phase 2+).

## Rationale

- AI-Integration (MCP Server) benötigt Java-Backend
- Vendor Lock-In vermeiden (cloud-agnostic)
- Team Skills: Java verbreiteter als ORDS
- Flexibilität für komplexe Orchestrierung

## Alternatives Considered

- **Oracle ORDS**: Schneller für einfache CRUD, aber Oracle-locked
- **Hybrid (ORDS + Spring Boot)**: Zu komplex für MVP

## Consequences

**Positive**:
- Flexibilität, Cloud-Portabilität, AI-ready

**Negative**:
- Mehr Entwicklungsaufwand vs. ORDS
- PL/SQL Custom Type-Mapping nötig

## Follow-Up Actions

- [ ] Spring Boot Boilerplate (Phase 0)
- [ ] PL/SQL Type-Mapping Spike (Phase 0)
```

**Alle ADRs** committen in Repository: `/docs/architecture/decisions/`

---

## Erfolgskriterien - Tag 2

Am Ende von Tag 2 haben wir erfolgreich:

✅ **Verfeinerter MVP-Scope** (3-5 Masken technisch validiert)  
✅ **Service-SP-Katalog** (Signaturen dokumentiert)  
✅ **3 Technologie-Entscheidungen** (Integration Layer, Deployment, AI Integration)  
✅ **Architektur-Diagramm (Draft)** der Zielarchitektur  
✅ **ADR-Vorlagen** für Post-Workshop-Formalisierung  
✅ **Identifizierte Risiken & Offene Fragen** (Parking Lot)  
✅ **Gemeinsames technisches Verständnis** zwischen WGV und codecentric  

**Ready für Tag 3**: Technologiestack definiert → Frontend-Framework + AI-Driven Dev Workshop

---

**Erstellt**: 2026-04-17  
**Autor**: Sócrates Ponce (codecentric)  
**Workshop**: WGV ICIS Modernisierung, 28-30 April 2026  
**Version**: 1.0
