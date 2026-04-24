# Tag 1: Masken Pattern Katalog

**Workshop**: WGV ICIS Modernisierung  
**Aktivität**: Analyse von Masken (stichprobenartig)  
**Verwendung**: Pattern-Matching für Migration-Ansatz  
**Zielgruppe**: Nutzer, Architekten, Developer

---

## Zweck dieses Dokuments

**codecentric Vorschlag**: Wir schlagen einen Pattern-Katalog mit **8 Masken-Typen** vor, um Oracle Forms im ICIS-System systematisch zu klassifizieren und jedem Pattern einen konkreten Migrations-Ansatz zuzuordnen.

**Wichtig**: Alle Migrations-Ansätze sind **Oracle-agnostisch** (kein APEX) und basieren auf modernen Cloud-native Technologien (React/Angular, Azure, Kubernetes).

**Verwendung**:
- ✅ **Während Tag 1 Maskenanalyse**: Pattern-Matching für 10-15 repräsentative Masken
- ✅ **Als Referenz**: Gemeinsames Vokabular zwischen codecentric und WGV
- ✅ **Post-Workshop**: WGV kann neue Masken selbständig klassifizieren

**Ergänzt**:
- `tag1_maskenanalyse_guide.md` (Methodik)
- `tag1_maskenanalyse_fragenkatalog.md` (Fragenkatalog)

---

## Pattern-Klassifikation: 2×2 Complexity Matrix

Alle Patterns werden nach **zwei Dimensionen** klassifiziert:

### Dimension 1: UI Complexity (Oberflächenkomplexität)

| Bewertung | Kriterien | Typische Merkmale |
|-----------|-----------|------------------|
| **Simple** | <20 Felder, Single-Tab, Standard-Layout | Einfaches Formular, lineare Eingabe |
| **Complex** | >30 Felder, Multi-Tab, dynamische Felder | Verschachtelte Tabs, bedingte Felder, Custom Controls |

### Dimension 2: Logic Complexity (Geschäftslogik-Komplexität)

| Bewertung | Kriterien | Typische Merkmale |
|-----------|-----------|------------------|
| **Simple** | CRUD, Basic Validation, 0-1 SPs | Daten erfassen/anzeigen, einfache Prüfungen |
| **Complex** | Berechnungen, Workflows, 3+ SPs, Integrationen | Tarifberechnung, Risikoprüfung, externe Systeme |

### Matrix-Darstellung

```
              Logic Complexity
                    │
        ┌───────────┼───────────┐
        │  Q2       │    Q4     │
   UI   │ UI-Heavy  │  Full     │
        │           │  Custom   │
   C  ──┼───────────┼───────────┼──
   o    │  Q1       │    Q3     │
   m    │ Quick     │  Logic-   │
   p    │ Wins      │  Heavy    │
   l    │           │           │
   e    └───────────┴───────────┘
   x                │
   i          Simple      Complex
   t
   y
```

**Quadranten**:
- **Q1 (Simple UI, Simple Logic)**: Quick Wins → AI-assisted React/Angular
- **Q2 (Complex UI, Simple Logic)**: UI-Heavy → React/Angular (UI-Fokus)
- **Q3 (Simple UI, Complex Logic)**: Logic-Heavy → Backend-first
- **Q4 (Complex UI, Complex Logic)**: Full Custom → AI-assisted Development

---

## Pattern-Katalog (codecentric Vorschlag: 8 Patterns)

### Pattern P1: Simple CRUD

**Quadrant**: Q1 (Simple UI, Simple Logic)

**Charakteristik**:
- ✅ <20 Felder
- ✅ Single Entity (z.B. Adresse, Notiz, Kommentar)
- ✅ Basic Validation (Pflichtfelder, Format-Prüfung)
- ✅ 0-1 Stored Procedures (INSERT/UPDATE/DELETE)
- ✅ Kein Workflow, keine Berechnungen

**Migrations-Ansatz**: **React/Angular** mit **AI-Code-Generierung** (Claude Code, GitHub Copilot)

**Strategie**:
- Schema-basierte Formular-Generierung
- Standard CRUD-Pattern (Create, Read, Update, Delete)
- Wiederverwendbare Form-Komponenten

**Aufwand**: 1-2 Wochen

**Beispiel-Masken** (hypothetisch):
- Adressänderung Kunde
- Notiz erfassen zu Vertrag
- Kontakthistorie-Eintrag

**UI-Pattern**: Standard-Formular (single page)

**Backend-Integration**: 
- 1 REST Endpoint: `POST /kunden/{id}/adresse`
- Wrapper für SP: `SP_ADRESSE_AKTUALISIEREN`

**Risiken**: ⚠️ Niedrig (etabliertes Pattern)

**AI-Unterstützung**:
- Formular-Code aus DB-Schema generieren lassen
- Validation-Logik aus Constraints ableiten
- Standard CRUD-Operations scaffolden

---

### Pattern P2: Search & Filter

