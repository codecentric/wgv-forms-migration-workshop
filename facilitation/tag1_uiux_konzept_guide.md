# Tag 1: Anwendungskonzept (UI/UX) Skizze - Facilitator Guide

**Workshop**: WGV ICIS Modernisierung  
**Zielgruppe**: Nutzer, Architekten, (optional: PO/Projektleiter, Developer)  
**Dauer**: ~90 Minuten  
**Ansatz**: Framework-basierte UI/UX Exploration + User Research Empfehlung

---

## Zielsetzung

Am Ende der UI/UX-Session haben wir:

✅ **Hybrid UI-Konzept verstanden**: Wann Chatbot, wann Forms, wann beides?  
✅ **Persona-Hypothesen dokumentiert**: Power User vs. Casual User (Annahmen!)  
✅ **Trade-Off Sliders definiert**: UI-Prioritäten für verschiedene Nutzertypen  
✅ **UI-Pattern-Map erstellt**: Welches Pattern für welche MVP-Maske?  
✅ **Keep/Change/Evolve-Liste**: Was von Oracle Forms behalten, ändern, weiterentwickeln?  
✅ **2-3 Low-Fidelity Sketches**: Konzept-Wireframes für MVP-Masken  
✅ **User Research Plan**: Empfehlung für Nutzerinterviews (KRITISCH!)  

---

## Facilitator-Mindset: Framework Providers, Not Designers

### Unsere Rolle

**✅ WIR SIND:**
- **Framework-Vermittler**: Wir zeigen WGV, wie man über UI/UX denkt
- **UX-Prinzipien-Coaches**: Wir lehren durch Beispiele (nicht durch Vorlesung)
- **Moderatoren**: WGV entscheidet, wir facilitieren
- **Realitäts-Check**: "Das sind Hypothesen – wir brauchen Nutzertests!"

**❌ WIR SIND NICHT:**
- Pixel-perfekte Designer (das kommt später)
- Oracle Forms Experten (WGV kennt ihr System besser)
- Finale Entscheider (WGV owned das Produkt)
- Hellseher (wir raten ohne Nutzerdaten)

### Value Proposition

> "Wir geben Ihnen heute ein **Framework zum Denken über UI/UX**. Die finalen Antworten kommen aber von **Ihren Nutzern**, nicht von uns."

---

## Kontext & Vorbereitung

### Input aus vorherigen Aktivitäten

**Aus Domain Mapping (~3-4h vorher)**:
- Domain Storytelling → Pain Points identifiziert (manuelle Prozesse, Medienbrüche)
- User Journeys → Wo sind Ineffizienzen?
- Automation Opportunities → Wo kann UI/UX verbessern?

**Aus Maskenanalyse (~1h vorher)**:
- 3-5 MVP-Kandidaten-Masken ausgewählt
- Cynefin-Klassifikation (Clear/Complicated/Complex)
- Patterns erkannt (CRUD vs. Workflow vs. Multi-Entity)

**Aus Feature/AI Discussion (~30min vorher)**:
- AI-Features identifiziert (Chatbot, Auto-fill, Semantic Search)
- Hybrid UI-Konzept diskutiert (Conversational + Forms)

**WICHTIG**: Diese Session baut auf allen vorherigen auf!

---

## Aktivitätsstruktur (90min)

### Fünfteilige Struktur

| Phase | Dauer | Format | Fokus |
|-------|-------|--------|-------|
| **Part 1: UI/UX Challenge & Framework Intro** | 15min | Präsentation + Diskussion | Hybrid UI-Spektrum, UX-Prinzipien Teaser |
| **Part 2: UX Principles by Example** | 20min | Konkrete Beispiel-Analyse | Eine Maske redesignen, Prinzipien zeigen |
| **Part 3: Personas & Trade-Off Sliders** | 25min | Kollaborativ | Power vs. Casual User, Prioritäten setzen |
| **Part 4: UI Pattern Exploration** | 15min | Pattern-Mapping | Welches Pattern für welche Maske? |
| **Part 5: Oracle Forms Migration Strategy** | 15min | Keep/Change/Evolve | Was behalten, ändern, entwickeln? |
| **Part 6: Low-Fidelity Sketching** | 15min | Quick Wireframes | 2-3 Konzept-Skizzen (Papier/Miro) |

**Abschluss**: User Research Empfehlung (throughout, besonders am Ende)

---

## Part 1: UI/UX Challenge & Framework Intro (~15min)

### Opening Statement

> "Wir modernisieren 900 Oracle Forms Masken. Die große Frage heute: **Wie soll die neue Oberfläche aussehen und funktionieren?**
> 
> **Wichtig**: Wir haben **begrenzte Daten** über Ihre Nutzer. Deshalb ist unser Ziel heute:
> - ✅ Ein **Framework** zum Denken über UI/UX
> - ✅ **Werkzeuge** für Entscheidungen (Personas, Sliders, Patterns)
> - ✅ **Konzept-Sketches** für 2-3 MVP-Masken
> - ✅ Eine **klare Empfehlung**: Nutzerinterviews durchführen!
> 
> Alles, was wir heute erarbeiten, sind **Hypothesen**. Nutzerinterviews validieren diese."

---

### The Central Challenge (Visualisieren auf Whiteboard)

