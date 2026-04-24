# Tag 1: Analyse von Masken - Facilitator Guide

**Workshop**: WGV ICIS Modernisierung  
**Zielgruppe**: Nutzer, Architekten, (optional: PO/Projektleiter, Developer)  
**Dauer**: ~1.5-2h (90-120 Minuten)  
**Ansatz**: Methodology Transfer - Framework Teaching + Sample-Based Demonstration

---

## Zielsetzung

### Was wir ERREICHEN wollen

Am Ende der Maskenanalyse-Session haben wir:

✅ **Methodik vermittelt**: WGV versteht, wie man Migration Complexity bewertet (2×2 Matrix)  
✅ **Framework demonstriert**: 2×2 Matrix + RICE + Pattern-Matching auf 10-15 Beispielmasken  
✅ **Templates übergeben**: WGV kann Analyse selbständig fortsetzen  
✅ **MVP-Kandidaten identifiziert**: 3-5 Masken für Phase 1 ausgewählt  
✅ **Aktionsplan erstellt**: Klare Next Steps für WGV nach dem Workshop  
✅ **Masken-Patterns erkannt**: 5-8 typische Muster dokumentiert (Pattern-Katalog P1-P8)  

### Was wir NICHT erreichen müssen

❌ **Vollständige Analyse aller 900 Masken** - unrealistisch in 3 Tagen  
❌ **Detaillierte technische Spezifikation** jeder Maske - kommt später  
❌ **Finale Migrations-Roadmap** - benötigt mehr Zeit und Daten  

---

## Facilitator-Mindset: Methodology Consultants

### Unsere Rolle heute

**✅ WIR SIND:**
- **Methodology Coaches**: Wir zeigen WGV, wie man denkt
- **Framework-Experten**: Wir bringen bewährte Frameworks mit (2×2 Matrix, RICE, Pattern Catalog)
- **Facilitators**: Wir moderieren, WGV liefert Domain-Wissen
- **Template-Providers**: Wir liefern wiederverwendbare Tools

**❌ WIR SIND NICHT:**
- Analysten, die alle 900 Masken bewerten
- Experten für ICIS-Masken (WGV sind die Experten!)
- Verantwortlich für finale Entscheidungen (WGV entscheidet)

### Value Proposition

> "Wir bringen Ihnen bei, wie Sie die Migration assessment selbst durchführen können. Nach dem Workshop haben Sie die Werkzeuge und das Wissen, um die restlichen Masken eigenständig zu bewerten."

---

## Kontext & Vorbereitung

### Input aus vorherigen Aktivitäten

**Aus Domain Mapping (~1.5h vorher)**:
- 5-8 identifizierte Bounded Contexts (Vertrag, Schaden, Kunde, etc.)
- Context Map mit Integration Patterns
- Core Domain Chart (Business Value Priorisierung)

**Aus ICIS Deep Dive (optional, falls durchgeführt)**:
- Service-Inventar von Stored Procedures
- Architektur-Verständnis (ICIS-Klassik vs. ICIS+)

### Pre-Workshop Homework für WGV

**KRITISCH**: Bitte WGV, **VOR** dem Workshop vorzubereiten:

📋 **Masken-Inventar Spreadsheet** mit Basis-Informationen:

| Spalte | Beschreibung | Beispiel |
|--------|--------------|----------|
| **Mask ID** | Eindeutige Kennung | M001, VERTRAG_001 |
| **Mask Name** | Funktionale Bezeichnung | Vertragsabschluss Neugeschäft |
| **Bounded Context** | Fachlicher Bereich | Vertragsverwaltung |
| **Usage Frequency** | Nutzungshäufigkeit (grob) | Daily, Weekly, Monthly, Rarely |
| **User Count** | Anzahl Nutzer (Schätzung) | ~50 Sachbearbeiter |
| **Known Complexity** | Subjektive Einschätzung | Low, Medium, High |
| **Notes** | Besonderheiten | Integriert mit SAP, Legacy-Code |

**Warum diese Vorbereitung?**
- ⏱️ Spart Zeit am Workshop-Tag (kein Data Entry)
- 📊 WGV kennt ihre Masken besser als wir
- 🎯 Ermöglicht Fokus auf Methodology, nicht Datensammlung

**Email-Template für WGV** (vor Workshop):

```
Betreff: Vorbereitung Workshop Tag 1 - Masken-Inventar

Liebe WGV-Kollegen,

für die Maskenanalyse am Tag 1 wäre es hilfreich, wenn Sie vorab ein 
einfaches Inventar Ihrer ~900 Oracle Forms Masken vorbereiten könnten.

Benötigte Informationen pro Maske:
- Mask ID / Name
- Fachlicher Bereich (z.B. Vertrag, Schaden, Kunde)
- Nutzungshäufigkeit (täglich, wöchentlich, monatlich, selten)
- Anzahl Nutzer (grobe Schätzung)
- Komplexität (Ihre subjektive Einschätzung: Low/Medium/High)

Eine Excel-Liste reicht völlig aus. Wir nutzen diese als Basis für die 
gemeinsame Analyse im Workshop.

Vielen Dank!
codecentric Team
```

---

## Aktivitätsstruktur (90-120min)

### Vierteilige Struktur

| Phase | Dauer | Format | Fokus |
|-------|-------|--------|-------|
| **Part 1: Framework Introduction** | 20min | Präsentation + Diskussion | RICE, 2×2 Matrix, Pattern Catalog, Impact/Effort Matrix erklären |
| **Part 2: Funnel Approach Demonstration** | 60-70min | Kollaborativ | 900 → 50 → 15 → 5 Masken (live) mit Pattern-Matching |
| **Part 3: Templates & Playbook Übergabe** | 20min | Hands-on | WGV lernt Tools für Post-Workshop |
| **Part 4: MVP Selection & Action Plan** | 20-30min | Entscheidung | 3-5 Masken auswählen, Next Steps definieren |

**Gesamtdauer**: ~90-120 Minuten

---

## Part 1: Framework Introduction (~20min)

**Ziel**: WGV versteht die Bewertungsmethodik

### Ablauf

**Einführung (5min)**:

