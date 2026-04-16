# Tag 1: Domain Mapping & Discovery - Facilitator Guide

**Workshop**: WGV ICIS Modernisierung  
**Zielgruppe**: Nutzer, Architekten, (optional: PO/Projektleiter, Developer)  
**Dauer**: ~1.5h für "Domäne erkennen" + Integration in weitere Tag 1 Aktivitäten  
**Ansatz**: Domain-Driven Design (DDD) - Event Storming, Context Mapping, Domain Storytelling

---

## Zielsetzung

Am Ende der Domain Mapping Session haben wir:

✅ **5-8 identifizierte Bounded Contexts** mit klaren Grenzen  
✅ **Domänenkarte** mit Integration Patterns (Context Map)  
✅ **Priorisierung** der Domänen nach Business Value und Komplexität  
✅ **Ubiquitous Language Glossar** für kritische Fachbegriffe  
✅ **2-3 detaillierte User Journeys** durch verschiedene Bounded Contexts  

**Output für Tag 2**: Basis für technische Validierung und Scope-Festlegung

---

## Domain-Kandidaten (Hypothesen basierend auf Architektur)

### Core Domains (Wettbewerbsvorteil)
- **Schaden (Claims Management)**: Schadensbearbeitung, Workflows
- **Vertrag (Contract/Policy Management)**: Policy Lifecycle, Vertragsführung
- **Kunde (Customer Management)**: Kundendaten, Adressen, Beziehungen
- **Lebensversicherung**: COR Life Integration - möglicherweise separater Bounded Context

### Supporting Subdomains (notwendig, aber nicht differenzierend)
- **GDV-Schnittstelle**: Branchenstandard-Kommunikation
- **Telefonie (CTI)**: SIP-Integration für Call Center
- **Batch Processing**: Jobs, geplante Aufgaben

### Generic Subdomains (Commodity, könnten COTS sein)
- **Document Management (DMS)**: Imagemaster Integration
- **Document Output/Printing**: Print, Fax, PDF, Email Services
- **SAP Integration**: Finance/Controlling

**Hinweis**: Diese Hypothesen müssen mit WGV validiert und verfeinert werden.

---

## Aktivität 1: Event Storming Light

**Dauer**: ~45-60min  
**Ziel**: Gemeinsam Domain Events und Bounded Contexts identifizieren

### Vorbereitung

**Materialien**:
- Digitales Whiteboard (Miro, Mural) oder physische Sticky Notes
- **Farbcodierung**:
  - 🟧 **Orange**: Domain Events (Vergangenheitsform, z.B. "SchadenmeldungErfasst")
  - 🟦 **Blau**: Commands/Actions (Imperative, z.B. "SchadenMelden")
  - 🟨 **Gelb**: Aggregates/Entities (z.B. "Schadenakte", "Police")
  - 🟪 **Pink**: Externe Systeme (z.B. "GDV", "COR Life", "SAP")
  - 🟥 **Rot**: Hot Spots/Probleme (z.B. "Manuelle Dateneingabe", "Zeitverzögerung")

**Vorbereitung**: 
- Architektur-Diagramm `diagrams/architektur_schaubild_icis_gesamt.svg` als Referenz bereitstellen
- Whiteboard-Template mit Timeline vorbereiten

### Ablauf

#### Phase 1: Warm-up (5min)

**Erklärung**:
- "Wir werden gemeinsam die wichtigsten **Ereignisse** (Events) in Ihrem Versicherungssystem identifizieren"
- "Ein Event ist etwas, das **passiert ist** und für das Geschäft **relevant** ist"
- "Beispiele: 'KundeAngelegt', 'AdresseGeändert', 'SchadenGemeldet', 'PoliceAbgeschlossen'"

**Regel**: 
- Vergangenheitsform
- Geschäftsrelevant (nicht technisch: "ButtonGedrückt" ❌)
- Aus Nutzerperspektive

#### Phase 2: Chaotic Exploration - Event Discovery (20min)

**Frage an WGV-Teilnehmer**:
> "Was sind die wichtigsten **Ereignisse**, die in Ihrem Versicherungssystem passieren? Denken Sie an einen typischen Arbeitstag eines Sachbearbeiters."