**Quadrant**: Q1 (Simple UI, Simple Logic) oder Q2 (wenn Filter komplex)

**Charakteristik**:
- ✅ Filterkriterien-Eingabe (5-15 Filter-Felder)
- ✅ Ergebnisliste (Tabelle mit Pagination)
- ✅ Export-Funktion (Excel/PDF)
- ✅ 1 Stored Procedure (Search Query mit dynamischen Filtern)
- ✅ Read-only (keine Datenänderung)

**Migrations-Ansatz**: **React/Angular** mit React Table oder AG Grid

**Aufwand**: 1-2 Wochen

**Beispiel-Masken** (hypothetisch):
- Partnersuche (Kunde/Vermittler suchen)
- Vertragssuche
- Schadensuche

**UI-Pattern**: 
- Oberer Bereich: Filter-Panel (kollapsierbar)
- Unterer Bereich: Ergebnistabelle (sortierbar, filterbar)
- Actions: Export, Details anzeigen

**Backend-Integration**:
- 1 REST Endpoint: `GET /partner/search?name=...&ort=...`
- Wrapper für SP: `SP_PARTNER_SUCHEN(p_filters IN VARCHAR2, p_result OUT SYS_REFCURSOR)`

**Risiken**: ⚠️ Niedrig (Standard-Pattern)

**Besonderheit**: Performance bei großen Resultsets (Pagination serverseitig)

**AI-Unterstützung**:
- React Table Setup generieren
- Filter-Komponenten aus Schema
- Export-Funktionen (Excel/PDF) scaffolden

---

### Pattern P3: Multi-Tab Form

**Quadrant**: Q2 (Complex UI, Simple Logic)

**Charakteristik**:
- ✅ 30-60 Felder verteilt auf 3-5 Tabs
- ✅ Entity + Related Entities (z.B. Kunde + Adressen + Kontakte)
- ✅ CRUD Operations auf mehreren Entities
- ✅ 2-3 Stored Procedures (je Entity eine)
- ✅ Validierung über Tabs hinweg (z.B. "Mind. eine Adresse")

**Migrations-Ansatz**: **React/Angular** mit Tab-Navigation (Material UI / Angular Material)

**Aufwand**: 2-3 Wochen

**Beispiel-Masken** (hypothetisch):
- Kundenstammdaten (Tabs: Basisdaten, Adressen, Kontakte, Bankverbindungen)
- Vertragsstammdaten (Tabs: Vertrag, Versicherte Objekte, Klauseln, Dokumente)

**UI-Pattern**:
- Tab-Navigation (Material UI Tabs / Angular Material)
- Jeder Tab = eigenes Formular
- Speichern: Alle Tabs validieren, dann gemeinsam speichern

**Backend-Integration**:
- Multi-Entity REST API:
  - `GET /kunden/{id}` (inkl. Relations)
  - `PUT /kunden/{id}` (inkl. Relations in einem Request)
- Wrapper für SPs: 
  - `SP_KUNDE_AKTUALISIEREN`
  - `SP_ADRESSE_AKTUALISIEREN`
  - `SP_KONTAKT_AKTUALISIEREN`

**Risiken**: 
- ⚠️ Mittel: Tab-Synchronisation (Änderungen in Tab 1 beeinflussen Tab 2?)
- ⚠️ Transaktions-Management (Rollback bei Fehler in Tab 3?)

**AI-Unterstützung**:
- Tab-Struktur aus Entity-Relationships generieren
- Form-Validierung über Tabs hinweg
- State Management (React Context / Redux)

**Migrations-Variante: Inkrementeller Ansatz (P1 → P3)**

Für komplexe P3-Masken mit 4+ Tabs kann eine **stufenweise Migration** sinnvoll sein:

**Phase 1: N × P1 (Separate Screens)**
- Jeder Tab wird als **eigenständige P1-Maske** migriert
- N separate Screens statt Tab-Navigation
- Aufwand: N × 1-2 Wochen (parallelisierbar)
- Schnellerer Rollout, niedrigeres Risiko pro Release

**Phase 2: P3-Komposition (Integration)**
- Tab-Navigation UI hinzufügen
- Koordinierte Transaktionen implementieren
- Cross-Tab-Validierung ergänzen
- Aufwand: +1-2 Wochen (zusätzlich)

**Wann empfehlenswert?**
- ✅ P3 mit 4+ Tabs
- ✅ Tabs sind weitgehend unabhängig (wenig Cross-Tab-Validierung)
- ✅ Time-to-Market-Druck (Nutzer brauchen schnell erste Funktionen)
- ✅ Strangler Fig Pattern (schrittweise Ablösung)

**Wann vermeiden?**
- ❌ Kritische Cross-Tab-Validierung (z.B. "Summe aller Tabs muss X ergeben")
- ❌ Nur 2-3 Tabs (Overhead zu groß)
- ❌ Nutzer akzeptieren keine UX-Regression (Multi-Screen statt Tabs)