> "Wir haben ~900 Masken zu migrieren. Das ist eine große Herausforderung.
> 
> Die Frage ist nicht: 'Können wir alle in diesem Workshop analysieren?' – das ist unmöglich.
> 
> Die Frage ist: '**Wie entscheiden wir, welche Masken zuerst migriert werden?**'
> 
> Dafür zeigen wir Ihnen heute einen **Hybrid-Ansatz** mit bewährten Frameworks:
> 1. **2×2 Complexity Matrix** - Einfache Klassifikation (UI × Logic Complexity)
> 2. **RICE Scoring** - Für Priorisierung (Reach, Impact, Confidence, Effort)
> 3. **Pattern Catalog** - 8 Migrations-Patterns (P1-P8) mit konkreten Beispielen
> 4. **Impact/Effort Matrix** - Für Quick Wins Visualisierung
> 
> Wir werden diese Frameworks **gemeinsam auf 10-15 Beispielmasken anwenden**. Danach haben Sie die Werkzeuge, um die restlichen Masken selbst zu bewerten."

---

### Framework 1: 2×2 Complexity Matrix (~5min)

**Präsentation**:

> "Bevor wir entscheiden können, **WELCHE** Masken wir priorisieren, müssen wir verstehen, **WIE KOMPLEX** sie sind. Dafür nutzen wir eine einfache 2×2 Matrix."

**Zwei einfache Fragen** → Vier Quadranten:

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

**Zwei Klassifikations-Fragen**:

1. **UI Complexity**: "Wie viele Felder? Wie viele Tabs?"
   - **Simple**: <20 Felder, Single-Tab
   - **Complex**: >30 Felder, Multi-Tab

2. **Logic Complexity**: "Wie viele Stored Procedures? Externe Systeme?"
   - **Simple**: 0-1 SPs, CRUD
   - **Complex**: 3+ SPs, Berechnungen, Integrationen

**Quadranten → Migrations-Ansatz**:

| Quadrant | UI | Logic | Migrations-Ansatz | Beispiel |
|----------|----|----|-------------------|----------|
| **Q1** | Simple | Simple | React/Angular (AI-generiert) | Adressänderung |
| **Q2** | Complex | Simple | React/Angular (UI-Fokus) | Multi-Tab Stammdaten |
| **Q3** | Simple | Complex | Backend-First | Tarifberechnung |
| **Q4** | Complex | Complex | Full Custom (AI-assisted) | Vertragsabschluss |

**Key Insight**:
> "Die 2×2 Matrix hilft uns, den **Migrations-Aufwand** einzuschätzen. Q1-Masken brauchen 1-2 Wochen, Q4-Masken 4-8 Wochen. Das ist die Basis für RICE Scoring!"

**Diskussion**:
- "Macht das Sinn für Sie?"
- "Wo würden Sie **Adressänderung** einordnen?" (→ Q1: Simple UI, Simple Logic)
- "Wo würden Sie **Vertragsabschluss mit Tarifberechnung** einordnen?" (→ Q4: Complex UI, Complex Logic)

---

### Framework 2: RICE Scoring (~7min)

**Präsentation**:

> "Jetzt wissen wir, **WIE KOMPLEX** Masken sind (2×2 Matrix). Aber wie entscheiden wir, **WELCHE** wir zuerst migrieren? Dafür nutzen wir RICE Scoring."

**Formel**:
```
RICE Score = (Reach × Impact × Confidence) / Effort
```

**Komponenten** (auf Whiteboard visualisieren):

| Komponente | Bedeutung | Skala | Beispiel |
|------------|-----------|-------|----------|
| **Reach** | Wie viele Nutzer betroffen? | Nutzer pro Monat | 200 Sachbearbeiter |
| **Impact** | Business Value | 1-5 (minimal → massive) | 4 (High) |
| **Confidence** | Sicherheit der Schätzung | 0-100% | 70% (Medium) |
| **Effort** | Aufwand in Person-Wochen | **Basierend auf 2×2 Matrix!** | 3 Wochen |

**Wichtig**: Der **Effort** kommt aus der 2×2 Matrix-Klassifikation:
- Q1 (Simple/Simple): 1-2 Wochen
- Q2 (Complex UI/Simple): 2-3 Wochen
- Q3 (Simple/Complex Logic): 2-3 Wochen
- Q4 (Complex/Complex): 4-8 Wochen

**Beispiel-Rechnung** (live vorrechnen):

```
Maske: "Adressänderung Kunde"

2×2 Matrix: Q1 (Simple UI, Simple Logic)

Reach:     200 Nutzer/Monat
Impact:    2 (Low - einfache Datenänderung)
Confidence: 90% (gut dokumentiert, einfach)
Effort:    1 Woche (weil Q1!)

RICE Score = (200 × 2 × 0.9) / 1 = 360

→ Hoher Score = Hohe Priorität (Quick Win!)
```

**Diskussion**:
- "Macht das Sinn für Sie?"
- "Sehen Sie, wie die 2×2 Matrix den Effort informiert?"
- "Wer kann Reach und Impact am besten einschätzen?" (→ WGV!)

---

### Framework 3: Pattern Catalog (~5min)

**Präsentation**:

**8 konkrete Migrations-Patterns** (detailliert in `tag1_masken_pattern_katalog.md`):

| Pattern ID | Name | Quadrant | Migrations-Ansatz | Aufwand |
|------------|------|----------|-------------------|---------|
| **P1** | Simple CRUD | Q1 | React/Angular (AI-generiert) | 1-2w |
| **P2** | Search & Filter | Q1/Q2 | React/Angular + Data Grid | 1-2w |
| **P3** | Multi-Tab Form | Q2 | React/Angular (Tabs) | 2-3w |
| **P4** | Wizard Workflow | Q1-Q3 | React/Angular (Stepper) | 2-4w |
| **P5** | Calculation-Heavy | Q3 | Backend-First | 2-3w |
| **P6** | Complex Workflow | Q4 | Full Custom (AI-assisted) | 4-8w |
| **P7** | Report Generator | Q1 | React/Angular + Template Engine | 2-3w |
| **P8** | Conversational Candidate | Q4 | Chatbot + Form Hybrid (MCP) | 4-8w |