```
Oracle Forms (Heute)          Modern UI (Ziel)
─────────────────────        ─────────────────────
• 20+ Jahre alt              • Modern, wartbar
• Keyboard-first             • Keyboard + Mouse
• Power Users trained        • Power + Casual Users
• Dense, kompakt             • Lesbar, spacious
• Keine AI                   • AI-augmentiert
• Desktop only               • Desktop/Laptop ✓

Frage: Was behalten? Was ändern?
```

**Kontext-Klarstellung**:
- ✅ Desktop/Laptop only (keine Mobile-App)
- ✅ Back-Office Nutzer (keine Kunden)
- ✅ Barrierefreiheit: Awareness, aber niedrige Priorität (per WGV)

---

### Framework Teaser: Das Hybrid UI-Spektrum

**Konzept**: Nicht "Chatbot ODER Forms", sondern **Spektrum**

```
Chatbot ←─────●─────────────→ Forms
         (Kontext-abhängig)
```

**Frage an WGV**:
> "Für welche Masken würden Sie einen **Chatbot** bevorzugen? Für welche **klassische Formulare**?"

**Diskussion** (3min):
- Adressänderung: Chatbot? (Casual User, einfach)
- Vertragsabschluss: Forms? (Power User, viele Felder)
- Partnersuche: Hybrid? (Search + Conversational Refinement)

**Output**: Erste Intuition, keine finale Entscheidung

---

## Part 2: UX Principles by Example (~20min)

**Ziel**: UX-Prinzipien durch **ein konkretes Beispiel** lehren (nicht durch Theorie-Vorlesung)

### Methodik: "Teach Through Redesign"

**Statement**:
> "Es gibt viele UX-Gesetze und Designprinzipien – Hick's Law, Fitts' Law, Miller's Law, Gestaltgesetze...
> 
> Statt alle durchzugehen, nehmen wir **eine Maske aus Ihren Videos** und zeigen, wie diese Prinzipien **zusammenwirken**."

---

### Beispiel: "Adressänderung" Maske (oder andere aus Videos)

#### Schritt 1: Oracle Forms Version zeigen (5min)

**WGV präsentiert** (oder Sie zeigen Video-Screenshot):

```
Aktuelle Oracle Forms Maske (Adressänderung):
┌────────────────────────────────────────┐
│ F3=Search F5=Refresh F10=Save         │
├────────────────────────────────────────┤
│ Kunde_ID:    [_______]                 │
│ Name:        [_______]                 │
│ Vorname:     [_______]                 │
│ Strasse:     [_______]                 │
│ PLZ:         [_______]                 │
│ Ort:         [_______]                 │
│ ...40 weitere Felder...                │
└────────────────────────────────────────┘
```

**Fragen an WGV** (kollaborativ):
- "Wie finden Ihre Nutzer diese Maske?"
- "Was funktioniert **gut**?" (z.B. Tastaturkürzel, Tab-Reihenfolge)
- "Was ist **frustrierend**?" (z.B. zu viele Felder, kein Undo, kryptische Fehler)

**Notieren**: Pain Points auf Whiteboard

---

#### Schritt 2: Modern Redesign Concept (10min)

**Facilitator zeigt Redesign** (auf Whiteboard/Miro skizzieren):

```
Modern Version (Adressänderung):
┌────────────────────────────────────────┐
│ [Logo] Adressänderung [Search Ctrl+K] │
├────────────────────────────────────────┤
│                                        │
│ Customer: Max Mustermann (ID: 12345)   │ ← Kontext klar
│                                        │
│ ┌─ Aktuelle Adresse ─────────────┐    │
│ │ Hauptstraße 1                  │    │ ← Gruppierung
│ │ 12345 Berlin                   │    │   (Gemeinsame Region)
│ └────────────────────────────────┘    │
│                                        │
│ ┌─ Neue Adresse ─────────────────┐    │
│ │ Straße:  [Neue Str. 5________] │    │ ← Größere Inputs
│ │ PLZ:     [54321______________] │    │   (Fitts' Law)
│ │ Ort:     [München____________] │    │
│ │                                │    │
│ │ 💡 Vorschläge:                 │    │ ← AI Augmentation
│ │    • Neue Str. 5, 54321 München│    │   (nicht blockierend)
│ └────────────────────────────────┘    │
│                                        │
│          [Abbrechen] [Speichern]       │ ← Aktionen unten
│                    (Ctrl+S)            │   (Serial Position)
└────────────────────────────────────────┘
```

**Narration** (während des Zeichnens):

**"Was haben wir geändert?"**

| Prinzip | Anwendung | Warum? |
|---------|-----------|--------|
| **Miller's Law (7±2)** | 2 Sektionen (Aktuell, Neu) statt 50 flache Felder | Reduziert kognitive Last |
| **Gestalt: Gemeinsame Region** | Boxen gruppieren zusammengehörige Felder | Klare Informationshierarchie |
| **Fitts' Law** | Größere Input-Felder | Leichter zu klicken/fokussieren |
| **Hick's Law** | Nur relevante Felder zeigen (nicht alle 50) | Schnellere Entscheidungen |
| **Serial Position Effect** | Aktionen unten (Speichern, Abbrechen) | Erwartete, merkbare Position |
| **Jakob's Law** | Ctrl+S Shortcut beibehalten | Vertrautheit für Power User |

---

**Schritt 3: Key Message (5min)**