**Facilitator-Prompts** (falls stockend):
- "Was passiert, wenn ein **neuer Kunde** zu Ihnen kommt?"
- "Was passiert, wenn ein Kunde **umzieht**?"
- "Was passiert, wenn ein **Schaden gemeldet** wird?"
- "Was passiert am **Jahresende** mit den Verträgen?"
- "Was passiert, wenn eine **Rechnung** nicht bezahlt wird?"

**Technik**: 
- Jeder Teilnehmer schreibt Events auf Sticky Notes
- Keine Diskussion, nur sammeln
- Alle Events auf Timeline (links → rechts, chronologisch)

**Erwartete Events** (Beispiele):
- KundeAngelegt
- AdresseGeändert
- AngebotsAnforderungEingegangen
- PoliceAbgeschlossen
- BeitragsZahlungErhalten
- SchadenGemeldet
- SchadenGutachtenErstellt
- SchadeLeistungAusgezahlt
- VertragGekündigt
- DokumentArchiviert
- GDV-MeldungVersendet

#### Phase 3: Temporal Ordering (10min)

**Aufgabe**:
- Events auf Timeline sortieren (von links nach rechts)
- Mehrere Flows sind ok (z.B. Neugeschäft parallel zu Schadenbearbeitung)

**Fragen**:
- "Welches Event passiert **zuerst**?"
- "Was muss passiert sein, **bevor** X passieren kann?"

#### Phase 4: Command & Actor Identification (10min)

**Frage**:
> "**Wer oder was löst** diese Events aus?"

**Hinzufügen**:
- 🟦 **Commands** (z.B. "Schaden melden", "Adresse ändern")
- 👤 **Actors** (z.B. "Sachbearbeiter", "Kunde", "System", "Externer Service")

**Beispiel**:
```
[Sachbearbeiter] → [Schaden melden] → [SchadenGemeldet]
[System/Batch] → [Jahresabschluss durchführen] → [JahresabschlussErstellt]
```

#### Phase 5: Bounded Context Emergence (15min)

**Aufgabe**: Events in **thematische Cluster** gruppieren

**Frage**:
> "Welche Events gehören **fachlich zusammen**? Welche könnten von **unterschiedlichen Teams** verantwortet werden?"

**Erwartete Cluster** (Bounded Context-Kandidaten):
- **Kundenverwaltung**: KundeAngelegt, AdresseGeändert, KundendatenAktualisiert
- **Neugeschäft/Angebote**: AngebotErstellt, AngebotAngenommen, PoliceAbgeschlossen
- **Vertragsführung**: BeitragsZahlungErhalten, VertragGeändert, VertragGekündigt
- **Schaden**: SchadenGemeldet, GutachtenErstellt, LeistungAusgezahlt
- **Dokumente**: DokumentErstellt, DokumentArchiviert, DokumentVersendet
- **GDV-Kommunikation**: GDV-MeldungEmpfangen, GDV-MeldungVersendet
- **Finance/Rechnungswesen**: RechnungErstellt, ZahlungVerbucht

**Diskussion**:
- "Könnten diese Cluster **unabhängig voneinander** entwickelt werden?"
- "Haben sie unterschiedliche **Datenmodelle**?"
- "Werden sie von unterschiedlichen **Fachabteilungen** genutzt?"

### Output

📊 **Visual Domain Map** mit:
- 5-8 identifizierten Bounded Contexts
- Typische Domain Events pro Kontext
- Commands und Actors
- Hot Spots (Problembereiche)

---

## Aktivität 2: Context Mapping Interview

**Dauer**: ~30-45min  
**Ziel**: System-Grenzen und Integrationsmuster verstehen

### Vorbereitung

**Materialien**:
- Context Map Template (vorbereitet auf Whiteboard)
- `diagrams/architektur_schaubild_icis_gesamt.svg` als Referenz

**Context Map Patterns** (Erklärung für Team):
- **Shared Kernel**: Gemeinsames Datenmodell (z.B. Kundenstammdaten)
- **Customer/Supplier**: Ein Team liefert für anderes Team
- **Conformist**: Downstream-Team muss sich anpassen (z.B. bei GDV-Standard)
- **Anti-Corruption Layer**: Übersetzungsschicht schützt eigenes Modell
- **Partnership**: Beidseitige Abhängigkeit, enge Zusammenarbeit
- **Separate Ways**: Keine Integration, komplett getrennt