**Pattern-Matching**:
- 2×2 Matrix klassifiziert → Quadrant (Q1-Q4)
- Pattern-Matching innerhalb Quadrant → Konkreter Ansatz (P1-P8)
- Pattern → Automatisch: Technology Stack + Aufwand

**Beispiel**:
- Maske: "Adressänderung"
- UI: Simple (<20 Felder), Logic: Simple (1 SP)
- Quadrant: **Q1**
- Pattern: **P1** (Simple CRUD)
- Ansatz: React/Angular mit AI-Generierung
- Aufwand: 1-2 Wochen

**Key Insight**:
> "Pattern Catalog gibt uns **konkrete Beispiele** und **Technology Stack** für jeden Masken-Typ."

---

### Framework 4: Impact/Effort Matrix (~3min)

**Präsentation** (2×2 Matrix auf Whiteboard):

```
    High Impact
        │
    ┌───┼───┐
    │ ● │●●●│  ● = Strategic Projects (High Effort, High Impact)
    │STR│ QW│  QW = Quick Wins (Low Effort, High Impact) ← MVP!
────┼───┼───┼────
    │ ▲ │ ✖ │  ▲ = Fill-ins (Low Effort, Low Impact)
    │   │   │  ✖ = Avoid (High Effort, Low Impact)
    └───┴───┘
        │
    Low Impact
```

**Anwendung**:
- **Quick Wins** → Beste MVP-Kandidaten (schneller Business Value)
- **Strategic Projects** → Phase 2-3 (wichtig, aber aufwändig)
- **Avoid** → Nicht migrieren (evtl. deprecaten)

**Diskussion**:
- "Wo würden Sie **Adressänderung** einordnen?" (→ Quick Win)
- "Wo würden Sie **komplexe Schadensbearbeitung** einordnen?" (→ Strategic)

---

**Output Part 1**:
- ✅ WGV versteht 2×2 Complexity Matrix, RICE Scoring, Pattern Catalog, Impact/Effort Matrix
- ✅ Gemeinsames Vokabular etabliert (Quadranten Q1-Q4, Patterns P1-P8)
- ✅ Logischer Ablauf verinnerlicht: Complexity → Effort → Priorisierung

---

## Part 2: Funnel Approach Demonstration (~60-70min)

**Ziel**: 900 Masken → 10-15 Samples → 3-5 MVP-Kandidaten (live demonstrieren)

### Drei-Stufen-Trichter

```
┌─────────────────────────────────────┐
│ TIER 1: Quick Categorization        │  ~20-25min
│ 900 Masken → ~50-100 Kandidaten     │  (Filter-basiert)
└─────────────────────────────────────┘
              ↓
┌─────────────────────────────────────┐
│ TIER 2: Pattern-Based Sampling      │  ~25-30min
│ ~50-100 → 10-15 Representative      │  (Clustering)
└─────────────────────────────────────┘
              ↓
┌─────────────────────────────────────┐
│ TIER 3: RICE Scoring Deep Dive      │  ~15-20min
│ 10-15 → 3-5 MVP-Kandidaten          │  (Scoring + Entscheidung)
└─────────────────────────────────────┘
```

---

### Tier 1: Quick Categorization (~20-25min)

**Ziel**: Filter Chain anwenden, um auf ~50-100 Masken zu kommen

**Vorbereitung**:
- WGV-Spreadsheet mit 900 Masken auf Bildschirm teilen
- Excel/Google Sheets Filter aktivieren

**Filter Chain** (live durchführen):

**Filter 1: Usage Frequency**
- Frage: "Zeigen Sie uns nur Masken, die **mindestens wöchentlich** genutzt werden."
- Excel: Filter auf "Daily" + "Weekly"
- Ergebnis: z.B. 900 → ~300 Masken

**Filter 2: User Count**
- Frage: "Welche Masken werden von **mehr als 10 Nutzern** verwendet?"
- Excel: Filter auf User Count > 10
- Ergebnis: ~300 → ~150 Masken

**Filter 3: Business Criticality**
- Frage: "Welche Masken sind **geschäftskritisch**? Markieren Sie diese."
- WGV fügt Spalte "Critical" hinzu (Ja/Nein), filtert
- Ergebnis: ~150 → ~80-100 Masken

**Filter 4: Not Deprecated**
- Frage: "Gibt es Masken, die Sie **sowieso nicht migrieren** wollen?"
- WGV filtert "Deprecated = No"
- Ergebnis: ~100 → ~50-80 Masken

**Diskussion** (5min):
- "Wir haben jetzt ~50-80 Kandidaten. Das sind die relevanten Masken für die Modernisierung."
- "Diese Liste können Sie später erweitern oder verfeinern."

**Output Tier 1**:
- 📋 Shortlist von 50-80 Masken (Excel-File dokumentieren)
- ✅ WGV hat Filter-Methodik gesehen

---

### Tier 2: Pattern-Based Sampling (~25-30min)

**Ziel**: 5-8 Masken-Patterns identifizieren und 10-15 Representative auswählen

**Vorbereitung**:
- Miro/Whiteboard mit 2D-Matrix vorbereiten
- Achsen: **Bounded Context** (X) × **2×2 Matrix Complexity** (Y)

**Aktivität**: Masken clustern

**Schritt 1: Bounded Context Mapping** (10min)

Frage: "Ordnen wir die 50-80 Masken nach **Bounded Context**."

**Whiteboard-Template**:

```
Bounded Context (aus Domain Mapping):
┌─────────────┬─────────────┬─────────────┬─────────────┐
│ Vertrag     │ Schaden     │ Kunde       │ Finance     │
│             │             │             │             │
│ [Masken]    │ [Masken]    │ [Masken]    │ [Masken]    │
│             │             │             │             │
└─────────────┴─────────────┴─────────────┴─────────────┘
```

**Durchführung**:
- WGV nennt Masken, wir ordnen sie Bounded Contexts zu
- Post-its oder Miro-Karten nutzen
- Ergebnis: z.B. 20 in Vertrag, 15 in Schaden, 12 in Kunde, etc.

**Schritt 2: 2×2 Matrix Classification** (15min)

Frage: "Innerhalb jedes Bounded Context: Welche Masken sind **Clear**, welche **Complicated**, welche **Complex**?"