> "Wir haben diese Prinzipien nicht 'auswendig gelernt'. Wir denken einfach:
> - **Wie reduzieren wir Komplexität?**
> - **Wie machen wir es schneller?**
> - **Wie halten wir es vertraut?**
> 
> Diese UX-Gesetze **helfen dabei** – aber **Nutzertests** zeigen uns, ob es wirklich funktioniert.
> 
> **Referenz** für nach dem Workshop: `context/gestaltgesetze_ux_laws_cognitive_bias.md` – dort finden Sie alle 9 Gestaltgesetze, 14 UX Laws, 7 Kognitive Bias dokumentiert."

**Kein Deep-Dive in alle Gesetze** – nur Teaser, dass es ein Framework gibt!

---

## Part 3: Personas & Trade-Off Sliders (~25min)

**Ziel**: Nutzertypen hypothetisch definieren + UI-Prioritäten setzen

### Einführung (2min)

> "Wir haben **zwei Hypothesen** über Ihre Nutzer:
> - Power User (täglich, schnell, Experten)
> - Casual User (gelegentlich, Guidance brauchen)
> 
> **WICHTIG**: Das sind **Annahmen**! Wir empfehlen **Nutzerinterviews** nach dem Workshop, um diese zu validieren."

---

### Tool 1: Persona Definition (10min)

**Persona 1: Power User "Anna, die Schnelle"** (Hypothese!)

```
Charakteristik:
├─ Nutzt System 6-8h/Tag
├─ 50-200 Vorgänge pro Tag
├─ Experten-Wissen (20+ Jahre Erfahrung)
├─ Keyboard > Mouse
├─ Speed > Guidance
└─ "Ich will keine Hilfe, ich will schnell fertig sein!"

UI-Anforderungen (Hypothese):
├─ Tastaturkürzel (Tab, Enter, Ctrl+S, Ctrl+F)
├─ Kompakte Layouts (viele Infos auf Bildschirm)
├─ Batch-Operationen (Mehrfachauswahl)
├─ Wenig Bestätigungen ("Are you sure?" nervt)
└─ Favoriten/Templates (Muster wiederverwenden)
```

**Persona 2: Casual User "Ben, der Gelegentliche"** (Hypothese!)

```
Charakteristik:
├─ Nutzt System 1-2x pro Woche
├─ 1-5 Vorgänge pro Session
├─ Basis-Wissen (1-2 Jahre Erfahrung)
├─ Mouse > Keyboard
├─ Guidance > Speed
└─ "Ich brauche Hilfe, ich mache das selten!"

UI-Anforderungen (Hypothese):
├─ Tooltips, Hinweise, Beispiele
├─ Conversational UI (Chatbot, Wizards)
├─ Bestätigungen (Fehler vermeiden)
├─ Fortschrittsanzeigen (Wo bin ich?)
└─ Einfache Suche (Natural Language)
```

---

**Diskussion mit WGV** (8min):

**Leitfragen**:
1. "**Stimmen diese Personas?** Haben Sie wirklich diese beiden Nutzertypen?"
2. "Gibt es **mehr Typen**? (z.B. Manager, die nur Reports sehen?)"
3. "Was sind die **tatsächlichen Unterschiede** zwischen den Nutzertypen?"
4. "Wie viel **Prozent** Ihrer Nutzer sind Power vs. Casual?" (grobe Schätzung)

**WICHTIG**: Jede Antwort mit "Das ist unsere **Vermutung**" qualifizieren!

**Output**: Dokumentierte Persona-Hypothesen (mit Fragezeichen!)

---

### Tool 2: Trade-Off Sliders (13min)

**Aktivität**: Gemeinsam UI-Prioritäten positionieren

**Vorbereitung**: Miro/Whiteboard mit Slider-Templates vorbereitet

---

#### Power User Sliders

```
┌─────────────────────────────────────────────┐
│ Power User (Anna) - UI Trade-Offs          │
├─────────────────────────────────────────────┤
│                                             │
│ Speed ←─────────●───→ Guidance             │
│         (80% Speed)                         │
│ "Fast workflow, no hand-holding"           │
│                                             │
│ Keyboard ←───────●─→ Mouse                 │
│           (70% Keyboard)                    │
│ "Tab-Tab-Enter Workflow"                   │
│                                             │
│ Dense ←───────●─────→ Spacious             │
│         (60% Dense)                         │
│ "Information density > whitespace"         │
│                                             │
│ AI Auto ←──●────────→ Manual Control       │
│        (20% AI)                             │
│ "AI suggests, I decide quickly"            │
│                                             │
│ Minimal ←──────●────→ Confirmations        │
│         (70% Minimal)                       │
│ "Don't ask me 'Are you sure?' 10x"         │
└─────────────────────────────────────────────┘
```

---

#### Casual User Sliders

```
┌─────────────────────────────────────────────┐
│ Casual User (Ben) - UI Trade-Offs          │
├─────────────────────────────────────────────┤
│                                             │
│ Speed ←───●─────────→ Guidance             │
│       (30% Speed)                           │
│ "Show me how, I'm learning"                │
│                                             │
│ Keyboard ←──●───────→ Mouse                │
│          (20% Keyboard)                     │
│ "Point and click is easier"                │
│                                             │
│ Dense ←──●──────────→ Spacious             │
│       (20% Dense)                           │
│ "Breathing room, clear labels"             │
│                                             │
│ AI Auto ←────────●──→ Manual Control       │
│           (60% AI)                          │
│ "AI guides me through process"             │
│                                             │
│ Minimal ←──●────────→ Confirmations        │
│        (30% Minimal)                        │
│ "Confirm before I break something"         │
└─────────────────────────────────────────────┘
```