### Leitfragen

#### Block 1: System-Grenzen identifizieren

**Frage 1**: "Welche fachlichen Bereiche haben **eigene Datenmodelle** in ICIS?"
- **Ziel**: Hinweis auf separate Bounded Contexts
- **Notieren**: Verschiedene Schemas? Verschiedene Tabellen-Präfixe?

**Frage 2**: "Gibt es Masken, die **nur von bestimmten Abteilungen** genutzt werden?"
- **Ziel**: Organisatorische Grenzen → Bounded Context-Grenzen
- **Beispiele**: Vertrieb vs. Leistung vs. Rechnungswesen vs. IT

**Frage 3**: "Welche Teile von ICIS könnten **unabhängig voneinander deployed** werden?"
- **Ziel**: Deployment-Grenzen identifizieren
- **Notieren**: Was muss immer zusammen deployt werden?

**Frage 4**: "Gibt es **separate Datenbanken oder Schemas** für verschiedene Bereiche?"
- **Ziel**: Physische Trennung = starkes Signal für Bounded Context

#### Block 2: Integration Patterns (Context Map)

**Frage 5**: "Wie kommuniziert ICIS mit **COR Life**?"
- Bidirektional oder nur in eine Richtung?
- Wer ist abhängig von wem?
- **Pattern-Kandidat**: Partnership? Customer/Supplier?

**Frage 6**: "Ist die **GDV-Schnittstelle** bidirektional oder nur outbound?"
- Müssen Sie sich an GDV-Standard halten?
- Können Sie das Format beeinflussen?
- **Pattern-Kandidat**: Conformist (GDV gibt Standard vor)

**Frage 7**: "Werden **SAP-Daten** in ICIS gespiegelt oder live abgefragt?"
- Gibt es einen lokalen Cache?
- Wie werden Konflikte gelöst?
- **Pattern-Kandidat**: Anti-Corruption Layer vs. Shared Kernel

**Frage 8**: "Welche **externen Systeme** sind kritisch? Was passiert, wenn sie ausfallen?"
- COR Life offline → Welche ICIS-Funktionen gehen noch?
- DMS offline → Können Sachbearbeiter weiterarbeiten?
- **Ziel**: Resilience-Anforderungen, Abhängigkeiten

#### Block 3: Ubiquitous Language Discovery

**Frage 9**: "Welche Begriffe bedeuten in **verschiedenen Abteilungen unterschiedliche Dinge**?"
- **Beispiel**: "Police" im Neugeschäft vs. Bestand vs. Schaden?
- **Ziel**: Hinweis auf separate Bounded Contexts mit eigenem Vokabular

**Frage 10**: "Gibt es **Synonyme** für denselben Fachbegriff?"
- Vertrag = Police = Versicherungsschein?
- Sind das wirklich Synonyme oder unterschiedliche Konzepte?
- **Ziel**: Begriffliche Klarheit, Basis für Ubiquitous Language

**Frage 11**: "Was ist der Unterschied zwischen 'Vertrag', 'Police', 'Versicherungsschein'?"
- **Ziel**: Klärung des fachlichen Vokabulars
- **Dokumentieren**: In Glossar festhalten

**Frage 12**: "Bedeutet 'Kunde' dasselbe für Neugeschäft und Bestandsführung?"
- **Beispiel**: Interessent vs. Versicherungsnehmer vs. Geschädigter
- **Ziel**: Kontext-spezifische Modelle identifizieren

#### Block 4: Datenfluss und Abhängigkeiten

**Frage 13**: "Wenn ich eine **Adresse ändere**, betrifft das nur Kundendaten oder auch Vertrag, Schaden, Rechnungswesen?"
- **Ziel**: Ist "Adresse" ein Shared Kernel oder kontextspezifisch?
- Welche Bounded Contexts müssen über Adressänderung informiert werden?

**Frage 14**: "Gibt es **unterschiedliche Arten von 'Schaden'** in verschiedenen Sparten (KFZ, Sach, Haftpflicht)?"
- **Ziel**: Ist Schaden ein übergreifender Bounded Context oder spartenspezifisch?