**Trade-offs**:
- 👍 Schnellere Wertlieferung (Early Wins)
- 👍 Niedrigeres Risiko pro Release
- 👍 Parallelisierbare Entwicklung
- 👎 Temporäre UX-Degradation (Multi-Screen-Navigation)
- 👎 Rework in Phase 2 (P1-Code für P3 anpassen)
- 👎 Cross-Entity-Validierung erst in Phase 2

**Beispiel**: Kundenstammdaten (4 Tabs)
- **Phase 1 (Wochen 1-8)**: 
  - Release 1: Basisdaten (P1, 2 Wochen)
  - Release 2: Adressen (P1, 2 Wochen)
  - Release 3: Kontakte (P1, 2 Wochen)
  - Release 4: Bankverbindungen (P1, 2 Wochen)
- **Phase 2 (Wochen 9-10)**: 
  - Tab-Navigation + Koordinierte Transaktionen (2 Wochen)
  - **Gesamt: 10 Wochen** (statt 3 Wochen Direktmigration zu P3, aber verteilt über mehrere Releases)

---

### Pattern P4: Wizard Workflow

**Quadrant**: Q1-Q3 (abhängig von Logic Complexity)

**Charakteristik**:
- ✅ 3-6 Steps (lineare oder bedingte Navigation)
- ✅ Jeder Step = Datensammlung
- ✅ Finale Submission am Ende
- ✅ 1-3 Stored Procedures (je nach Komplexität)
- ✅ Zwischenspeichern möglich (Draft Mode)

**Migrations-Ansatz**: **React/Angular** mit Stepper-Komponente (Material UI Stepper / Angular CDK Stepper)

**Aufwand**: 2-3 Wochen (linear) oder 3-4 Wochen (bedingte Navigation)

**Beispiel-Masken** (hypothetisch):
- Antragswizard Neugeschäft (Steps: Kunde auswählen → Tarif wählen → Optionen → Prüfung → Abschluss)
- Schadenanlage Wizard (Steps: Schadenart → Beteiligte → Schaden-Details → Dokumente → Abschluss)

**UI-Pattern**:
- Stepper (Material UI Stepper / Angular Stepper)
- "Zurück" / "Weiter" Navigation
- Progress Bar
- Final Review Step

**Backend-Integration**:
- **Option A**: Draft API (zwischenspeichern)
  - `POST /antraege/draft` (nach jedem Step)
  - `POST /antraege/{id}/submit` (finaler Abschluss)
- **Option B**: Single Submit (nur am Ende)
  - `POST /antraege` (komplettes Objekt)

**Risiken**:
- ⚠️ Mittel: Bedingte Navigation (Step 3 hängt von Antwort in Step 1 ab)
- ⚠️ Validation über Steps hinweg (z.B. "Gesamtprämie muss passen")

**AI-Unterstützung**:
- Wizard-Struktur aus Prozess-Beschreibung generieren
- Step-Validierung automatisch ableiten
- Navigation-Logik scaffolden

---

### Pattern P5: Calculation-Heavy

**Quadrant**: Q3 (Simple UI, Complex Logic)

**Charakteristik**:
- ✅ 10-20 Input-Felder
- ✅ Komplexe Berechnung (Stored Procedure)
- ✅ Ergebnis-Anzeige (oft nicht editierbar)
- ✅ 1-2 Stored Procedures (Berechnung + optional Speichern)
- ✅ Oft iterativ ("Was-wäre-wenn"-Szenarien)

**Migrations-Ansatz**: **Integration-Layer-First** (REST API-Wrapper für SP + einfaches React/Angular UI)

**Aufwand**: 2-3 Wochen (SP-Integration + UI)

**Beispiel-Masken** (hypothetisch):
- Tarifberechnung / Prämienrechner
- Risikoberechnung
- Rückstellungsberechnung

**UI-Pattern**:
- Input-Panel (links oder oben)
- "Berechnen" Button
- Ergebnis-Panel (rechts oder unten, oft Read-Only)
- Optional: "Szenario speichern"

**Backend-Integration**:
- REST Endpoint: `POST /tarif/berechnen`
  - Request: Input-Parameter (JSON)
  - Response: Berechnungs-Ergebnis (JSON)
- Wrapper für SP: `SP_TARIF_BERECHNEN(p_input IN ..., p_result OUT ...)`

**Risiken**:
- ⚠️ Hoch: **Stored Procedure ist Black Box** (undokumentierte Business Rules)
- ⚠️ Performance (komplexe Berechnungen können langsam sein)
- ⚠️ Testing (wie validieren wir Korrektheit der Berechnung?)

**Besonderheit**: **SP-Logik nicht neu schreiben** (zu riskant) → Wrapper-Ansatz

**AI-Unterstützung**:
- Input-Form aus SP-Parametern generieren
- Result-Display aus SP-Output-Struktur
- API-Wrapper-Code scaffolden

---

### Pattern P6: Complex Workflow

**Quadrant**: Q4 (Complex UI, Complex Logic)