---

**Durchführung** (~10min):

**Für jeden Slider**:
1. **Erklären**: "Speed vs. Guidance – wo setzen wir den Slider für Power User?"
2. **WGV diskutiert**: "80% Speed – sie wollen schnell durch die Maske"
3. **Positionieren**: Gemeinsam Slider setzen
4. **Begründung notieren**: "Warum?" → "Power User machen das 100x/Tag, kennen jeden Schritt"

**Repeat** für alle 5 Slider × 2 Personas

**Output**: Dokumentierte Slider-Positionen (Foto/Screenshot)

---

### Adaptive UI Decision (5min)

**Frage an WGV**:
> "Basierend auf den Sliders: Brauchen wir **eine UI für alle** oder **zwei Modi** (Power/Guided)?"

**Optionen diskutieren**:

```
Option A: Single UI (Kompromiss)
├─ Pro: Einfacher zu bauen/warten
├─ Pro: Konsistenz (Jakob's Law)
└─ Con: Niemand 100% zufrieden

Option B: User-Togglable Modes ✓ (Empfohlen)
├─ Pro: Beste Erfahrung für jeden
├─ Pro: [Power Mode ↔ Guided Mode] Toggle
└─ Con: Mehr Aufwand (2 UI-Varianten)

Option C: Role-Based (Automatisch)
├─ Pro: System weiß, wer du bist
├─ Pro: Kein manuelles Umschalten
└─ Con: Was wenn Power User mal Guidance braucht?
```

**WGV entscheidet** → Dokumentieren + Rationale

---

## Part 4: UI Pattern Exploration (~15min)

**Ziel**: Pattern-Katalog zeigen, Masken zuordnen (Hypothesen!)

### Pattern-Katalog (5min präsentieren)

**4 UI-Patterns**:

#### Pattern 1: Single-Page Form
- **Best for**: 5-15 Felder, single entity, power users
- **Beispiel**: Adressänderung
- **Sketch**:
```
┌─────────────────────┐
│ [Feld 1_________]   │
│ [Feld 2_________]   │
│ [Feld 3_________]   │
│ [Save] [Cancel]     │
└─────────────────────┘
```

---

#### Pattern 2: Wizard/Stepper
- **Best for**: Multi-step workflow, decision points, casual users
- **Beispiel**: Vertragsabschluss
- **Sketch**:
```
Step 1/5: ● ○ ○ ○ ○
┌─────────────────────┐
│ [Select Customer]   │
│ [Options...]        │
│ [Back] [Next]       │
└─────────────────────┘
```

---

#### Pattern 3: Master-Detail
- **Best for**: Multi-entity relationships, complex data, power users
- **Beispiel**: Contract Management
- **Sketch**:
```
┌───────┬─────────────┐
│ List  │ Detail View │
│ Item1 │ [Data...]   │
│ Item2 │ [More...]   │
└───────┴─────────────┘
```

---

#### Pattern 4: Conversational/Chatbot
- **Best for**: Exploratory, casual users, simple actions
- **Beispiel**: Address change via chat
- **Sketch**:
```
┌─────────────────────┐
│ User: Change addr.. │
│ Bot:  Found X...    │
│ User: New is...     │
│ [Confirm] [Edit]    │
└─────────────────────┘
```

---

### Pattern Selection Activity (10min)

**Template** (Whiteboard/Miro):

| Mask | Cynefin | Primary User | Pattern Hypothesis | Rationale |
|------|---------|--------------|-------------------|-----------|
| Adressänderung | Clear | Casual | **Single-Page Form** OR **Chatbot** | Einfach, selten → Conversational? |
| Vertragsabschluss | Complicated | Power | **Wizard** | Multi-step, viele Entscheidungen |
| Schadenanlage | Complicated | Power | **Master-Detail** | Mehrere Entities (Claim, Customer, Contract) |
| Partnersuche | Clear | Power | **Search + Grid** | Hohe Frequenz, einfache Query |

**Diskussion moderieren**:
- "Welches Pattern macht Sinn für **Adressänderung**?"
- "Chatbot oder klassisches Form?"
- "Würde Anna (Power User) einen Chatbot nutzen? Oder lieber schnelles Form?"

**WICHTIG**: "Das sind **Hypothesen**! Wir validieren mit Prototypen + Nutzertests."

**Output**: Pattern-Map (dokumentiert)

---

## Part 5: Oracle Forms Migration Strategy (~15min)

**Ziel**: Keep/Change/Evolve Framework anwenden

### Framework: Was behalten? Was ändern? Was entwickeln?

**Template** (Whiteboard):

```
┌──────────────────────────────────────────────┐
│ KEEP (Familiarity = Adoption)               │
├──────────────────────────────────────────────┤
│ • Tastaturkürzel (Tab, Ctrl+S, F3, F5)      │
│ • Feldbezeichnungen (gleiche Terminologie)  │
│ • Workflow-Sequenz (Customer → Product → ..│
│ • Business Rules (Validierung)              │
│ • Tab-Reihenfolge (Muscle Memory!)          │
└──────────────────────────────────────────────┘
```

```
┌──────────────────────────────────────────────┐
│ CHANGE (Modernization = Better UX)          │
├──────────────────────────────────────────────┤
│ • Pop-up Hell → Inline Expansion/Modals     │
│ • Dichte Grids → Lesbare Tabellen           │
│ • Kryptische Fehler → Klare Erklärungen     │
│ • Kein Undo → Undo/Redo Stack               │
│ • Lost Context → Breadcrumbs, State Persist │
└──────────────────────────────────────────────┘
```