**2D-Matrix**:

```
                 Bounded Context
2×2 Matrix          │ Vertrag │ Schaden │ Kunde │ Finance │
─────────────────┼─────────┼─────────┼───────┼─────────┤
Clear (Simple)   │  ●●●    │  ●●     │  ●●●● │  ●      │
─────────────────┼─────────┼─────────┼───────┼─────────┤
Complicated      │  ●●     │  ●●●●   │  ●    │  ●●     │
─────────────────┼─────────┼─────────┼───────┼─────────┤
Complex          │  ●      │  ●      │       │         │
─────────────────┴─────────┴─────────┴───────┴─────────┘
```

**Leitfragen** (pro Maske):
- "Ist das eine **einfache CRUD-Maske**?" → Clear
- "Viele Business Rules, aber **gut verstanden**?" → Complicated
- "Viele **Abhängigkeiten, emergentes Verhalten**?" → Complex

**Schritt 3: Representative Sampling** (5min)

Frage: "Wählen wir **1-2 repräsentative Masken pro Zelle** aus."

**Auswahlkriterien**:
- Typisch für diese Kombination (Bounded Context × 2×2 Matrix)
- Gut bekannt (Knowledge Risk niedrig)
- Idealerweise: Mix aus Quick Win + Strategic

**Ergebnis**:
- 10-15 ausgewählte Masken (markiert auf Matrix)
- 5-8 identifizierte **Patterns** (z.B. "Clear CRUD in Vertrag", "Complex Workflow in Schaden")

**Output Tier 2**:
- 📊 2D-Matrix mit geclusterten Masken
- 🎯 10-15 repräsentative Masken für RICE Scoring
- 📋 5-8 dokumentierte Patterns

---

### Tier 3: RICE Scoring Deep Dive (~15-20min)

**Ziel**: Die 10-15 repräsentativen Masken mit RICE bewerten

**Vorbereitung**:
- RICE Scoring Template in Excel/Miro vorbereitet

**Template**:

| Mask ID | Mask Name | Reach (Users/mo) | Impact (1-5) | Confidence (%) | Effort (weeks) | RICE Score | Quadrant |
|---------|-----------|------------------|--------------|----------------|----------------|------------|----------|
| M001 | Vertragsabschluss | 50 | 5 | 60% | 4 | 37.5 | Strategic |
| M042 | Adressänderung | 200 | 2 | 90% | 1 | 360 | **Quick Win** |
| M089 | Schadenanlage | 30 | 4 | 50% | 3 | 20 | Strategic |
| ... | ... | ... | ... | ... | ... | ... | ... |

**Scoring-Prozess** (live, gemeinsam mit WGV):

**Pro Maske (~1-2min)**:

1. **Reach**: "Wie viele Nutzer pro Monat?"
   - WGV schätzt (basierend auf internem Wissen)
   - Notieren

2. **Impact**: "Business Value? 1-5?"
   - 1 = Minimal (Nice-to-have)
   - 3 = Medium (Wichtiger Workflow)
   - 5 = Massive (Mission-critical, Revenue)
   - WGV bewertet, wir notieren

3. **Effort**: "Person-Wochen Schätzung?"
   - Basierend auf:
     - 2×2 Matrix-Typ (Clear = 0.5-1, Complicated = 2-4, Complex = 4-8)
     - Anzahl Domains (Multi-Domain +50%)
     - Integration Complexity (External Systems +50%)
   - Gemeinsam schätzen

4. **Confidence**: "Wie sicher sind wir?"
   - Start: 80% (baseline)
   - **Reduktion** für:
     - Knowledge Risk: Ein Experte (−20%)
     - Undokumentiert (−10%)
     - External Dependencies (−10%)
   - **Erhöhung** für:
     - Gut dokumentiert (+10%)
     - Ähnlich zu ICIS+ Masken (+10%)
   - Gemeinsam justieren

5. **Berechnen**: `RICE = (Reach × Impact × Confidence) / Effort`

**Beispiel-Scoring (live vorführen)**:

```
Maske: "Adressänderung Kunde" (M042)

WGV-Input:
- Reach: "Wird täglich genutzt, ca. 200 Sachbearbeiter" → 200
- Impact: "Wichtig für Datenqualität, aber nicht revenue-critical" → 2
- Effort: "Einfache Maske, schätze 1 Woche" → 1
- Confidence: "Gut dokumentiert, ähnlich zu ICIS+ Maske" → 90%

Berechnung:
RICE = (200 × 2 × 0.9) / 1 = 360

Einordnung: Quick Win! (Low Effort, High Reach)
```

**Nach Scoring aller 10-15 Masken**:

**Sortieren nach RICE Score** (höchste zuerst):

```
Rang │ Mask Name              │ RICE Score │ Quadrant
─────┼────────────────────────┼────────────┼───────────
  1  │ Adressänderung         │ 360        │ Quick Win
  2  │ Partnersuche           │ 200        │ Quick Win
  3  │ Vertragsabschluss      │ 37.5       │ Strategic
  4  │ Schadenanlage KFZ      │ 30         │ Strategic
  5  │ Tarifberechnung        │ 20         │ Strategic
...
```

**Output Tier 3**:
- 📊 RICE-scored Table (10-15 Masken)
- 🎯 Top 3-5 Masken identifiziert

---

**Gesamtoutput Part 2**:
- ✅ Funnel-Methodik demonstriert (900 → 50 → 15 → 5)
- ✅ WGV hat Prozess miterlebt und kann ihn replizieren
- ✅ 10-15 Masken bewertet (Beispiele für Patterns)

---

## Part 3: Templates & Playbook Übergabe (~20min)

**Ziel**: WGV mit Tools ausstatten für Post-Workshop Arbeit

### Template 1: RICE Scoring Spreadsheet

**Übergabe** (Excel/Google Sheets Template):

**Enthält**:
- Vorbefüllte Spalten (Mask ID, Name, Reach, Impact, Confidence, Effort)
- **Automatische Berechnung** von RICE Score (Formel hinterlegt)
- **Conditional Formatting**:
  - Grün: RICE > 100 (Quick Wins)
  - Gelb: RICE 50-100 (Strategic)
  - Rot: RICE < 50 (Low Priority)