**Frage 15**: "Welche Masken greifen auf **dieselben Stored Procedures** zu?"
- **Ziel**: Clustering von Masken nach Geschäftslogik → Bounded Context-Grenzen
- **Technische Validierung**: Wird am Tag 2 tiefer analysiert

**Frage 16**: "Gibt es **regelmäßige Datenkonflikte** zwischen ICIS und externen Systemen (z.B. SAP)?"
- **Beispiele**: Kundenstammdaten synchron? Eventual Consistency?
- **Ziel**: Shared Data-Probleme, Need for Integration Patterns

### Output

📋 **Context Map** zeigt:
- Bounded Contexts als Boxen
- Integration Patterns als Linien (mit Labels: Shared Kernel, Conformist, etc.)
- Externe Systeme und deren Beziehungen
- Abhängigkeiten und Datenflüsse

📖 **Ubiquitous Language Glossar** (Start):
```markdown
## Bounded Context: Vertragsverwaltung

| Begriff | Definition | Synonyme | Abgrenzung zu |
|---------|------------|----------|---------------|
| Police  | Abgeschlossener Versicherungsvertrag mit Policennummer | Vertrag | Angebot (noch nicht abgeschlossen) |
| Kunde   | Versicherungsnehmer mit aktiver Police | VN | Interessent (hat nur Angebot) |
```

---

## Aktivität 3: Core Domain Chart

**Dauer**: ~15-20min  
**Ziel**: Domänen nach Business Value und Komplexität priorisieren

### Vorbereitung

**Materialien**:
- 2x2 Matrix auf Whiteboard oder Miro
- Liste der identifizierten Bounded Contexts aus Aktivität 1

**Achsen**:
- **Y-Achse**: Business Differentiation (Generic → Supporting → Core)
- **X-Achse**: Model Complexity (Simple → Complex)

```
Business
Value
  ↑
  │  Supporting │  CORE
  │  Simple     │  CORE Complex
  │─────────────┼─────────────
  │  Generic    │  Supporting
  │  Simple     │  Complex
  │
  └──────────────────────→ Complexity
```

### Ablauf

**Schritt 1: Erklärung der Kategorien (5min)**

**Core Domain**:
- Wettbewerbsvorteil
- Fachliche Differenzierung
- Hoher Business Value
- **Beispiele**: Innovative Schadensbearbeitung, Spezielle Tarifierungslogik

**Supporting Subdomain**:
- Notwendig, aber nicht differenzierend
- Unterstützt Core Domain
- **Beispiele**: GDV-Schnittstelle, Dokumentenarchivierung

**Generic Subdomain**:
- Commodity
- Könnte durch COTS ersetzt werden
- **Beispiele**: Email-Versand, Standard-Druckservices

**Schritt 2: Plotting (10min)**

**Frage an Teilnehmer**:
> "Wo würden Sie [Bounded Context X] auf dieser Matrix einordnen?"

**Für jeden Bounded Context**:
1. **Business Value**: Core / Supporting / Generic?
2. **Komplexität**: Simple (wenige Regeln) / Complex (viele Abhängigkeiten, Regeln)?

**Diskussion**:
- "Bietet dieser Bereich **Wettbewerbsvorteile**?"
- "Ist die Geschäftslogik **komplex** oder eher einfach?"
- "Könnten wir dafür eine **Standard-Software** kaufen?"

**Schritt 3: Strategische Implikationen (5min)**

**Quadranten-Strategien**:

| Quadrant | Strategie | Modernisierungsansatz |
|----------|-----------|----------------------|
| **Core + Complex** | Invest heavily | AI-driven Modernisierung, Custom Development, höchste Priorität |
| **Core + Simple** | Quick wins | APEX-Kandidaten, schnelle Migration |
| **Supporting + Complex** | Outsource or Simplify | Anti-Corruption Layer, möglicherweise später |
| **Supporting + Simple** | Low-Code/COTS | APEX, Oracle REST Data Services |
| **Generic + Complex** | Buy COTS | Evaluierung von Standardsoftware |
| **Generic + Simple** | Keep as-is or minimal | Niedrige Priorität |