**Charakteristik**:
- ✅ >40 Felder verteilt auf mehrere Tabs/Steps
- ✅ Non-lineare Navigation (bedingte Steps)
- ✅ 3+ Stored Procedures
- ✅ Externe System-Integrationen (SAP, GDV, DMS)
- ✅ Komplexe Business Rules (Risikoprüfung, Genehmigungsworkflow)
- ✅ Multi-User (z.B. Antrag + Genehmigung)

**Migrations-Ansatz**: **Full Custom Development** (AI-assisted mit Claude Code / GitHub Copilot)

**Aufwand**: 4-8 Wochen

**Beispiel-Masken** (hypothetisch):
- Vertragsabschluss Neugeschäft (komplex)
- Risikoprüfung mit Genehmigungsworkflow
- Schadenanlage KFZ (mit Gutachter-Integration)

**UI-Pattern**:
- Hybrid: Wizard (für linearen Teil) + Tabs (für Details)
- Dynamische Felder (basierend auf vorherigen Eingaben)
- Statusanzeige (Draft → In Prüfung → Genehmigt → Abgeschlossen)

**Backend-Integration**:
- Multi-Endpoint REST API:
  - `POST /vertraege/draft` (Zwischenspeichern)
  - `POST /vertraege/{id}/calculate` (Tarifberechnung)
  - `POST /vertraege/{id}/risk-check` (Risikoprüfung)
  - `POST /vertraege/{id}/submit` (Finaler Abschluss)
  - `GET /vertraege/{id}/status` (Status-Abfrage)
- Wrapper für SPs:
  - `SP_TARIF_BERECHNEN`
  - `SP_VERTRAG_ANLEGEN`
  - `SP_RISIKO_PRUEFEN`
  - External API Calls (SAP, DMS)

**Risiken**:
- 🔴 **Sehr hoch**: Viele Abhängigkeiten (SPs, externe Systeme)
- 🔴 Knowledge Risk (nur 1-2 Experten kennen Maske)
- 🔴 Testing-Aufwand (End-to-End Tests komplex)
- 🔴 Integration Testing (SAP, GDV Mock nötig?)

**Besonderheit**: **MVP-Kandidat für Phase 2-3**, nicht Phase 1 (zu riskant)

**AI-Unterstützung**:
- Komplexe Forms mit AI-gestützter Code-Generierung
- Integration-Tests generieren lassen
- Workflow-State-Machine aus Beschreibung

---

### Pattern P7: Report Generator

**Quadrant**: Q1 (Simple UI, Simple Logic)

**Charakteristik**:
- ✅ Parameter-Eingabe (5-15 Felder)
- ✅ Report-Generierung (PDF, Excel, Word)
- ✅ 1 Stored Procedure (Report Query)
- ✅ Template-basiert (Oracle Reports → moderne Template Engine)

**Migrations-Ansatz**: **React/Angular** + PDF/Excel Library (JasperReports, jsPDF, ExcelJS)

**Strategie**:
- Oracle Reports Templates → JasperReports oder Custom Template Engine migrieren
- Parameter-UI in React/Angular
- Backend: Template Rendering (JasperReports + Spring Boot)

**Aufwand**: 2-3 Wochen (Template-Migration ist Hauptaufwand)

**Beispiel-Masken** (hypothetisch):
- Vertragsdokumentation generieren
- Schadensbericht erstellen
- Monatsabschluss-Report

**UI-Pattern**:
- Parameter-Formular (einfach)
- "Generieren" Button
- Preview (optional)
- Download / Drucken

**Backend-Integration**:
- REST Endpoint: `POST /reports/vertrag/{id}/generate`
  - Request: Parameter (JSON)
  - Response: PDF-Download (Binary)
- Wrapper für SP: `SP_VERTRAG_REPORT_DATEN(p_vertrag_id IN NUMBER, p_cursor OUT SYS_REFCURSOR)`
- Template Engine: JasperReports, Apache POI, oder PDF-Library (jsPDF, PDFKit)

**Risiken**:
- ⚠️ Mittel: **Template-Migration** (Oracle Reports → moderne Library)
- ⚠️ Layout-Treue (muss 1:1 aussehen wie alte Reports?)
- ⚠️ Regulatorisch (GDV-konforme Dokumente → Layout kritisch)

**Besonderheit**: 
- Oft regulatorisch (GDV-konforme Dokumente) → **Layout-Treue kritisch**
- Viele ähnliche Masken → **Template wiederverwenden**

**AI-Unterstützung**:
- Parameter-Form generieren
- PDF-Template aus Oracle Reports Layout konvertieren (teilweise)
- Report-Download-Logik scaffolden

---

### Pattern P8: Conversational Candidate

**Quadrant**: Q4 (Complex UI, Complex Logic) → aber **neue Interaktion**

**Charakteristik**:
- ✅ Viele Fragen / Verzweigungen
- ✅ Guidance nötig ("Was muss ich tun?")
- ✅ Unterschiedliche User-Typen (Experte vs. Gelegenheitsnutzer)
- ✅ Potential für AI-Unterstützung (NLP, Vorausfüllen)