- **Pivot Table** vorbereitet (nach Bounded Context, 2×2 Matrix-Typ)

**Live-Demo** (5min):
- Zeigen, wie man eine neue Maske einträgt
- Zeigen, wie RICE automatisch berechnet wird
- Zeigen, wie man nach Quadrant filtert

**File**: `WGV_RICE_Scoring_Template.xlsx`

---

### Template 2: 2×2 Matrix Classification Matrix

**Übergabe** (Miro Board oder Excel):

**Miro-Template**:
- 2D-Matrix: Bounded Context × 2×2 Matrix-Typ
- Drag-and-Drop Masken-Karten
- Farbcodierung nach Priorität

**Alternative: Excel-Template**:
- Dropdown für "Bounded Context"
- Dropdown für "2×2 Matrix Type" (Clear, Complicated, Complex)
- Auto-Filter aktiviert

**File**: `WGV_2×2 Matrix_Classification.xlsx` oder Miro-Link

---

### Template 3: Impact/Effort Matrix (Visual)

**Übergabe** (Miro oder PowerPoint):

**Visualisierung** der 10-15 gescorten Masken:

```
    High Impact
        │
    ┌───┼───┐
    │ ● │●●●│  ● Vertragsabschluss (Strategic)
    │   │ ■■│  ■ Adressänderung (Quick Win)
────┼───┼───┼────
    │   │ ✖ │  
    └───┴───┘
        │
    Low Impact
```

**File**: `WGV_Impact_Effort_Matrix.pptx` oder Miro-Link

---

### Playbook: "How to Continue" (Step-by-Step)

**Übergabe** (Markdown/PDF-Dokument):

**Inhalt**:

```markdown
# WGV Maskenanalyse Playbook - Post-Workshop

## Ziel
Bewertung der verbleibenden ~885 Masken mit der gelernten Methodik.

## Schritt-für-Schritt Anleitung

### Phase 1: Datensammlung (1-2 Wochen)
1. Vervollständigen Sie das Masken-Inventar (falls noch nicht komplett)
2. Für jede Maske dokumentieren:
   - Bounded Context (aus Domain Mapping)
   - Usage Frequency
   - User Count
   - Known Complexity

### Phase 2: Quick Filtering (1 Tag)
1. Öffnen Sie `WGV_RICE_Scoring_Template.xlsx`
2. Wenden Sie Filter Chain an (siehe Workshop Tag 1):
   - Usage Frequency ≥ Weekly
   - User Count > 10
   - Business Critical = Yes
   - Deprecated = No
3. Ergebnis: ~50-100 Kandidaten-Masken

### Phase 3: Pattern-Based Clustering (2-3 Tage)
1. Öffnen Sie `WGV_2×2 Matrix_Classification.xlsx`
2. Ordnen Sie Masken nach Bounded Context
3. Klassifizieren Sie jede Maske (Clear/Complicated/Complex)
4. Identifizieren Sie 1-2 repräsentative Masken pro Pattern

### Phase 4: RICE Scoring (1 Woche)
1. Für jede repräsentative Maske:
   - Reach schätzen (Nutzer pro Monat)
   - Impact bewerten (1-5)
   - Confidence bewerten (%)
   - Effort schätzen (Person-Wochen)
2. Template berechnet automatisch RICE Score
3. Sortieren nach Score (höchste = höchste Priorität)

### Phase 5: Priorisierung & Roadmap (3-5 Tage)
1. Top 10-20 Masken identifizieren (höchste RICE Scores)
2. Nach Quadrant gruppieren:
   - Quick Wins → Phase 1 (MVP)
   - Strategic → Phase 2-3
   - Fill-ins → Phase 4+
   - Avoid → Nicht migrieren
3. Roadmap erstellen basierend auf Priorisierung

## Zeitplan (Gesamt: 3-4 Wochen)
- Woche 1-2: Datensammlung
- Woche 2: Filtering & Clustering
- Woche 3: RICE Scoring
- Woche 4: Priorisierung & Roadmap

## Ansprechpartner
codecentric steht für Review und Rückfragen zur Verfügung.
```

**File**: `WGV_Maskenanalyse_Playbook.md`

---

**Diskussion** (5min):

- "Ist der Playbook verständlich?"
- "Wer in Ihrem Team wird diese Analyse fortführen?"
- "Benötigen Sie Unterstützung von codecentric für Review?"

**Output Part 3**:
- ✅ 3 Templates übergeben (RICE, 2×2 Matrix, Impact/Effort)
- ✅ Playbook dokumentiert
- ✅ WGV weiß, wie sie nach Workshop fortfahren

---

## Part 4: MVP Selection & Action Plan (~20-30min)

**Ziel**: Finale Entscheidung für 3-5 MVP-Kandidaten-Masken

### Schritt 1: Quick Wins Review (10min)

**Frage an WGV**:
> "Basierend auf unserer Analyse: Welche **3-5 Masken** sollten wir für das MVP auswählen?"

**Kriterien wiederholen**:
- ✅ **Quick Wins** bevorzugen (Low Effort, High Impact)
- ✅ **Business Value** hoch (Impact ≥ 3)
- ✅ **Technisch machbar** (Confidence ≥ 60%)
- ✅ **Representative** für Patterns (verschiedene Bounded Contexts abdecken)

**Diskussion moderieren**:
- Zeigen: Top 5 RICE-scored Masken
- Diskutieren: "Macht diese Auswahl Sinn?"
- Justieren: Falls WGV andere Präferenzen hat (dokumentieren!)

**Beispiel-Auswahl**:

```
MVP-Kandidaten (3-5 Masken):

1. Adressänderung Kunde (RICE: 360, Quick Win)
   - Bounded Context: Kunde
   - 2×2 Matrix: Clear (Simple CRUD)
   - Ansatz: React/Angular (AI-generiert) Kandidat

2. Partnersuche (RICE: 200, Quick Win)
   - Bounded Context: Vertrag
   - 2×2 Matrix: Clear
   - Ansatz: React/Angular Simple UI

3. Vertragsabschluss Neugeschäft (RICE: 37.5, Strategic)
   - Bounded Context: Vertrag
   - 2×2 Matrix: Complicated
   - Ansatz: Custom Development, AI-assisted

4. Schadenanlage KFZ (RICE: 30, Strategic)
   - Bounded Context: Schaden
   - 2×2 Matrix: Complicated
   - Ansatz: Custom Development

5. (Optional) Hybride Chatbot-Maske (RICE: TBD, Experiment)
   - Bounded Context: TBD
   - 2×2 Matrix: Complex
   - Ansatz: Prototype für Conversational UI
```