### Output

📊 **Core Domain Chart** mit:
- Positionierung aller Bounded Contexts
- Strategische Empfehlungen pro Quadrant
- **MVP-Kandidaten**: Core + Simple für Quick Wins, Core + Complex für Business Impact

---

## Aktivität 4: Domain Storytelling

**Dauer**: ~20-30min  
**Ziel**: Deep-Dive in 1-2 kritische User Journeys

### Vorbereitung

**Materialien**:
- Domain Storytelling Notation (Icons: Actor, Work Object, Activity, Annotation)
- Whiteboard oder Miro-Template

**Notation**:
- 👤 **Actor**: Person oder System (z.B. Sachbearbeiter, Kunde, GDV-System)
- 📄 **Work Object**: Dokument oder Datenobjekt (z.B. Schadenakte, Police, Angebot)
- ➡️ **Activity**: Was macht der Actor mit dem Work Object? (nummeriert 1, 2, 3...)
- 💭 **Annotation**: Kommentare, Probleme, Fragen

### Ablauf

**Schritt 1: Szenario auswählen (5min)**

**Frage an WGV**:
> "Welche 2 Szenarien sind am wichtigsten zu verstehen?"

**Empfohlene Szenarien**:
- **Szenario A** (hohe Frequenz): z.B. "Adressänderung Kunde"
- **Szenario B** (hohe Komplexität): z.B. "Schadenmeldung mit Gutachten und Auszahlung"
- **Szenario C** (AI-Potenzial): z.B. "Angebotsanforderung Neugeschäft"

**Auswahl**: Pick 1-2 basierend auf Workshop-Zeit

**Schritt 2: Story erzählen (15-20min pro Szenario)**

**Fragen-Template**:

1. **"Wer startet den Prozess?"** 
   - 👤 Actor identifizieren
   
2. **"Was ist der Auslöser?"**
   - Event oder Anforderung

3. **"Was ist der erste Schritt?"**
   - ➡️ Activity 1: [Actor] [Verb] [Work Object]
   - Beispiel: 1️⃣ Sachbearbeiter öffnet Kundenmaske

4. **"Was passiert als nächstes?"**
   - 2️⃣ Sachbearbeiter sucht Kunde anhand Versicherungsnummer
   - 3️⃣ System lädt Kundendaten aus Datenbank
   - etc.

5. **"Welche Systeme/Masken werden dabei genutzt?"**
   - Oracle Forms-Maske XYZ
   - Stored Procedure ABC
   - Externes System (z.B. DMS für Dokumente)

6. **"Wo muss der Sachbearbeiter zwischen Masken wechseln?"**
   - 💭 Annotation: "Context-Grenze! Medienbruch!"
   - Hinweis auf Bounded Context-Grenzen

7. **"Wo werden Daten manuell kopiert?"**
   - 💭 Annotation: "Pain Point! Automatisierungspotenzial!"
   - AI-Feature-Kandidat

8. **"Welche Schritte dauern am längsten?"**
   - 💭 Annotation: "Performance-Problem" oder "Warten auf externes System"
   - Modernisierungspotenzial

9. **"Wer ist am Ende involviert?"**
   - Beispiel: Kunde erhält Brief → 📄 Bestätigungsschreiben

10. **"Was ist der erfolgreiche Abschluss?"**
    - End-Event (z.B. "AdresseGeändertBestätigt")

**Schritt 3: Annotieren (5min)**

**Markierungen hinzufügen**:
- 🔴 **Pain Points**: Manuelle Arbeit, Medienbrüche, lange Wartezeiten
- 🟢 **Automation Opportunities**: AI-Features, RPA-Kandidaten
- 🟡 **Bounded Context Boundaries**: Wo werden verschiedene Kontexte berührt?
- 🔵 **Integration Points**: Externe Systeme, Stored Procedures

### Output

📖 **2 visualisierte User Journeys** mit:
- Schritt-für-Schritt Ablauf
- Involvierte Actors und Systeme
- Pain Points und Verbesserungspotenziale
- Bounded Context-Übergänge
- **AI-Feature-Kandidaten** (für später am Tag 1)

---