**Migrations-Ansatz**: **Hybride Lösung** (Chatbot + React/Angular Form)

**Strategie**:
- Conversational UI für Guided Input
- Klassisches Formular als Fallback / Review
- MCP-basierte AI-Integration für Intent Recognition & Entity Extraction

**Aufwand**: 4-8 Wochen (Experimentell, Prototyping)

**Beispiel-Masken** (hypothetisch):
- Schadenmeldung einfach (Guided Input via Chatbot)
- Kundenanfrage / Beratung (Conversational + Formular)
- Selbstauskunft Kunde (KYC-Prozess)

**UI-Pattern**:
- **Conversational UI** (Chat-Interface) für Fragen
- **Form UI** (klassisches Formular) für Details/Review
- Umschalt-Möglichkeit ("Ich will lieber das Formular ausfüllen")

**Backend-Integration**:
- REST API (wie Standard-Maske)
- **AI Layer** (MCP-basiert):
  - Intent Recognition (Was will der Nutzer?)
  - Entity Extraction (Daten aus Chat-Konversation)
  - Pre-Fill (Formular vorausfüllen basierend auf Chat)
  - Validation Support (Chatbot erklärt Fehler)

**Risiken**:
- 🔴 **Sehr hoch**: Experimentelles Pattern (wenig Best Practices)
- 🔴 AI-Risiken (Halluzination, falsche Daten)
- 🔴 UX-Risiko (Nutzer akzeptieren Chatbot?)
- 🔴 Hybrid-Complexity (Chat + Form sync)

**Besonderheit**: 
- **Experiment für Tag 3** (AI-Driven Development Workshop)
- Nicht für MVP Phase 1, aber **Proof-of-Concept** interessant

**AI-Unterstützung**:
- Conversational Flow aus Prozess-Beschreibung
- Intent-Training-Daten generieren
- Chat-to-Form Mapping

---

## Pattern-Übersicht Matrix

| Pattern ID | Pattern Name | UI | Logic | Quadrant | Migrations-Ansatz | Aufwand |
|------------|--------------|----|----|----------|------------------|---------|
| **P1** | Simple CRUD | Simple | Simple | Q1 | React/Angular (AI-generiert) | 1-2w |
| **P2** | Search & Filter | Simple/Complex | Simple | Q1/Q2 | React/Angular + Data Grid | 1-2w |
| **P3** | Multi-Tab Form | Complex | Simple | Q2 | React/Angular (Tabs) | 2-3w |
| **P4** | Wizard Workflow | Variable | Variable | Q1-Q3 | React/Angular (Stepper) | 2-4w |
| **P5** | Calculation-Heavy | Simple | Complex | Q3 | Integration-Layer-First + Simple UI | 2-3w |
| **P6** | Complex Workflow | Complex | Complex | Q4 | Full Custom (AI-assisted) | 4-8w |
| **P7** | Report Generator | Simple | Simple | Q1 | React/Angular + Template Engine | 2-3w |
| **P8** | Conversational Candidate | Complex | Complex | Q4 | Chatbot + Form Hybrid (MCP) | 4-8w |

---

## Technology Stack pro Pattern

| Pattern | Frontend | Backend | AI-Tooling | Besonderheit |
|---------|----------|---------|-----------|--------------|
| **P1** | React/Angular | Spring Boot REST | Claude Code (Code Gen) | Schema-driven Forms |
| **P2** | React Table / AG Grid | Spring Boot REST | - | Server-side Pagination |
| **P3** | Material UI Tabs | Spring Boot REST | Claude Code (Tab Gen) | Multi-Entity Transactions |
| **P4** | Material UI Stepper | Spring Boot REST | Claude Code (Wizard Gen) | Draft Mode (optional) |
| **P5** | Simple React/Angular | Spring Boot REST | - | SP-Wrapper kritisch |
| **P6** | Custom (Wizard+Tabs) | Spring Boot Multi-API | Claude Code (Full Support) | Externe Integrationen |
| **P7** | React/Angular | JasperReports + Spring | - | Template-Migration |
| **P8** | Custom Chat UI | Spring Boot + MCP | Claude API (MCP) | Experimental |

**Wichtig**: Alle Technologien sind **Oracle-unabhängig** und **Cloud-native** (Azure-ready, Kubernetes-ready).

---

## Pattern-Matching im Workshop

### Schritt 1: 2×2 Matrix Klassifikation (~1 Minute pro Maske)

**Frage 1**: "Ist die UI simple oder complex?"
- **Simple**: <20 Felder, Single-Tab, Standard-Layout
- **Complex**: >30 Felder, Multi-Tab, dynamische Felder

**Frage 2**: "Ist die Logik simple oder complex?"
- **Simple**: CRUD, 0-1 SPs, keine Integrationen
- **Complex**: Berechnungen, 3+ SPs, externe Systeme

**Ergebnis**: Quadrant (Q1, Q2, Q3, Q4)