**Rationale dokumentieren**:
- Warum diese Masken?
- Was repräsentieren sie?
- Welche Patterns decken sie ab?

---

### Schritt 2: Action Plan Erstellung (10min)

**Gemeinsam erstellen** (Whiteboard/Miro):

**Action Plan: Post-Workshop Tag 1**

| Action Item | Owner | Timeline | Deliverable |
|-------------|-------|----------|-------------|
| **1. Vervollständigen Masken-Inventar** | WGV Team | 1-2 Wochen | Excel mit allen 900 Masken |
| **2. RICE Scoring für restliche Masken** | WGV Team | 3-4 Wochen | Priorisierte Masken-Liste |
| **3. Review RICE Scoring** | codecentric (optional) | Nach 4 Wochen | Feedback & Empfehlungen |
| **4. Technische Validierung MVP-Masken** | Tag 2 Workshop | Morgen | Bestätigung: Technisch machbar? |
| **5. Stored Procedures Inventar** | WGV + codecentric | Tag 2 Workshop | Service-Katalog für MVP-Masken |
| **6. UI/UX Konzept für MVP-Masken** | codecentric + WGV | Heute Nachmittag | Skizzen, Wireframes |

---

### Schritt 3: Übergabe an Tag 2 (5min)

**Frage an Gruppe**:
> "Sind diese 3-5 Masken ein guter Scope für die technische Validierung morgen?"

**Erwartungen setzen**:
- Tag 2 wird diese Masken **technisch validieren**
- Stored Procedures Review: Welche Services werden gebraucht?
- Architektur-Design: Wie sieht die Integration Layer aus?

**Dokumentieren**:
- MVP-Scope Proposal (3-5 Masken)
- Rationale (Warum diese?)
- Open Questions für Tag 2

---

**Output Part 4**:
- ✅ 3-5 MVP-Kandidaten-Masken ausgewählt
- ✅ Rationale dokumentiert
- ✅ Action Plan erstellt
- ✅ Übergabe an Tag 2 vorbereitet

---

## Häufige Facilitator-Herausforderungen

### Challenge 1: "Wir haben keine Daten zu Nutzungshäufigkeit"

**Symptom**: WGV kann Reach nicht schätzen (keine Analytics)

**Lösung**:
- **Grobe Schätzung akzeptieren**: "Mehr als 10 Nutzer?" reicht
- **Relative Bewertung**: "Ist Maske A häufiger genutzt als Maske B?"
- **Kategorien statt Zahlen**: "Daily / Weekly / Monthly / Rarely"
- **Pragmatisch**: Confidence entsprechend reduzieren (50% statt 80%)

---

### Challenge 2: "Zu viele Masken in Quick Win Quadrant"

**Symptom**: Alle Masken werden als "Quick Win" eingeschätzt (unrealistisch)

**Lösung**:
- **Kritisch hinterfragen**: "Wirklich nur 1 Woche Aufwand?"
- **Hidden Complexity aufdecken**: "Welche Stored Procedures werden genutzt?"
- **Integration Complexity**: "Welche externen Systeme sind involviert?"
- **Effort neu kalibrieren**: "1 Woche = nur UI? Oder inkl. Backend-Integration?"

---

### Challenge 3: "WGV will alle 900 Masken in Phase 1 migrieren"

**Symptom**: Unrealistischer Scope, kein Priorisierungswille

**Lösung**:
- **Reality Check**: "Wie viele Developer haben Sie? Wie viel Zeit?"
- **MVP-Konzept erklären**: "Phase 1 = Lernen & Proof-of-Concept, nicht alles"
- **Risiko aufzeigen**: "Big Bang Migration = hohes Risiko, kein Feedback Loop"
- **Quick Wins betonen**: "Frühe Erfolge zeigen Wert, motivieren Team"

---

### Challenge 4: "2×2 Matrix-Klassifikation wird debattiert"

**Symptom**: Team uneinig, ob Maske "Complicated" oder "Complex" ist

**Lösung**:
- **Es gibt kein richtig/falsch**: 2×2 Matrix ist ein Werkzeug, keine Wissenschaft
- **Pragmatisch**: "Wir markieren als Complicated, passen aber Confidence an"
- **Dokumentieren**: "Unsicher → Confidence = 50%"
- **Später validieren**: "Tag 2 zeigt uns, ob Einschätzung stimmt"

---

### Challenge 5: "Effort-Schätzung sehr unsicher"

**Symptom**: "Keine Ahnung, wie lange das dauert"

**Lösung**:
- **T-Shirt Sizing** statt Wochen: "Small / Medium / Large / X-Large"
- **Relative Estimation**: "Wie viel schwieriger als Maske X?"
- **Confidence reflektiert Unsicherheit**: Unsicher = Confidence 30-50%
- **Validierung später**: "Wir schätzen jetzt, validieren technisch am Tag 2"

---

### Challenge 6: "WGV hat keine Zeit für Post-Workshop Playbook"

**Symptom**: "900 Masken analysieren? Wir haben keine Ressourcen!"

**Lösung**:
- **Schrittweise**: "Sie müssen nicht alle 900 sofort machen"
- **Fokus auf Candidates**: "Analysieren Sie nur die ~100 relevanten"
- **Iterativ**: "Machen Sie 20 Masken pro Monat, in 5 Monaten fertig"
- **Priorisierung hilft**: "Die wichtigsten 50 reichen für Roadmap-Planung"
- **codecentric Support anbieten**: "Wir können Review-Sessions machen"

---

## Erfolgskriterien

Am Ende der Maskenanalyse-Session haben wir erfolgreich:

✅ **Methodik vermittelt**: WGV kann RICE + 2×2 Matrix selbständig anwenden  
✅ **Framework demonstriert**: 10-15 Masken live bewertet  
✅ **Templates übergeben**: WGV hat Tools (Excel, Miro) für Post-Workshop  
✅ **MVP-Scope definiert**: 3-5 Kandidaten-Masken für Tag 2 ausgewählt  
✅ **Action Plan erstellt**: Klare Next Steps für WGV dokumentiert  
✅ **Patterns identifiziert**: 5-8 typische Masken-Typen erkannt  
✅ **Gemeinsames Verständnis**: WGV + codecentric aligned auf Approach  

**Nächster Schritt**: Tag 2 - Technische Validierung der MVP-Masken & Architektur-Design

---

## Integration mit weiteren Tag 1 Aktivitäten

### Input aus Domain Mapping

**Was wir nutzen**:
- Bounded Contexts → Für Clustering der Masken
- Core Domain Chart → Für Business Value-Bewertung (Impact)
- Context Map → Für Integration Complexity (Effort + Confidence)

**Wie wir es nutzen**:
- Masken werden nach Bounded Context gruppiert
- "Core Domain" Masken bekommen höheren Impact-Score
- Masken mit vielen Context-Übergängen bekommen höheren Effort

---

### Input für UI/UX Konzept (~1.5h später)

**Was wir übergeben**:
- 3-5 MVP-Masken → Basis für UI/UX Skizzen
- 2×2 Matrix-Classification → Informiert UI Pattern (CRUD vs. Workflow vs. Chatbot)
- Quick Wins → Fokus für User Journey Analyse

**Beispiel**:
- Adressänderung (Clear/Simple) → Einfaches Formular-Pattern
- Vertragsabschluss (Complicated) → Wizard/Stepper-Pattern
- Hybride Chatbot-Maske (Complex) → Conversational UI Experiment

---

### Input für AI Features Discussion (~1h später)

**Was wir übergeben**:
- Masken mit **hoher manueller Arbeit** → AI Automation Kandidaten
- Masken mit **komplexen Regeln** → AI Decision Support
- Masken mit **viel Datensuche** → AI Semantic Search

**Beispiel**:
- Partnersuche → AI-powered Semantic Search
- Schadenanlage → AI Data Extraction aus Dokumenten
- Vertragsabschluss → AI Pre-fill basierend auf historischen Daten

---

### Output für Tag 2

**Was Tag 2 nutzt**:
- **3-5 MVP-Masken** → Scope für technische Validierung
- **RICE-Scored Liste** → Priorisierung für Stored Procedure Review
- **2×2 Matrix-Classification** → Migrations-Ansatz (React/Angular vs. Custom vs. Prototype)
- **Effort-Schätzungen** → Basis für Roadmap-Planung

---

## Materialien & Templates

### Checkliste für Facilitator

**Vor dem Workshop**:
- [ ] WGV kontaktiert: Masken-Inventar Spreadsheet vorbereiten
- [ ] Excel-Templates vorbereiten:
  - [ ] `WGV_RICE_Scoring_Template.xlsx` (mit Formeln)
  - [ ] `WGV_2×2 Matrix_Classification.xlsx` (mit Dropdowns)
- [ ] Miro-Board vorbereiten:
  - [ ] 2D-Matrix (Bounded Context × 2×2 Matrix)
  - [ ] Impact/Effort Matrix (2×2)
  - [ ] Post-its für Masken
- [ ] Playbook-Dokument vorbereiten: `WGV_Maskenanalyse_Playbook.md`
- [ ] Beispiel-Rechnungen vorbereiten (RICE für 2-3 Masken)

**Während des Workshops**:
- [ ] Framework-Erklärung: RICE, 2×2 Matrix, Impact/Effort (~20min)
- [ ] Funnel Approach live demonstrieren (900 → 50 → 15 → 5)
- [ ] Mindestens 10 Masken mit RICE scoren (live, gemeinsam)
- [ ] Templates ausfüllen während Workshop (nicht nachher!)
- [ ] Fotografie/Screenshots von allen Whiteboards
- [ ] Action Plan gemeinsam erstellen und dokumentieren

**Nach dem Workshop**:
- [ ] Templates finalisieren und an WGV senden
- [ ] Playbook fertigstellen (ggf. anpassen basierend auf Feedback)
- [ ] MVP-Scope dokumentieren für Tag 2 Vorbereitung
- [ ] Identified Patterns dokumentieren (5-8 Masken-Typen)
- [ ] Follow-up Email an WGV: Templates + Playbook + Action Plan

---

### Template Files (Deliverables)

**File 1: `WGV_RICE_Scoring_Template.xlsx`**

Spalten:
- Mask ID
- Mask Name
- Bounded Context (Dropdown)
- 2×2 Matrix Type (Dropdown: Clear / Complicated / Complex)
- Reach (Nutzer/Monat)
- Impact (1-5, Dropdown)
- Confidence (%, Slider)
- Effort (Wochen)
- RICE Score (Formel: =(Reach × Impact × Confidence) / Effort)
- Quadrant (Formel: IF-Bedingung basierend auf Effort/Impact)

Conditional Formatting:
- Grün: RICE > 100
- Gelb: RICE 50-100
- Rot: RICE < 50

---

**File 2: `WGV_2×2 Matrix_Classification.xlsx`**

Spalten:
- Mask ID
- Mask Name
- Bounded Context
- 2×2 Matrix Type
- Characteristics (Text: Warum diese Klassifikation?)
- Recommended Approach (React/Angular / Custom / Prototype)

Pivot Table:
- Rows: Bounded Context
- Columns: 2×2 Matrix Type
- Values: Count of Masks

---

**File 3: `WGV_Impact_Effort_Matrix.pptx`**

Slide 1: 2×2 Matrix mit geplotteten Masken
- X-Achse: Effort (Low → High)
- Y-Achse: Impact (Low → High)
- Data Points: Top 10-15 Masken (aus RICE Scoring)
- Quadrant Labels: Quick Wins, Strategic, Fill-ins, Avoid

---

**File 4: `WGV_Maskenanalyse_Playbook.md`**