## Empfohlener Zeitplan Tag 1 "Domäne erkennen" (~1.5h)

| Zeit | Aktivität | Dauer |
|------|-----------|-------|
| 09:00-09:45 | **Aktivität 1**: Event Storming Light | 45min |
| 09:45-10:30 | **Aktivität 2**: Context Mapping Interview | 45min |
| ☕ **Pause** | | 15min |
| 10:45-11:05 | **Aktivität 3**: Core Domain Chart | 20min |
| 11:05-11:35 | **Aktivität 4**: Domain Storytelling (1 Szenario) | 30min |

**Gesamtdauer**: ~1.5h + Pause = 1h 50min

**Optional**: Zweites Domain Storytelling Szenario kann in "Analyse von Masken" (~1.5-2h) integriert werden.

---

## Integration mit weiteren Tag 1 Aktivitäten

### Übergang zu "Analyse von Masken" (~1.5-2h)

**Input aus Domain Mapping**:
- Liste der identifizierten Bounded Contexts
- Core Domain Chart (Priorisierung)
- Ubiquitous Language Glossar

**Aktivität**:
- **Masken kategorisieren** nach Bounded Context
- **Stichproben-Analyse** pro Bounded Context:
  - 1-2 Masken aus "Core + Simple" → APEX-Kandidaten
  - 1-2 Masken aus "Core + Complex" → Custom Development
  - 1-2 Masken aus "Generic" → Keep as-is oder Standard-Software
- **Pattern-Identifikation**: CRUD vs. Workflow vs. Complex Business Logic

**Output**: 
- Klassifizierte Maskenliste mit ~900 Masken gruppiert nach Bounded Context
- 5-10 detailliert analysierte Beispielmasken

### Übergang zu "Anwendungskonzept (UI/UX) Skizze" (~1.5h)

**Input aus Domain Storytelling**:
- Identifizierte Pain Points
- Power User Workflows
- Medienbrüche und manuelle Schritte

**Aktivität**:
- **UI Pattern Definition** basierend auf Bounded Context:
  - Schaden → Workflow-orientiert, viele Statusübergänge
  - Kundenverwaltung → CRUD-lastig
  - Neugeschäft → Wizard/Stepper-Pattern
- **Hybrid UI-Konzept**: Wo macht Chatbot Sinn? Wo Forms?

### Übergang zu "Feature/Prioritäten Liste & AI Features" (~1h)

**Input aus Domain Mapping**:
- Annotierte User Journeys mit Automation Opportunities
- Pain Points aus Domain Storytelling

**Aktivität**:
- **AI-Feature-Identifikation**:
  - Manuelle Datenübertragung → AI Data Extraction
  - Regelbasierte Entscheidungen → AI Decision Support
  - Dokumentensuche → AI Semantic Search
- **Quick Wins**: Einfache Automatisierung mit hohem Business Value

### Übergang zu "Initial Scope Discussion" (~1h)

**Input aus Core Domain Chart**:
- Priorisierte Bounded Contexts
- Core + Simple für Quick Wins

**Aktivität**:
- **MVP-Scope festlegen**: 3-5 Masken aus priorisierten Bounded Contexts
- **Kriterien**:
  - Business Value (aus Core Domain Chart)
  - Technische Machbarkeit (wird Tag 2 validiert)
  - Nutzungshäufigkeit (aus Domain Storytelling)
  - Abhängigkeiten minimal

**Output**: 
- Scope-Vorschlag mit 3-5 MVP-Kandidaten-Masken
- Rationale: Warum diese Masken?

---

## Materialien & Templates

### Checkliste für Facilitator

**Vor dem Workshop**:
- [ ] Digitales Whiteboard (Miro/Mural) vorbereiten mit Templates:
  - [ ] Event Storming Timeline
  - [ ] Context Map Canvas
  - [ ] Core Domain Chart (2x2 Matrix)
  - [ ] Domain Storytelling Template
- [ ] Architektur-Diagramme bereitstellen:
  - [ ] `diagrams/architektur_schaubild_icis_gesamt.svg`
  - [ ] `context/architektur_schaubild_icis_gesamt.md` (Interpretation)