---

### Schritt 2: Pattern-Matching (~1-2 Minuten pro Maske)

**Frage**: "Welchem Pattern ähnelt diese Maske am meisten?"

**Vorgehen**:
1. Filtere nach Quadrant (z.B. Q1 → nur P1, P2, P7 möglich)
2. Vergleiche mit Pattern-Beschreibungen
3. Wähle ähnlichstes Pattern

**Pattern-Karten zeigen**:
- Für jedes der 8 Patterns: Name + Beispiel + Mockup
- WGV wählt ähnlichstes Pattern

**Ergebnis**: Pattern ID (P1-P8)

---

### Schritt 3: Migrations-Ansatz ableiten (~30 Sekunden)

**Automatisch aus Pattern**:
- Pattern → Migrations-Ansatz (React/Angular, Backend-First, Custom)
- Pattern → Technology Stack (siehe Matrix oben)
- Pattern → Aufwand-Schätzung (1-8 Wochen)

**Dokumentieren in RICE Template**:
- Effort-Spalte: Baseline aus Pattern
- Migrations-Ansatz: Aus Pattern-Katalog
- Technology: Aus Pattern-Stack-Mapping

---

## Verwendung Post-Workshop

### WGV Playbook: "Wie klassifiziere ich eine neue Maske?"

**Schritt 1: Complexity Assessment** (1 Minute)
1. Zähle Felder: <20 = Simple UI, >30 = Complex UI
2. Zähle SPs + Integrationen: 0-1 = Simple Logic, 3+ = Complex Logic
3. Platziere Maske in 2×2 Matrix → Quadrant

**Schritt 2: Pattern Matching** (2 Minuten)
1. Öffne Pattern-Katalog
2. Filtere nach Quadrant (z.B. Q1 → nur P1, P2, P7)
3. Vergleiche Maske mit Patterns in diesem Quadrant
4. Wähle ähnlichstes Pattern

**Schritt 3: Migrations-Ansatz ablesen** (30 Sekunden)
1. Lies Migrations-Ansatz aus Pattern-Tabelle ab
2. Lies Technology Stack ab
3. Lies Aufwand-Schätzung ab
4. Dokumentiere in RICE Scoring Template

**Gesamtzeit**: ~3-4 Minuten pro Maske

---

## Pattern-Discovery Workflow (während Workshop)

Falls wir **neue Patterns** entdecken, die nicht in diesem Katalog sind:

### Neues Pattern dokumentieren

**Template**:

```markdown
### Pattern P9: [Name]

**Quadrant**: Q? (UI Complexity, Logic Complexity)

**Charakteristik**:
- [ ] Merkmal 1
- [ ] Merkmal 2
- [ ] ...

**Migrations-Ansatz**: [React/Angular / Custom / ...]

**Aufwand**: X-Y Wochen

**Beispiel-Masken**: [WGV-Beispiele]

**Risiken**: [Beschreibung]

**AI-Unterstützung**: [Wie kann AI helfen?]
```

**Wann neue Patterns erstellen?**
- Maske passt zu **keinem** der 8 bestehenden Patterns
- Maske repräsentiert **signifikant unterschiedlichen** Migrations-Ansatz
- **≥3 ähnliche Masken** existieren (lohnt sich als Pattern)

---

## Integration mit anderen Dokumenten

### Input aus ICIS Deep Dive

**ICIS+ Komponenten-Wiederverwendung**:
- Pattern P3 (Multi-Tab Form): Können Vaadin-Tab-Logik-Patterns übernommen werden?
- Pattern P2 (Search & Filter): Existiert Filter-Komponente in ICIS+ (Spring-Service)?

**Stored Procedure Inventar**:
- Pattern P5 (Calculation-Heavy): Welche Berechnungs-SPs gibt es?
- Pattern P6 (Complex Workflow): Welche SPs werden kombiniert?

---

### Output für UI/UX Konzept Session

**Pattern → UI Pattern Mapping**:
- Pattern P1, P7 → Standard-Formular
- Pattern P2 → Filter + Table Pattern
- Pattern P3 → Tab-Navigation Pattern
- Pattern P4 → Wizard/Stepper Pattern
- Pattern P5 → Input-Calculation-Result Pattern
- Pattern P6 → Hybrid (Wizard + Tabs)
- Pattern P8 → Conversational UI (Experimentell)

---

### Output für Tag 2

**Pattern → Technology Stack Decisions**:
- P1-P4, P7 → React vs. Angular Decision (Tag 3)
- P5, P6 → Backend Integration Layer (Spring Boot vs. ORDS)
- P8 → MCP Integration (AI Layer)

**Pattern → Architecture Implications**:
- P1-P4 → Standard 3-Tier (Frontend → API → DB)
- P5 → Backend-Heavy (SP-Wrapper kritisch)
- P6 → Multi-Tier (External System Integration)
- P8 → AI Layer (MCP Server)

---

## Visuelle Hilfsmittel (für Workshop)