```
┌──────────────────────────────────────────────┐
│ EVOLVE (Hybrid: Familiar + Modern)          │
├──────────────────────────────────────────────┤
│ • Search: F3 (keep) + Natural Language (add)│
│ • Forms: Keyboard (keep) + AI Suggestions   │
│ • Navigation: Menus (keep) + Breadcrumbs    │
│ • Validation: Rules (keep) + Better Messages│
└──────────────────────────────────────────────┘
```

---

### Aktivität: Gemeinsam ausfüllen (12min)

**Leitfragen**:

**KEEP**:
- "Was würde Power User Anna **vermissen**, wenn wir es entfernen?"
- "Welche Tastaturkürzel sind **unverzichtbar**?"
- "Welche Workflow-Sequenzen sind **eingeprägt**?"

**CHANGE**:
- "Was frustriert **Casual User Ben** heute am meisten?"
- "Welche Oracle Forms Patterns sind **veraltet**?"
- "Was führt zu **häufigen Fehlern**?"

**EVOLVE**:
- "Wo können wir **beide Welten** kombinieren?" (Alt + Neu)
- "Welche Features können wir **AI-augmentieren**?" (z.B. Search)

**Output**: Ausgefüllte Keep/Change/Evolve-Liste (dokumentiert)

---

## Part 6: Low-Fidelity Concept Sketching (~15min)

**Ziel**: Schnelle visuelle Konzepte (NICHT pixel-perfect!)

### Approach: Paper Sketches ODER Miro Rough Wireframes

**Statement**:
> "Wir zeichnen jetzt **grobe Konzepte** für 2-3 MVP-Masken. Das sind **Napkin Sketches** – kein Photoshop, kein Figma. Stift + Papier oder Miro-Boxen."

---

### Sketch 1: "Adressänderung" (2 Varianten) (~5min)

**Variant A: Traditional Form**

```
┌─────────────────────────────────────┐
│ [Logo] Adressänderung    [Ctrl+K]  │
├─────────────────────────────────────┤
│ Kunde: Max Mustermann (12345)      │
│                                     │
│ ┌─ Aktuell ─┐  ┌─ Neu ─────────┐  │
│ │Hauptstr. 1│  │Straße [_____]│   │
│ │12345      │  │PLZ    [_____]│   │
│ │Berlin     │  │Ort    [_____]│   │
│ └───────────┘  └──────────────┘   │
│                                     │
│ [Abbrechen] [Speichern (Ctrl+S)]    │
└─────────────────────────────────────┘
```

**Variant B: Conversational**

```
┌─────────────────────────────────────┐
│ 🤖 Assistent                        │
├─────────────────────────────────────┤
│ User: Adresse ändern für 12345     │
│                                     │
│ Bot:  Gefunden: Max Mustermann      │
│       Aktuell: Hauptstr. 1, Berlin  │
│       Neue Adresse?                 │
│                                     │
│ User: Neue Str. 5, München          │
│                                     │
│ Bot:  Bestätigen:                   │
│       Neue Str. 5, 80331 München    │
│       [Bestätigen] [Bearbeiten]     │
└─────────────────────────────────────┘
```

**Frage an WGV**: "Welche Variante würden Anna und Ben bevorzugen?"

---

### Sketch 2-3: Weitere MVP-Masken (~10min)

**Basierend auf Zeit**:
- Vertragsabschluss (Wizard-Pattern)
- Schadenanlage (Master-Detail)
- Partnersuche (Search + Grid)

**Facilitator**: Nicht auf Perfektion zielen!
- Boxen + Labels reichen
- Fokus auf Layout, Flow, Key Interactions
- Offene Fragen identifizieren

**Output**: 2-3 Low-Fidelity Sketches (Foto/Screenshot)

---

## Abschluss: User Research Empfehlung (~5min, integriert)

**Throughout the session**, immer wieder betonen:

> "**Das sind Hypothesen!** Wir raten basierend auf Best Practices. **Nutzerinterviews** geben uns echte Daten."

---

### Finale Empfehlung (am Ende)

**Statement**:

> "**Was wir heute gemacht haben**: Hypothesen aufgestellt.
> 
> **Was wir DRINGEND empfehlen**: Diese Hypothesen validieren!
> 
> **Nächster Schritt**: **5-10 Nutzerinterviews** (je 45min)
> 
> **Fragen für Interviews**:
> 1. Welche Masken nutzen Sie täglich?
> 2. Was geht schnell? Was ist frustrierend?
> 3. Keyboard oder Mouse bevorzugt?
> 4. Würden Sie einen Chatbot nutzen?
> 5. Zeigen Sie uns Ihren typischen Workflow (Observation!)
> 
> **Warum wichtig?**
> - Wir haben heute **geraten** (basierend auf UX-Prinzipien)
> - Nutzerinterviews geben **Daten**
> - Bessere Entscheidungen = weniger Nacharbeit später
> 
> **Aufwand**: 5-10 Interviews à 45min = 1 Woche  
> **Return**: Vermeidung von Monaten falscher Entwicklung
> 
> **Wir können helfen**: Interview-Guide erstellen, erste Interviews moderieren (optional)"

---

## Gesamtoutput der Session

**Deliverables**:

1. ✅ **Persona-Hypothesen** (Power User, Casual User) + Fragezeichen
2. ✅ **Trade-Off Sliders** (dokumentierte Positionen für beide Personas)
3. ✅ **UI-Pattern-Map** (Welches Pattern für welche Maske – Hypothesen)
4. ✅ **Keep/Change/Evolve-Liste** (Oracle Forms Migration Strategy)
5. ✅ **2-3 Low-Fidelity Sketches** (Konzept-Wireframes)
6. ✅ **User Research Plan** (Interview-Guide Empfehlung)

**NICHT Deliverables**:
- ❌ High-Fidelity Mockups
- ❌ Complete Design System
- ❌ Finale UI-Entscheidungen (need user validation!)

---

## Häufige Facilitator-Herausforderungen

### Challenge 1: "Wir wollen pixel-perfekte Designs"

**Symptom**: WGV erwartet Figma-Mockups, nicht Sketches

**Lösung**:
- **Erwartungen managen**: "Heute = Konzepte, Pixel-perfekt = später (nach Nutzertests)"
- **Grund erklären**: "Wir investieren nicht in Design, bevor wir Nutzer gefragt haben"
- **Prozess zeigen**: "Sketch → Test → Refine → High-Fidelity"
- **Beispiel**: "Tesla baut nicht das Auto, bevor sie Kundenfeedback haben"

---

### Challenge 2: "Unsere Nutzer sind alle gleich"

**Symptom**: "Alle Power User" oder "Alle gleich erfahren"

**Lösung**:
- **Hinterfragen**: "Nutzen alle die Masken **gleich häufig**?"
- **Beispiele**: "Gibt es Aushilfen? Neue Mitarbeiter? Urlaubsvertretungen?"
- **Daten**: "Haben Sie Analytics? Wer nutzt was wie oft?"
- **Fallback**: "OK, dann designen wir für **einen** User-Typ – aber Interviews zeigen vielleicht mehr Varianz"

---

### Challenge 3: "Chatbot ist Hype, wir wollen Forms"

**Symptom**: Skepsis gegenüber Conversational UI

**Lösung**:
- **Nicht pushen**: "Völlig OK! Chatbot ist **eine Option**, nicht Pflicht"
- **Hybrid zeigen**: "Chatbot **nur** für einfache Fälle (Adressänderung)"
- **Forms für Rest**: "Komplexe Masken → klassische Forms"
- **A/B Test**: "Wir können **beide** prototypen, Nutzer entscheiden"

---

### Challenge 4: "Jakob's Law blockiert Innovation"

**Symptom**: "Wenn wir Oracle Forms kopieren, warum modernisieren?"

**Lösung**:
- **Balance erklären**: "Jakob's Law ≠ Kopieren. Es bedeutet: **Vertrautheit wahren**"
- **Evolution zeigen**: "Tastaturkürzel behalten (vertraut) + AI Suggestions hinzufügen (neu)"
- **Beispiel**: "Gmail sah wie Outlook aus (vertraut), aber war schneller (besser)"
- **Trade-off**: "Zu radikal = Ablehnung. Zu konservativ = kein Wert. Balance finden."

---

### Challenge 5: "Wir haben keine Zeit für Nutzerinterviews"

**Symptom**: "Zu viel Aufwand, wir wissen schon, was Nutzer wollen"

**Lösung**:
- **Risiko aufzeigen**: "Ohne Interviews: **50% Chance**, dass wir falsch liegen"
- **Kosten vergleichen**: 
  - Interviews: 1 Woche
  - Falsche UI bauen + neu machen: 3-6 Monate
- **Minimal Viable**: "Machen Sie **3 Interviews** (nicht 10), besser als 0"
- **Remote möglich**: "30min Video-Call reicht, kein Vor-Ort nötig"

---

### Challenge 6: "Personas fühlen sich zu generisch an"

**Symptom**: "Anna und Ben existieren nicht bei uns"

**Lösung**:
- **Namen ändern**: "Nennen wir sie wie Ihre echten Kollegen (mit Erlaubnis!)"
- **Konkretisieren**: "Beschreiben Sie **eine echte Person** – wie arbeitet sie?"
- **Daten nutzen**: "Haben Sie einen **typischen** Power User? Laden wir ihn ein!"
- **Iterativ**: "Personas = Hypothesen. Nach Interviews: Update mit echten Namen/Details"

---

## Integration mit weiteren Tag 1 Aktivitäten

### Input aus Domain Mapping

**Was wir nutzen**:
- Domain Storytelling Pain Points → UI/UX Verbesserungs-Opportunities
- Manuelle Prozessschritte → Candidates für UI Automation
- Medienbrüche → Wo UI nahtloser machen?

**Beispiel**: 
- Pain Point: "Sachbearbeiter kopiert Daten manuell aus PDF"
- UI/UX Lösung: Auto-fill Feature (OCR + AI)

---

### Input aus Maskenanalyse

**Was wir nutzen**:
- 3-5 MVP-Masken → Basis für UI Pattern Mapping
- Cynefin-Klassifikation → Informiert Pattern-Wahl
  - Clear → Single-Page Form oder Chatbot
  - Complicated → Wizard oder Master-Detail
  - Complex → Prototyping nötig

---

### Input aus Feature/AI Discussion

**Was wir nutzen**:
- AI-Features (Chatbot, Auto-fill) → In UI-Sketches integrieren
- Hybrid UI-Konzept → Conversational + Forms Balance