- [ ] Farbcodierung erklären (Orange, Blau, Gelb, Pink, Rot)
- [ ] Context Map Pattern Cheat Sheet ausdrucken/teilen
- [ ] Ubiquitous Language Glossar-Template vorbereiten

**Während des Workshops**:
- [ ] Timeboxing strikt einhalten (Pomodoro-Timer nutzen)
- [ ] Aktiv dokumentieren (Screenshots, Fotos von Whiteboard)
- [ ] Ubiquitous Language Glossar live befüllen
- [ ] Parking Lot für technische Detailfragen (→ Tag 2)

**Nach dem Workshop**:
- [ ] Digitalisierung aller Outputs (falls physisch)
- [ ] Context Map sauber dokumentieren
- [ ] Bounded Context-Liste mit Beschreibung erstellen
- [ ] Vorbereitung für Tag 2: Scope-Vorschlag formulieren

### Template: Ubiquitous Language Glossar

```markdown
# Ubiquitous Language - WGV ICIS Modernisierung

## Bounded Context: [Name]

| Begriff | Definition | Synonyme | Abgrenzung zu | Kontext |
|---------|------------|----------|---------------|---------|
| Police  | ... | Vertrag | Angebot | Vertragsverwaltung |
| Kunde   | ... | Versicherungsnehmer | Interessent | Kundenverwaltung |

## Bounded Context: [Name]

...
```

### Template: Context Map

```
┌─────────────────┐         ┌─────────────────┐
│   Neugeschäft   │────────▶│  Vertragsverwaltung │
│                 │   OHS   │                 │
└─────────────────┘         └─────────────────┘
                                   │
                                   │ SK
                                   ▼
                            ┌─────────────────┐
                            │  Kundenverwaltung │
                            └─────────────────┘

Legende:
OHS = Open Host Service
SK = Shared Kernel
CF = Conformist
ACL = Anti-Corruption Layer
```

### Referenz: DDD Pattern Cheat Sheet

**Context Map Patterns**:

| Pattern | Beschreibung | Wann nutzen? |
|---------|--------------|--------------|
| **Shared Kernel** | Gemeinsames Datenmodell, beide Teams committen | Enge Zusammenarbeit, kleine gemeinsame Kern |
| **Customer/Supplier** | Supplier liefert API, Customer nutzt | Klare Abhängigkeit, Supplier-Priorität |
| **Conformist** | Downstream muss sich anpassen | Externe Standards (GDV), keine Verhandlungsmacht |
| **Anti-Corruption Layer** | Übersetzungsschicht schützt eigenes Modell | Legacy-System, externes System mit schlechtem Modell |
| **Partnership** | Beide Teams koordinieren Releases | Gegenseitige Abhängigkeit, gemeinsames Ziel |
| **Separate Ways** | Keine Integration | Komplett unabhängige Bereiche |
| **Open Host Service** | Supplier bietet offene API für viele Consumer | Viele Downstream-Systeme |

---

## Verbindung zu bestehenden Dokumenten

### Facilitator-Referenzen

- **Architektur-Verständnis**: `context/architektur_schaubild_icis_gesamt.md`
- **Oracle Forms Details**: `context/icis_oracle_forms_architektur.md`
- **WGV Erwartungen**: `context/Modernisierungsworkshop-Draft.md`
- **Decision Frameworks**: `facilitation/decision_frameworks.md` 
  - Nutze **Cynefin Framework** zur Klassifikation von Domänen (Simple/Complicated/Complex)
  - Nutze **Weighted Decision Matrix** zur Bounded Context-Priorisierung

### Outputs für Tag 2

Die Domain Mapping Outputs fließen direkt in Tag 2 ein:

- **Bounded Context-Liste** → Basis für technische Validierung
- **Context Map** → Architektur-Design der Integration Layer
- **Core Domain Chart** → Scope-Priorisierung und MVP-Auswahl
- **Ubiquitous Language** → API-Design, Datenmodell-Diskussion
- **Domain Storytelling** → Stored Procedure-Analyse, welche Services werden gebraucht?

---

## Häufige Facilitator-Herausforderungen

### Challenge 1: "Wir haben keine Bounded Contexts, alles ist ein System"

**Symptom**: Teilnehmer sagen "Alles ist ICIS, es gibt keine Grenzen"