### Miro-Board Setup

**Frame: Pattern-Katalog**

```
┌─────────────────────────────────────────────────────────┐
│  MASKEN PATTERN-KATALOG (8 Patterns)                    │
│  Oracle-agnostic, Cloud-native                          │
│                                                          │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐             │
│  │ P1       │  │ P2       │  │ P3       │             │
│  │ CRUD     │  │ Search   │  │ Multi-Tab│             │
│  │          │  │          │  │          │             │
│  │ [Mockup] │  │ [Mockup] │  │ [Mockup] │             │
│  │ Q1       │  │ Q1/Q2    │  │ Q2       │             │
│  │ React/AI │  │ React    │  │ React    │             │
│  │ 1-2w     │  │ 1-2w     │  │ 2-3w     │             │
│  └──────────┘  └──────────┘  └──────────┘             │
│                                                          │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐             │
│  │ P4       │  │ P5       │  │ P6       │             │
│  │ Wizard   │  │ Calc     │  │ Complex  │             │
│  │ [Mockup] │  │ [Mockup] │  │ [Mockup] │             │
│  │ Q1-Q3    │  │ Q3       │  │ Q4       │             │
│  │ React    │  │ Backend  │  │ Custom   │             │
│  │ 2-4w     │  │ 2-3w     │  │ 4-8w     │             │
│  └──────────┘  └──────────┘  └──────────┘             │
│                                                          │
│  ┌──────────┐  ┌──────────┐                            │
│  │ P7       │  │ P8       │                            │
│  │ Report   │  │ Chatbot  │                            │
│  │ [Mockup] │  │ [Mockup] │                            │
│  │ Q1       │  │ Q4       │                            │
│  │ React+   │  │ Hybrid+  │                            │
│  │ Template │  │ MCP      │                            │
│  │ 2-3w     │  │ 4-8w     │                            │
│  └──────────┘  └──────────┘                            │
└─────────────────────────────────────────────────────────┘
```

**Interaktion**:
- Masken-Post-Its drag-and-drop auf Pattern-Karten
- Pattern → Migrations-Ansatz wird automatisch zugeordnet

---

### Pattern-Karten (Handout)

**Für jedes Pattern**: A6-Karte mit:
- Pattern ID + Name
- Quadrant (Q1-Q4)
- 3-5 Key Characteristics
- Migrations-Ansatz (Technology Stack)
- Aufwand-Schätzung
- 2 WGV-Beispiele (falls bekannt)

**Verwendung**: WGV kann Karten anfassen, vergleichen, diskutieren

---

## Häufige Fragen (FAQ)

### F: Was, wenn eine Maske zu 2 Patterns passt?

**A**: 
- **Option 1**: Wähle das **dominante** Pattern (was ist die Haupt-Herausforderung?)
- **Option 2**: Markiere als **Hybrid** (z.B. "P3 + P5" = Multi-Tab + Calculation)
- **Implikation**: Aufwand = **Summe** der Patterns (2-3w + 2-3w = 4-6w)

**Beispiel**: Vertragsstammdaten (Multi-Tab) mit Prämienberechnung (Calculation)
- Pattern: P3 + P5 (Hybrid)
- Aufwand: 4-6 Wochen

---

### F: Pattern passt, aber Aufwand-Schätzung scheint zu niedrig?

**A**: 
- Pattern-Aufwand ist **Baseline** (optimaler Fall)
- **Risiko-Faktoren erhöhen Aufwand**:
  - Knowledge Risk (+50%: nur 1 Experte)
  - Integration Complexity (+30% pro externe System)
  - Undokumentierte SPs (+40%)
  - Performance-Probleme (+20%)

**Formel**: `Finale Schätzung = Baseline × (1 + Risiko-Faktoren)`

**Beispiel**: 
- Pattern P5 (Calculation-Heavy): Baseline 2 Wochen
- Risiken: Undokumentierte SP (+40%), 1 Experte (+50%)
- Finale Schätzung: 2w × (1 + 0.4 + 0.5) = 2w × 1.9 = **3.8 Wochen**

---

### F: Sollten wir P3 (Multi-Tab Form) direkt migrieren oder schrittweise (N × P1 → P3)?

**A**: Hängt von **Komplexität**, **Time-to-Market** und **Cross-Tab-Validierung** ab.

**Direktmigration (Standard-Ansatz)**:
- ✅ Wählen wenn: 2-3 Tabs, viel Cross-Tab-Validierung, Nutzer erwarten Tab-UX
- ⏱ Aufwand: 2-3 Wochen
- 📦 Output: Vollständige P3-Maske mit Tab-Navigation

**Inkrementelle Migration (P1 → P3)**:
- ✅ Wählen wenn: 4+ Tabs, wenig Cross-Tab-Validierung, Time-to-Market-Druck
- ⏱ Aufwand: Phase 1 (N × 1-2w parallel) + Phase 2 (1-2w Integration) = **10+ Wochen gesamt, aber verteilt**
- 📦 Output: Early Wins (jeder Tab einzeln nutzbar), dann finale P3-Integration