---

### Output für Initial Scope Discussion (~1h später)

**Was wir übergeben**:
- UI-Pattern-Map → Teil des MVP-Scopes
- Persona-Hypothesen → Informiert Scope-Priorisierung
- User Research Plan → Action Item für Post-Workshop

---

### Output für Tag 2

**Was Tag 2 nutzt**:
- UI-Patterns → Technische Validierung (Ist Chatbot machbar?)
- Persona-basierte Requirements → Architektur-Entscheidungen
- Keep/Change/Evolve-Liste → Migration-Strategie

---

## Materialien & Templates

### Checkliste für Facilitator

**Vor dem Workshop**:
- [ ] Whiteboard/Miro vorbereiten:
  - [ ] Hybrid UI-Spektrum Visualisierung
  - [ ] Persona-Templates (Power User, Casual User)
  - [ ] Trade-Off Sliders (5 Slider × 2 Personas)
  - [ ] Keep/Change/Evolve Boxes
  - [ ] Pattern-Katalog (4 Patterns mit Sketches)
- [ ] Beispiel-Redesign vorbereiten (Adressänderung oder andere Maske aus Videos)
- [ ] Referenz-Dokument bereithalten: `context/gestaltgesetze_ux_laws_cognitive_bias.md`
- [ ] User Research Interview-Guide vorbereiten (Template)

**Während des Workshops**:
- [ ] One Example Redesign durchführen (20min)
- [ ] Personas gemeinsam definieren (Hypothesen!)
- [ ] Trade-Off Sliders live setzen (kollaborativ)
- [ ] Pattern-Mapping für alle MVP-Masken
- [ ] Keep/Change/Evolve-Liste ausfüllen
- [ ] 2-3 Low-Fi Sketches erstellen (schnell, nicht perfekt!)
- [ ] Screenshots/Fotos von allen Whiteboards
- [ ] User Research Empfehlung mehrfach betonen

**Nach dem Workshop**:
- [ ] Persona-Hypothesen dokumentieren (Markdown/Confluence)
- [ ] Trade-Off Sliders dokumentieren (Screenshot + Rationale)
- [ ] UI-Pattern-Map finalisieren
- [ ] Keep/Change/Evolve-Liste aufbereiten
- [ ] Sketches digitalisieren (falls physisch)
- [ ] User Research Interview-Guide an WGV senden
- [ ] Input für Tag 2 vorbereiten

---

### Template: User Research Interview-Guide

**File**: `WGV_User_Research_Interview_Guide.md`

```markdown
# User Research Interview-Guide - WGV ICIS Modernisierung

## Zielsetzung
Validierung von Persona-Hypothesen und UI/UX-Anforderungen.

## Teilnehmer
- 5 Power Users (täglich im System)
- 5 Casual Users (wöchentlich/monatlich im System)

## Interview-Dauer
45 Minuten pro Person

## Struktur

### Teil 1: Warm-up (5min)
- Rolle/Abteilung?
- Wie lange arbeiten Sie mit ICIS?
- Wie oft nutzen Sie das System?

### Teil 2: Workflow Observation (15min)
"Zeigen Sie mir, wie Sie eine typische Aufgabe durchführen."
- Screen-Sharing oder Vor-Ort
- Notieren: Welche Masken? Welche Shortcuts? Wo Frustration?

### Teil 3: Pain Points (10min)
- Was nervt Sie am meisten?
- Was dauert zu lange?
- Wo machen Sie oft Fehler?

### Teil 4: Präferenzen (10min)
- Keyboard oder Mouse bevorzugt?
- Würden Sie einen Chatbot nutzen? Für was?
- Lieber schnell oder lieber geführt?

### Teil 5: Redesign-Feedback (5min)
- Zeigen: 2-3 UI-Sketches aus Workshop
- "Was gefällt? Was nicht?"
```

---

### Template: Persona Documentation

**File**: `WGV_Personas.md`

```markdown
# User Personas - WGV ICIS Modernisierung

⚠️ **ACHTUNG**: Diese Personas sind **HYPOTHESEN** basierend auf Workshop-Diskussionen. Sie müssen durch Nutzerinterviews validiert werden!

## Persona 1: Power User "Anna, die Schnelle"

**Status**: ❓ Hypothese (nicht validiert)

### Charakteristik
- Nutzungshäufigkeit: 6-8h/Tag
- Vorgänge pro Tag: 50-200
- Erfahrung: 20+ Jahre
- Input-Präferenz: Keyboard >> Mouse
- Priorität: Speed > Guidance

### UI-Anforderungen
- Tastaturkürzel (Tab, Ctrl+S, F3)
- Kompakte Layouts
- Batch-Operationen
- Minimale Bestätigungen
- Favoriten/Templates

### Validierungs-Status
- [ ] Interview durchgeführt
- [ ] Hypothesen bestätigt
- [ ] Hypothesen angepasst

---

## Persona 2: Casual User "Ben, der Gelegentliche"

...
```

---

## Referenzen & Verbindungen zu anderen Dokumenten

### Facilitator-Referenzen

- **UX/UI Expert Role**: `rollen/ux_ui_expert.md`
  - Theoretische Grundlagen (Gestaltgesetze, UX Laws, Cognitive Bias)
  - Hybrid UI-Konzeption
  - Human-in-the-Loop Prinzipien