Inhalt (siehe Part 3 oben):
- Zielsetzung
- Schritt-für-Schritt Anleitung (5 Phasen)
- Zeitplan (3-4 Wochen)
- Ansprechpartner

---

## Referenzen & Verbindungen zu anderen Dokumenten

### Facilitator-Referenzen

- **Decision Frameworks**: `facilitation/decision_frameworks.md`
  - RICE Scoring (Detail-Erklärung)
  - 2×2 Matrix Framework (Hintergrund)
  - Impact/Effort Matrix (Visualisierung)
- **Domain Mapping**: `facilitation/tag1_domain_mapping_guide.md`
  - Bounded Contexts (Input für Clustering)
  - Core Domain Chart (Input für Impact-Bewertung)
- **ICIS Deep Dive**: `facilitation/tag1_icis_deep_dive_guide.md`
  - Service-Inventar (Input für Effort-Schätzung)
  - Stored Procedure Patterns (Complexity-Indikator)

### Outputs für Tag 2

- **MVP-Scope** → Input für "Technische Validierung"
- **RICE-Scores** → Priorisierung für Stored Procedure Review
- **2×2 Matrix-Classification** → Migrations-Ansatz (React/Angular vs. Custom)
- **Effort-Estimates** → Roadmap-Planung

---

## Anpassungen & Varianten

### Variant A: Mehr Zeit verfügbar (2.5h statt 1.5h)

**Änderungen**:
- Part 2 (Funnel): 90min statt 60min
  - Mehr Masken scoren (20 statt 10-15)
  - Tiefere Diskussion pro Maske
- Part 4 (Action Plan): 40min statt 20min
  - Detaillierte Roadmap-Planung
  - Post-Workshop Timeline feiner granuliert

---

### Variant B: Weniger Zeit verfügbar (1h statt 1.5h)

**Änderungen**:
- Part 1 (Framework): 15min statt 20min (schnellere Erklärung)
- Part 2 (Funnel): 40min statt 60min
  - Nur 5-8 Masken scoren (statt 10-15)
  - Tier 1 überspringen (WGV hat Pre-Filter gemacht)
- Part 3 (Templates): 10min statt 20min (nur Übergabe, keine Live-Demo)

**Trade-off**: Weniger Demonstration, mehr Vertrauen auf Post-Workshop Playbook

---

### Variant C: Remote Workshop

**Anpassungen**:
- **Miro statt physischem Whiteboard** (vorbereiten!)
- **Breakout Rooms** für paralleles Clustering (Bounded Contexts)
- **Digitale Timer** sichtbar teilen
- **Screen Sharing** für Excel-Templates (alle sehen mit)
- **Mehr Pausen** (Zoom-Fatigue nach 60min)

---

### Variant D: WGV hat keine Masken-Inventar-Vorbereitung

**Symptom**: WGV kommt ohne vorbereitetes Spreadsheet

**Notfall-Plan**:
- **Option 1**: Tier 1 überspringen, direkt zu Tier 2
  - WGV nennt "Top 20 wichtigste Masken" aus Gedächtnis
  - Diese 20 clustern und scoren
- **Option 2**: Workshop verkürzen auf 1h
  - Nur Framework erklären + 5 Beispiele
  - Rest als Homework für WGV
- **Option 3**: Teil verschieben auf Tag 2 Vormittag
  - WGV erstellt Liste über Nacht
  - Tag 2 Start mit Maskenanalyse (30min)

**Präventiv**: Email 1 Woche vorher mit Template senden!

---

## Kommunikations-Snippets

### Opening Statement

> "Willkommen zur Maskenanalyse! Wir haben ~900 Masken, und unser Ziel heute ist **nicht**, alle zu analysieren – das wäre unrealistisch.
>
> Stattdessen zeigen wir Ihnen die **Methodik**, wie wir so eine Migration bewerten. Wir analysieren **gemeinsam 10-15 repräsentative Masken**, und Sie lernen dabei das Framework kennen, das Sie nach dem Workshop auf die restlichen anwenden können.
>
> Am Ende haben Sie:
> - ✅ Ein wiederverwendbares Framework (RICE, 2×2 Matrix)
> - ✅ Templates für Ihre weitere Arbeit
> - ✅ Eine erste Auswahl von 3-5 MVP-Masken
> - ✅ Einen Aktionsplan für die nächsten Wochen
>
> Klingt das gut? Dann legen wir los!"

---

### Transition zu Part 2 (Funnel)

> "Jetzt wird's praktisch. Wir haben Ihr Spreadsheet mit den Masken hier auf dem Bildschirm.
>
> Wir werden jetzt **gemeinsam filtern**: Von 900 Masken runter auf ~50, dann auf ~15, und dann bewerten wir die 15 im Detail.
>
> Das Ziel: Sie sehen den Prozess live, und können ihn später replizieren."

---

### Transition zu Part 3 (Templates)

> "Super, wir haben jetzt 15 Masken bewertet und 5 für das MVP ausgewählt.
>
> Jetzt übergeben wir Ihnen die **Werkzeuge**, damit Sie nach dem Workshop weitermachen können. Drei Templates:
> 1. RICE Scoring Excel-Sheet
> 2. 2×2 Matrix Classification Matrix
> 3. Impact/Effort Visualisierung
>
> Plus ein **Playbook**: Step-by-Step, wie Sie die restlichen 885 Masken bewerten."

---

### Closing Statement

> "Perfekt! Wir haben heute:
> - ✅ Die Methodik gelernt (RICE, 2×2 Matrix)
> - ✅ 15 Masken gemeinsam bewertet
> - ✅ 5 MVP-Kandidaten ausgewählt
> - ✅ Templates und Playbook übergeben
>
> **Nächste Schritte**:
> - Heute Nachmittag: UI/UX Konzept für diese 5 Masken
> - Morgen (Tag 2): Technische Validierung – sind diese 5 technisch machbar?
> - Nach dem Workshop: Sie bewerten die restlichen Masken selbst
>
> Fragen? Dann machen wir weiter mit dem UI/UX-Teil!"

---

**Erstellt**: 2026-04-14  
**Autor**: Sócrates Ponce (codecentric)  
**Workshop**: WGV ICIS Modernisierung, 28-30 April 2026  
**Version**: 1.0