**Entscheidungskriterien**:

| Kriterium | Direktmigration | Inkrementell (P1 → P3) |
|-----------|----------------|----------------------|
| Anzahl Tabs | 2-3 | 4+ |
| Cross-Tab-Validierung | Viel | Wenig |
| Time-to-Market | Kann warten (2-3w) | Dringend (erste Funktion nach 1-2w) |
| Nutzer-Akzeptanz | Tab-UX erwartet | Multi-Screen OK |
| Aufwand gesamt | 2-3 Wochen | 10+ Wochen (aber verteilt) |

**Empfehlung**: **Direktmigration** ist Standard. **Inkrementell** nur bei klarem Business-Case (Early Wins kritisch, Tabs unabhängig).

**Siehe auch**: Pattern P3 → Abschnitt "Migrations-Variante: Inkrementeller Ansatz"

---

### F: Können wir neue Patterns hinzufügen?

**A**: **Ja!** Katalog ist **erweiterbar**.

**Kriterien für neues Pattern**:
- ✅ Signifikant unterschiedlicher Migrations-Ansatz
- ✅ ≥3 ähnliche Masken existieren
- ✅ Nicht abgedeckt durch bestehende 8 Patterns

**Prozess**:
1. Dokumentiere Pattern (siehe Template oben)
2. Vergib Pattern ID (P9, P10, ...)
3. Füge zu Pattern-Übersicht Matrix hinzu
4. Erstelle Pattern-Karte für Miro

---

### F: Warum nicht Oracle APEX für Quick Wins (P1, P7)?

**A**: 

**Problem mit APEX**:
- ❌ **Oracle-Vendor-Lock-in** (bleibt in Oracle-Ökosystem)
- ❌ Nicht Cloud-agnostic (schwierige Azure-Migration)
- ❌ Langfristig: Gleiche Abhängigkeit wie Oracle Forms

**Vorteil von React/Angular (auch für Simple Patterns)**:
- ✅ **Oracle-unabhängig** (moderne Tech Stack)
- ✅ **Cloud-native** (Azure, Kubernetes ready)
- ✅ **AI-Tooling-Unterstützung** (Claude Code, Copilot generieren CRUD-Forms schnell)
- ✅ **Wiederverwendbarkeit** (gleicher Stack wie komplexe Masken)
- ✅ **Langfristig**: Einheitlicher Tech Stack (1 Team, 1 Skillset)

**Aufwand-Vergleich**:
- APEX: 0.5-1 Woche (schneller initial)
- React/Angular (AI-generiert): 1-2 Wochen (etwas länger, aber zukunftssicher)

**Entscheidung**: **Leicht höherer initialer Aufwand** (1-2w statt 0.5-1w) ist **akzeptabel** für **Oracle-Unabhängigkeit**.

---

### F: Was ist der Unterschied zwischen P4 (Wizard) und P6 (Complex Workflow)?

**A**: 

| Kriterium | P4 (Wizard) | P6 (Complex Workflow) |
|-----------|-------------|----------------------|
| **Navigation** | Linear (Step 1 → 2 → 3) oder einfache Verzweigung | Non-linear, komplexe Verzweigungen |
| **Steps** | 3-6 Steps | Oft >6 Steps + Tabs |
| **SPs** | 1-3 SPs | 3+ SPs |
| **Integrationen** | Selten | Häufig (SAP, GDV, DMS) |
| **Aufwand** | 2-4 Wochen | 4-8 Wochen |
| **Risiko** | Mittel | Sehr hoch |

**Beispiel P4**: Antragswizard (5 Steps, linear, 2 SPs)  
**Beispiel P6**: Vertragsabschluss (8 Steps + 4 Tabs, nicht-linear, 5 SPs, SAP-Integration)

---

## Änderungshistorie

| Version | Datum | Änderung | Autor |
|---------|-------|----------|-------|
| 1.0 | 2026-04-22 | Initiale Erstellung (8 Patterns, Oracle-agnostic) | Sócrates Ponce (codecentric) |

---

## Nächste Schritte

**Vor Workshop**:
1. ✅ Miro Pattern-Karten vorbereiten (8 Karten mit Mockups)
2. ✅ Handout drucken (A6-Karten für jedes Pattern)
3. ✅ WGV bitten, 2-3 Beispiel-Masken pro Pattern zu nennen (Pre-Workshop Email)

**Während Workshop**:
1. ✅ Pattern-Katalog als codecentric Vorschlag vorstellen (~10min)
2. ✅ 10-15 Masken klassifizieren (Pattern-Matching)
3. ✅ Neue Patterns dokumentieren (falls entdeckt) oder bestehende anpassen

**Nach Workshop**:
1. ✅ Katalog finalisieren (ggf. neue Patterns ergänzen)
2. ✅ WGV-Beispiele in Katalog aufnehmen
3. ✅ An WGV übergeben als Referenz-Dokument