**Lösung**:
- Frage: "Welche **Tabellen** ändern sich, wenn Sie eine Adresse ändern vs. einen Schaden anlegen?"
- Frage: "Könnte **Team A** unabhängig von **Team B** deployen?"
- Zeige externe Systeme (COR Life, SAP) als klare Bounded Contexts → übertrage Konzept auf ICIS-intern

### Challenge 2: Zu viele Events, zu granular

**Symptom**: "ButtonGedrückt", "FeldAusgefüllt" - technische statt geschäftliche Events

**Lösung**:
- Regel wiederholen: "Nur **geschäftsrelevante** Events"
- Frage: "Würde der **Geschäftsführer** sich dafür interessieren?"
- Beispiel: ❌ "FormularGeöffnet" → ✅ "AngebotErstellt"

### Challenge 3: Diskussionen über technische Details

**Symptom**: "Aber die Stored Procedure XYZ macht doch..." - zu früh in Implementierung

**Lösung**:
- **Parking Lot**: "Gute Frage, notieren wir für Tag 2 (technische Validierung)"
- Fokus auf **fachliche** Prozesse halten
- Reminder: "Heute verstehen wir das WAS, morgen das WIE"

### Challenge 4: Keine Einigung auf Ubiquitous Language

**Symptom**: "Bei uns sagen Team A 'Police' und Team B 'Vertrag'"

**Lösung**:
- Das ist ein **Feature**, kein Bug! → Hinweis auf separate Bounded Contexts
- Dokumentieren: Beide Begriffe in separaten Kontexten
- Diskussion: "Meinen Sie dasselbe oder unterschiedliche Konzepte?"

### Challenge 5: Zu abstrakte Diskussionen

**Symptom**: "Wir brauchen eine flexible Architektur für die Zukunft..."

**Lösung**:
- **Konkrete Beispiele** fordern: "Nennen Sie mir einen konkreten Prozess"
- Domain Storytelling nutzen: "Zeigen Sie mir, wie das heute funktioniert"
- Post-its statt Whiteboard-Textwüsten → visualisieren!

---

## Erfolgskriterien

Am Ende von Tag 1 "Domäne erkennen" haben wir erfolgreich:

✅ **5-8 Bounded Contexts** identifiziert mit klaren Namen und Verantwortlichkeiten  
✅ **Context Map** zeigt Integration Patterns zwischen Kontexten und externen Systemen  
✅ **Core Domain Chart** priorisiert Domänen nach Business Value und Komplexität  
✅ **Ubiquitous Language Glossar** dokumentiert mindestens 10-15 Schlüsselbegriffe  
✅ **2-3 Domain Stories** visualisieren kritische User Journeys mit Pain Points  
✅ **Gemeinsames Verständnis** zwischen Nutzer, Architekten und codecentric-Team  
✅ **Scope-Basis** für Tag 2: Welche Bounded Contexts sind MVP-Kandidaten?  

**Nächster Schritt**: Tag 2 - Technische Validierung des Scopes und Architektur-Design

---

## Anpassungen & Varianten

### Variant A: Mehr Zeit für Event Storming (2h statt 1.5h)

Falls sehr viele Teilnehmer oder komplexe Domäne:
- Event Storming: 60min statt 45min
- Zweites Domain Storytelling Szenario hinzufügen

### Variant B: Remote Workshop

**Anpassungen**:
- Miro statt physischem Whiteboard (vorbereiten!)
- Breakout Rooms für paralleles Event Discovery
- Digitale Timer sichtbar teilen
- Mehr Pausen (Zoom-Fatigue)

### Variant C: Technische Teilnehmer dominieren

**Symptom**: Architekten/Developer reden über Implementierung statt Domäne

**Lösung**:
- Nutzer/Fachbereich **aktiv einbinden**: "Was sagt der Fachbereich dazu?"
- Rolle "Moderator" und "Scribe" trennen
- Parking Lot rigoros nutzen für technische Details

---

**Erstellt**: 2026-04-13  
**Autor**: Sócrates Ponce (codecentric)  
**Workshop**: WGV ICIS Modernisierung, 28-30 April 2026  
**Version**: 1.0