- **UX Laws & Principles**: `context/gestaltgesetze_ux_laws_cognitive_bias.md`
  - 9 Gestaltgesetze (Ähnlichkeit, Nähe, Prägnanz, etc.)
  - 14 UX Laws (Hick's, Fitts', Jakob's, Miller's, etc.)
  - 7 Kognitive Bias (Anchoring, Default, Framing, etc.)
- **Domain Mapping**: `facilitation/tag1_domain_mapping_guide.md`
  - Domain Storytelling Pain Points → UI/UX Opportunities
- **Maskenanalyse**: `facilitation/tag1_maskenanalyse_guide.md`
  - 3-5 MVP-Masken → Basis für UI Pattern Mapping
  - Cynefin-Klassifikation → Pattern-Wahl
- **Feature/AI Discussion**: `facilitation/tag1_features_ai_guide.md`
  - AI-Features → Integration in UI-Sketches

---

## Anpassungen & Varianten

### Variant A: Mehr Zeit verfügbar (2h statt 1.5h)

**Änderungen**:
- Part 2 (Example): 30min statt 20min
  - Zwei Beispiele statt eins (Adressänderung + Vertragsabschluss)
- Part 6 (Sketching): 30min statt 15min
  - 4-5 Sketches statt 2-3
  - Mehr Detail pro Sketch

---

### Variant B: Weniger Zeit verfügbar (60min statt 90min)

**Änderungen**:
- Part 1 (Intro): 10min statt 15min (schnellere Erklärung)
- Part 2 (Example): 15min statt 20min (ein Beispiel, weniger Diskussion)
- Part 3 (Personas): 15min statt 25min (nur 3 Sliders statt 5)
- Part 4 (Patterns): 10min statt 15min (nur Top 3 Masken)
- Part 5 (Migration): 10min statt 15min (Keep/Change nur, kein Evolve)

**Trade-off**: Weniger Tiefe, mehr Fokus auf Key Decisions

---

### Variant C: Remote Workshop

**Anpassungen**:
- **Miro statt physischem Whiteboard** (vorbereiten!)
- **Breakout Rooms**: Paralleles Arbeiten an Sliders (Power vs. Casual)
- **Digitale Sketching**: Miro Shapes statt Papier
- **Screen Sharing**: Beispiel-Redesign als Slides vorbereiten
- **Mehr Pausen**: Zoom-Fatigue (alle 30min kurze Pause)

---

### Variant D: Videos nicht verfügbar

**Symptom**: Keine Oracle Forms Videos/Screenshots vorhanden

**Lösung**:
- **WGV Live-Demo**: Sachbearbeiter zeigt Maske live
- **Beschreibung**: WGV beschreibt verbal, wir skizzieren
- **Generic Example**: Wir zeigen generisches "Before/After" aus anderen Projekten
- **Fokus shift**: Mehr Zeit auf Personas/Sliders, weniger auf Example

---

## Kommunikations-Snippets

### Opening Statement

> "Willkommen zur UI/UX-Session! Wir haben 3-5 Masken für das MVP ausgewählt. Die Frage heute: **Wie sollen diese Masken aussehen und funktionieren?**
> 
> **WICHTIG**: Wir haben **begrenzte Daten** über Ihre Nutzer. Deshalb:
> - ✅ Framework zum Denken über UI/UX
> - ✅ Konzept-Sketches für MVP-Masken
> - ✅ **Empfehlung**: Nutzerinterviews durchführen!
> 
> Alles heute = **Hypothesen**. Interviews = **Validierung**."

---

### Transition zu Example Redesign (Part 2)

> "Jetzt wird's konkret. Wir nehmen **eine Maske aus Ihren Videos** und zeigen, wie UX-Prinzipien sie verbessern können.
> 
> Nicht alle Prinzipien im Detail – aber Sie sehen, **wie wir denken**."

---

### Transition zu Personas (Part 3)

> "Wir haben zwei Nutzer-Hypothesen: Power User Anna und Casual User Ben.
> 
> **Frage**: Stimmt das? Oder sind Ihre Nutzer anders?
> 
> **Wichtig**: Wir **raten** gerade. Nutzerinterviews geben uns **Fakten**."

---

### Transition zu Sketching (Part 6)

> "Jetzt zeichnen wir! Aber **keine Kunstwerke** – Napkin Sketches.
> 
> Wir wollen **Konzepte testen**, nicht perfekte Designs bauen. Das kommt nach Nutzertests."

---

### Closing Statement

> "Perfekt! Wir haben heute:
> - ✅ UX-Prinzipien durch Beispiel gelernt
> - ✅ Persona-Hypothesen aufgestellt
> - ✅ UI-Prioritäten mit Sliders gesetzt
> - ✅ Patterns für MVP-Masken gemapped
> - ✅ Keep/Change/Evolve-Strategie definiert
> - ✅ 2-3 Konzept-Sketches erstellt
> 
> **Nächste Schritte**:
> - **KRITISCH**: 5-10 Nutzerinterviews (1 Woche)
> - Prototypen bauen (basierend auf Sketches)
> - A/B Tests (Chatbot vs. Form, etc.)
> 
> **Morgen (Tag 2)**: Technische Validierung – sind diese UI-Patterns technisch machbar?
> 
> Fragen?"

---

**Erstellt**: 2026-04-15  
**Autor**: Sócrates Ponce (codecentric)  
**Workshop**: WGV ICIS Modernisierung, 28-30 April 2026  
**Version**: 1.0
