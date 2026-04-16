# Tag 1: Feature/Prioritäten Liste & AI Features - Facilitator Guide

**Workshop**: WGV ICIS Modernisierung  
**Zielgruppe**: Nutzer, Architekten, (optional: PO/Projektleiter, Developer)  
**Dauer**: ~45-60 Minuten  
**Ansatz**: AI Feature Discovery + Framework Reuse (RICE aus Maskenanalyse)

---

## Zielsetzung

Am Ende der Feature/AI-Session haben wir:

✅ **AI-Feature-Katalog erstellt**: 10-15 potenzielle AI-Capabilities identifiziert  
✅ **Features priorisiert**: RICE-Scoring angewendet (Framework-Reuse!)  
✅ **Top 3-5 Features ausgewählt**: Für MVP-Integration  
✅ **Features mit Masken verknüpft**: Welche Features passen zu welchen Masken?  
✅ **Innovation-Potenzial erkannt**: Wo kann AI echten Business Value schaffen?  
✅ **Realistische Erwartungen gesetzt**: Was ist machbar, was nicht?  

---

## Facilitator-Mindset: Innovation Enablers

### Unsere Rolle

**✅ WIR SIND:**
- **AI-Möglichkeiten-Aufzeiger**: "Das ist mit AI heute möglich"
- **Realitäts-Check**: "Das ist realistisch / Das ist Zukunftsmusik"
- **Facilitators**: Wir moderieren Feature-Brainstorming
- **Framework-Coaches**: Wir helfen, RICE auf Features anzuwenden

**❌ WIR SIND NICHT:**
- AI-Verkäufer, die alles mit AI lösen wollen
- Technische Spezifikations-Ersteller (kommt Tag 2)
- Entscheider über Features (WGV entscheidet)

### Value Proposition

> "Wir zeigen Ihnen, welche AI-Features heute realistisch sind und helfen Ihnen, die wertvollsten für Ihr MVP auszuwählen."

---

## Kontext & Vorbereitung

### Input aus vorherigen Aktivitäten

**Aus Domain Mapping (~3-4h vorher)**:
- Domain Storytelling → Pain Points identifiziert
- Manuelle Prozessschritte → Automatisierungs-Kandidaten
- Medienbrüche → AI-Integration-Möglichkeiten
- Annotation von User Journeys → "Automation Opportunities"

**Aus Maskenanalyse (~1h vorher)**:
- 3-5 MVP-Kandidaten-Masken ausgewählt
- RICE-Framework **bereits gelernt** und angewendet
- Quick Wins identifiziert
- Patterns erkannt (CRUD vs. Workflow vs. Complex)

**Aus UI/UX Skizze (falls bereits durchgeführt)**:
- Power User Workflows analysiert
- Pain Points in bestehenden User Journeys
- Hybrid UI-Konzept (Chatbot vs. Forms) diskutiert

**WICHTIG**: Diese Session **baut auf RICE-Framework auf** - Framework wird NICHT neu gelehrt!

---

## Aktivitätsstruktur (45-60min)

### Zweiteilige Struktur

| Phase | Dauer | Format | Fokus |
|-------|-------|--------|-------|
| **Part 1: AI Feature Discovery** | 35-40min | Brainstorming + Strukturierung | 10-15 AI-Features identifizieren |
| **Part 2: Feature Prioritization (RICE)** | 15-20min | Scoring + Entscheidung | Top 3-5 Features auswählen |

**Gesamtdauer**: ~45-60 Minuten

---

## Part 1: AI Feature Discovery (~35-40min)

**Ziel**: Katalog von 10-15 potenziellen AI-Features erstellen

### Einführung (5min)

**Opening Statement**:

> "Wir haben jetzt 3-5 Masken für das MVP ausgewählt. Die Frage ist: **Welche neuen Fähigkeiten** wollen wir dem modernisierten System geben?
> 
> Besonders interessant: **Wo kann AI helfen?**
> - Manuelle Prozesse automatisieren?
> - Daten intelligenter suchen?
> - Sachbearbeiter bei Entscheidungen unterstützen?
> 
> In den nächsten 40 Minuten sammeln wir **AI-Feature-Ideen**, und dann priorisieren wir sie mit dem **RICE-Framework**, das wir eben bei den Masken gelernt haben."

**Erwartungen setzen**:
- Wir sammeln Ideen, keine technischen Spezifikationen
- Alles ist erlaubt, wir filtern später
- Fokus auf Business Value, nicht auf Technologie

---

### Schritt 1: Pain Point Mapping (~10min)

**Ziel**: Verbindung zwischen Pain Points (aus Domain Mapping) und AI-Lösungen

**Aktivität**: Whiteboard Review

**Vorbereitung**:
- Domain Storytelling Ergebnisse auf Bildschirm zeigen
- Annotationen mit 🔴 Pain Points markiert

**Leitfragen**:

1. "Wo haben wir **manuelle Dateneingabe** identifiziert?"
   - **AI-Potenzial**: Auto-fill, Data Extraction, OCR

2. "Wo müssen Sachbearbeiter **zwischen Systemen wechseln**?"
   - **AI-Potenzial**: Intelligent Integration, Context Switching Automation

3. "Wo gibt es **repetitive Suchen** nach Informationen?"
   - **AI-Potenzial**: Semantic Search, Intelligent Recommendations

4. "Wo werden **komplexe Entscheidungen** getroffen?"
   - **AI-Potenzial**: Decision Support, Risk Scoring

5. "Wo entstehen **Wartezeiten** durch externe Systeme?"
   - **AI-Potenzial**: Predictive Pre-fetching, Smart Caching

**Dokumentation** (Miro/Whiteboard):

```
Pain Point → AI Feature Opportunity

Manual Data Entry           → Auto-fill, OCR, Data Extraction
→ "Schadensdaten manuell    → AI: Scanne Schadensbericht,
   aus PDF übertragen"         extrahiere Daten automatisch

Cross-System Search         → Semantic Search, Unified Search
→ "Kundeninfo in 3 Systemen → AI: "Zeige mir alles zu Kunde X"
   nachschlagen"               (ICIS, SAP, DMS)

Complex Decision            → Decision Support, Risk Scoring
→ "Tarif manuell auswählen  → AI: "Empfohlener Tarif basierend
   basierend auf Profil"       auf Kundenprofil"
```

**Output**:
- 5-8 Pain Point → AI Feature Mappings
- Erste Feature-Ideen dokumentiert

---

### Schritt 2: AI Capability Brainstorming (~15min)

**Ziel**: Strukturiertes Brainstorming für AI-Features

**Methode**: Kategorien-geführtes Brainstorming

**Vorbereitung**:
- Whiteboard mit 5 Kategorien vorbereiten

**5 AI-Feature-Kategorien**:

```
┌─────────────────────────────────────────────────────────┐
│ 1. AUTOMATION (Manuelle Arbeit eliminieren)            │
│ 2. AUGMENTATION (Sachbearbeiter unterstützen)          │
│ 3. INTELLIGENCE (Smarte Entscheidungen)                │
│ 4. INTERACTION (Neue UI-Patterns)                      │
│ 5. INTEGRATION (Systeme verbinden)                     │
└─────────────────────────────────────────────────────────┘
```

**Durchführung** (~3min pro Kategorie):

---

#### Kategorie 1: AUTOMATION

**Frage**: "Welche **manuellen Tätigkeiten** könnten vollständig automatisiert werden?"

**Beispiele** (Insurance-Domain-spezifisch):

| Feature | Beschreibung | Business Value |
|---------|--------------|----------------|
| **Auto-fill aus Dokumenten** | OCR + AI extrahiert Daten aus gescannten Verträgen/Schäden | Zeitersparnis 70% |
| **Automatische Kategorisierung** | AI klassifiziert eingehende Dokumente (Schaden, Antrag, etc.) | Routing-Fehler ↓ |
| **Batch-Verarbeitung** | AI verarbeitet einfache Anträge ohne menschliche Prüfung | Durchsatz ↑ |
| **Auto-Vervollständigung** | AI füllt Formular basierend auf Kundenprofil vor | User Friction ↓ |

**WGV-Input sammeln**:
- "Welche repetitiven Aufgaben nerven Ihre Sachbearbeiter am meisten?"
- Post-its / Miro-Karten erstellen

---

#### Kategorie 2: AUGMENTATION

**Frage**: "Wo könnten **AI-Vorschläge** Sachbearbeiter unterstützen?"

**Beispiele**:

| Feature | Beschreibung | Business Value |
|---------|--------------|----------------|
| **Tarif-Empfehlungen** | AI schlägt optimalen Tarif basierend auf Kundenprofil vor | Conversion ↑ |
| **Risk Scoring** | AI bewertet Risiko eines Antrags/Schadens | Fraud Detection ↑ |
| **Next-Best-Action** | AI schlägt nächsten Prozessschritt vor | Prozesseffizienz ↑ |
| **Duplicate Detection** | AI erkennt Duplikate (Kunden, Verträge, Schäden) | Datenqualität ↑ |

**WGV-Input sammeln**:
- "Wo müssen Sachbearbeiter schwierige Entscheidungen treffen?"
- "Wo wäre ein 'Vorschlag' hilfreich?"

---

#### Kategorie 3: INTELLIGENCE

**Frage**: "Welche **smarten Funktionen** würden Business Value schaffen?"

**Beispiele**:

| Feature | Beschreibung | Business Value |
|---------|--------------|----------------|
| **Semantic Search** | "Zeige alle Verträge ähnlich zu diesem" (nicht nur Keyword) | Schnellere Info-Beschaffung |
| **Predictive Analytics** | "Welche Kunden werden wahrscheinlich kündigen?" | Retention ↑ |
| **Anomaly Detection** | AI erkennt ungewöhnliche Muster (Fraud, Fehler) | Risiko ↓ |
| **Trend Analysis** | AI zeigt Trends in Schadensverläufen | Strategische Insights |

**WGV-Input sammeln**:
- "Welche Fragen könnten Sie mit Daten beantworten, wenn Sie die Werkzeuge hätten?"

---

#### Kategorie 4: INTERACTION

**Frage**: "Welche **neuen UI-Interaktionen** könnten sinnvoll sein?"

**Beispiele**:

| Feature | Beschreibung | Business Value |
|---------|--------------|----------------|
| **Chatbot für einfache Queries** | "Zeige mir den Vertrag von Kunde X" | Self-Service ↑ |
| **Voice Input** | Sachbearbeiter diktiert Schadensnotizen | Schnellere Erfassung |
| **Conversational Forms** | "Ich möchte einen Schaden anlegen" → Chat-Dialog statt Formular | UX ↑ |
| **Smart Suggestions** | Autocomplete für Kundennamen, Adressen | Tippfehler ↓ |

**WGV-Input sammeln**:
- "Wie würden Power User am liebsten mit dem System interagieren?"
- "Chatbot oder klassisches Formular - wo macht was Sinn?"

**WICHTIG**: Hybrid UI-Konzept (aus UI/UX Session) hier einbringen!

---

#### Kategorie 5: INTEGRATION

**Frage**: "Wie könnte AI **verschiedene Systeme intelligenter verbinden**?"

**Beispiele**:

| Feature | Beschreibung | Business Value |
|---------|--------------|----------------|
| **Unified Search** | Suche über ICIS + SAP + DMS + COR Life gleichzeitig | Ein Suchfeld statt 4 |
| **Smart Data Sync** | AI erkennt, welche Daten zwischen Systemen abgeglichen werden müssen | Konsistenz ↑ |
| **Context Switching Assistant** | "Zeige mir SAP-Daten, während ich in ICIS arbeite" | Medienbrüche ↓ |
| **Intelligent Caching** | AI lädt Daten aus langsamen Systemen proaktiv vor | Wartezeit ↓ |

**WGV-Input sammeln**:
- "Welche Systemwechsel sind am störendsten?"
- "Wo müssen Sie manuell Daten zwischen Systemen abgleichen?"

---

**Nach allen 5 Kategorien**:

**Sammlung auf Whiteboard**:

```
AUTOMATION (5-8 Features)
├─ Auto-fill aus Dokumenten (OCR)
├─ Automatische Kategorisierung
├─ Auto-Vervollständigung
└─ ...

AUGMENTATION (3-5 Features)
├─ Tarif-Empfehlungen
├─ Risk Scoring
└─ ...

INTELLIGENCE (3-5 Features)
├─ Semantic Search
├─ Predictive Analytics
└─ ...

INTERACTION (3-5 Features)
├─ Chatbot für einfache Queries
├─ Conversational Forms
└─ ...

INTEGRATION (2-4 Features)
├─ Unified Search
├─ Smart Data Sync
└─ ...
```

**Ergebnis**: ~15-25 Feature-Ideen gesammelt

---

### Schritt 3: Feature Catalog Structuring (~10min)

**Ziel**: Von Brainstorming-Chaos zu strukturiertem Katalog

**Aktivität**: Clustering und Deduplizierung

**Durchführung**:

1. **Duplikate entfernen**: 
   - "Auto-fill" und "Auto-Vervollständigung" → Zusammenführen
   - "Chatbot" erscheint in INTERACTION + AUGMENTATION → Einmal aufführen

2. **Konkretisieren**:
   - "AI-Support" → Zu vage, was genau?
   - "Semantic Search" → Gut, konkret
   - "Bessere Suche" → Umformulieren zu "Semantic Search"

3. **Kategorisieren** nach Anwendungsfall:
   - Für welche **Maske** ist das relevant?
   - Für welchen **User-Typ**? (Power User vs. Gelegenheitsnutzer)

**Template** (Excel/Miro):

| Feature ID | Feature Name | Kategorie | Beschreibung | Relevante Maske(n) | User Type |
|------------|--------------|-----------|--------------|-------------------|-----------|
| F001 | Auto-fill aus PDF | Automation | OCR + AI extrahiert Schadensdaten aus gescanntem Bericht | Schadenanlage | Power User |
| F002 | Chatbot für Adressänderung | Interaction | Conversational UI für einfache Datenänderungen | Adressänderung | Gelegenheitsnutzer |
| F003 | Semantic Search | Intelligence | "Zeige ähnliche Verträge" | Vertragssuche | Power User |
| F004 | Tarif-Empfehlung | Augmentation | AI schlägt optimalen Tarif vor | Vertragsabschluss | Power User |
| ... | ... | ... | ... | ... | ... |

**Ergebnis**: Strukturierter Katalog mit 10-15 Features

**Output Part 1**:
- 📋 Feature-Katalog (10-15 Features)
- 🗂️ Kategorisiert (Automation, Augmentation, Intelligence, Interaction, Integration)
- 🔗 Verknüpft mit MVP-Masken

---

## Part 2: Feature Prioritization mit RICE (~15-20min)

**Ziel**: Top 3-5 Features für MVP auswählen

### Framework Reuse (5min)

**WICHTIG**: RICE wurde bereits in Maskenanalyse gelehrt!

**Quick Recap** (2min, NICHT neu lehren):

> "Wir haben vorhin bei der Maskenanalyse RICE gelernt. Erinnern Sie sich?
> 
> ```
> RICE Score = (Reach × Impact × Confidence) / Effort
> ```
> 
> Das funktioniert genauso für Features:
> - **Reach**: Wie viele Nutzer profitieren davon?
> - **Impact**: Wie viel Business Value? (1-5)
> - **Confidence**: Wie sicher sind wir, dass es funktioniert? (%)
> - **Effort**: Wie viel Aufwand? (Person-Wochen)
> 
> Wenden wir das jetzt auf unsere Features an!"

**Kein Deep-Dive**, nur kurze Erinnerung!

---

### RICE Scoring Session (10-15min)

**Vorbereitung**:
- Excel-Template vorbereitet (analog zu Maskenanalyse)
- Feature-Katalog (10-15 Features) als Basis

**Scoring-Prozess** (~1min pro Feature):

**Template**:

| Feature | Reach (Users) | Impact (1-5) | Confidence (%) | Effort (weeks) | RICE Score |
|---------|---------------|--------------|----------------|----------------|------------|
| Auto-fill aus PDF | 30 | 4 | 60% | 4 | 18 |
| Chatbot Adressänderung | 200 | 2 | 80% | 3 | 106.7 |
| Semantic Search | 100 | 3 | 70% | 6 | 35 |
| Tarif-Empfehlung | 50 | 5 | 50% | 8 | 15.6 |
| ... | ... | ... | ... | ... | ... |

**Beispiel-Scoring** (live mit WGV):

```
Feature: "Chatbot für Adressänderung"

Reach: "Alle 200 Sachbearbeiter, die Adressänderungen machen" → 200
Impact: "Spart Zeit, aber nicht mission-critical" → 2 (Low)
Confidence: "Chatbots sind bewährt, Adressänderung ist simpel" → 80%
Effort: "Chatbot-Integration + NLP + Testing" → 3 Wochen

RICE = (200 × 2 × 0.8) / 3 = 106.7

→ Quick Win! (High Reach, Low Effort)
```

**Weitere Beispiele**:

```
Feature: "Auto-fill aus PDF (OCR + AI)"

Reach: "~30 Sachbearbeiter in Schadenbearbeitung" → 30
Impact: "Spart 70% Zeit, weniger Fehler" → 4 (High)
Confidence: "OCR ist gut, aber AI-Extraction noch unsicher" → 60%
Effort: "OCR-Integration + AI-Modell trainieren + Testing" → 4 Wochen

RICE = (30 × 4 × 0.6) / 4 = 18

→ Strategic (Medium RICE, aber hoher Impact für Nische)
```

---

### Confidence-Kalibrierung für AI-Features

**Besonderheit**: AI-Features haben oft **niedrigere Confidence** als Standard-Features

**Faktoren, die Confidence senken**:

| Faktor | Confidence-Reduktion | Beispiel |
|--------|---------------------|----------|
| **AI-Modell muss trainiert werden** | −20% | Custom OCR für Versicherungsdokumente |
| **Unbekannte Datenqualität** | −15% | Semantic Search auf legacy Daten |
| **Neue Technologie (unbewiesen)** | −10% | Conversational UI für komplexe Workflows |
| **Regulatorische Unsicherheit** | −10% | AI-Entscheidungen in regulierter Branche |

**Faktoren, die Confidence erhöhen**:

| Faktor | Confidence-Erhöhung | Beispiel |
|--------|---------------------|----------|
| **Bewährte Technologie** | +10% | Standard-Chatbot (kein Custom NLP) |
| **Klare Datengrundlage** | +10% | Auto-fill aus strukturierten Datenbanken |
| **Proof-of-Concept vorhanden** | +15% | Ähnliches Feature bei ICIS+ bereits im Einsatz |

**Diskussion moderieren**:
- "Wie sicher sind wir, dass das funktioniert?"
- "Haben wir ähnliche Features schon mal gebaut?"
- "Welche Risiken sehen Sie?"

---

### Top Features Selection (~5min)

**Nach Scoring aller Features**:

**Sortieren nach RICE Score** (höchste zuerst):

```
Rang │ Feature                      │ RICE  │ Kategorie     │ Quadrant
─────┼──────────────────────────────┼───────┼───────────────┼───────────
  1  │ Chatbot Adressänderung       │ 106.7 │ Interaction   │ Quick Win
  2  │ Semantic Search              │ 35    │ Intelligence  │ Strategic
  3  │ Auto-fill aus PDF            │ 18    │ Automation    │ Strategic
  4  │ Tarif-Empfehlung             │ 15.6  │ Augmentation  │ Strategic
  5  │ Unified Search (ICIS+SAP)    │ 12    │ Integration   │ Fill-in
...
```

**Diskussion**:
> "Basierend auf RICE: Welche **3-5 Features** wollen wir im MVP haben?"

**Auswahlkriterien**:
- ✅ **Mindestens 1 Quick Win** (schneller Erfolg)
- ✅ **Mix aus Kategorien** (nicht nur Chatbot, auch Intelligence/Automation)
- ✅ **Passt zu MVP-Masken** (Feature muss zu ausgewählten Masken passen)
- ✅ **Technisch validierbar** (Tag 2 muss Machbarkeit prüfen können)

**Beispiel-Auswahl**:

```
MVP Features (3-5 ausgewählt):

1. Chatbot für Adressänderung (RICE: 106.7, Quick Win)
   - Passt zu: Adressänderungs-Maske (MVP-Kandidat)
   - Kategorie: Interaction
   - Aufwand: 3 Wochen

2. Semantic Search (RICE: 35, Strategic)
   - Passt zu: Vertragssuche, Schadensuche
   - Kategorie: Intelligence
   - Aufwand: 6 Wochen

3. Auto-fill aus PDF (RICE: 18, Strategic)
   - Passt zu: Schadenanlage (MVP-Kandidat)
   - Kategorie: Automation
   - Aufwand: 4 Wochen

4. (Optional) Tarif-Empfehlung (RICE: 15.6)
   - Passt zu: Vertragsabschluss
   - Kategorie: Augmentation
   - Aufwand: 8 Wochen
```

**Rationale dokumentieren**:
- Warum diese Features?
- Welche Masken profitieren davon?
- Welche Patterns decken sie ab?

---

### Feature-Mask Mapping (5min)

**Wichtig**: Features zu Masken zuordnen

**Template** (Whiteboard/Miro):

```
MVP-Maske: Adressänderung
├─ Feature: Chatbot für einfache Änderungen
├─ Feature: Auto-Vervollständigung (Adressen)
└─ Feature: (Standard-UI, kein weiteres AI-Feature)

MVP-Maske: Vertragsabschluss
├─ Feature: Tarif-Empfehlung (AI)
├─ Feature: Semantic Search (ähnliche Verträge)
└─ Feature: Auto-fill aus CRM-Daten

MVP-Maske: Schadenanlage
├─ Feature: Auto-fill aus PDF (OCR + AI)
├─ Feature: Duplicate Detection (AI)
└─ Feature: Risk Scoring (AI)
```

**Diskussion**:
- "Macht diese Zuordnung Sinn?"
- "Haben wir zu viele Features für eine Maske?" (Scope Creep!)
- "Gibt es Masken ohne AI-Features?" (Das ist OK!)

**Output Part 2**:
- ✅ RICE-scored Feature-Liste
- 🎯 Top 3-5 Features ausgewählt
- 🔗 Features zu Masken zugeordnet

---

## Gesamtoutput der Session

Am Ende haben wir:

✅ **Feature-Katalog**: 10-15 AI/UX Features dokumentiert  
✅ **Priorisierung**: RICE-Scores für alle Features  
✅ **MVP-Selection**: 3-5 Features für Phase 1 ausgewählt  
✅ **Feature-Mask-Mapping**: Welches Feature für welche Maske?  
✅ **Rationale**: Warum diese Features? (dokumentiert)  
✅ **Input für Tag 2**: Technische Validierung der Features  

---

## Häufige Facilitator-Herausforderungen

### Challenge 1: "AI soll alles lösen" (Overhype)

**Symptom**: Jedes Problem wird mit "AI macht das" beantwortet

**Lösung**:
- **Realitäts-Check**: "Welche **Daten** braucht die AI dafür?"
- **Complexity aufzeigen**: "AI-Modell trainieren = 3-6 Monate, nicht 3 Wochen"
- **Effort entsprechend erhöhen**: Unrealistische Features bekommen hohen Effort → niedriger RICE
- **Beispiele zeigen**: "Chatbot für Adressänderung = einfach. Chatbot für Schadensbeurteilung = komplex."

---

### Challenge 2: "Wir haben keine AI-Experten" (Angst)

**Symptom**: WGV ist unsicher, ob sie AI-Features bauen können

**Lösung**:
- **Realistische Erwartungen**: "Ihr braucht keine AI-Forscher, nur gute Entwickler + Tools"
- **Managed Services zeigen**: "Viele AI-Features nutzen fertige APIs (Azure AI, OpenAI)"
- **Confidence reflektiert Unsicherheit**: "Unsicher = Confidence 50%, das ist OK!"
- **Tag 2 validiert**: "Morgen klären wir technisch, was machbar ist"

---

### Challenge 3: "Feature-Scope explodiert"

**Symptom**: 30+ Features im Katalog, alle "must-have"

**Lösung**:
- **RICE als Realitäts-Check**: "Schauen wir uns die Scores an - welche sind wirklich prioritär?"
- **MVP-Konzept wiederholen**: "Phase 1 = Lernen, nicht alles bauen"
- **MoSCoW anwenden**: "Must / Should / Could / Won't"
- **Zeitbudget zeigen**: "3 Features = 12 Wochen, 10 Features = 40 Wochen. Was ist realistisch?"

---

### Challenge 4: "Features passen nicht zu Masken"

**Symptom**: Semantic Search ausgewählt, aber keine Such-Maske im MVP

**Lösung**:
- **Feature-Mask-Mapping Review**: "Zu welcher MVP-Maske gehört dieses Feature?"
- **Scope adjustieren**: Entweder Feature verschieben (Phase 2) oder Maske hinzufügen
- **Pragmatisch**: "Wir können Semantic Search als Proof-of-Concept bauen, auch ohne dedizierte Maske"

---

### Challenge 5: "Confidence-Bewertung sehr divergent"

**Symptom**: Architekten sagen 80%, Nutzer sagen 30%

**Lösung**:
- **Perspektiven klären**: "Architekten = technische Machbarkeit, Nutzer = Business Value"
- **Mittelweg finden**: (80% + 30%) / 2 = 55%
- **Unsicherheit dokumentieren**: "Hohe Varianz → Tag 2 Spike/Prototype nötig"
- **Confidence = konservativ**: Im Zweifel niedriger ansetzen

---

### Challenge 6: "Regulatorische Bedenken bei AI"

**Symptom**: "Dürfen wir AI für Schadensentscheidungen nutzen?" (DSGVO, Transparenz)

**Lösung**:
- **AI als Augmentation, nicht Automation**: "AI schlägt vor, Mensch entscheidet"
- **Explainability betonen**: "AI muss Entscheidung begründen können"
- **Compliance-Feature hinzufügen**: "AI Audit Trail" als eigenes Feature
- **Confidence entsprechend senken**: Regulatorisches Risiko = −10-20% Confidence

---

## Integration mit weiteren Tag 1 Aktivitäten

### Input aus Domain Mapping

**Was wir nutzen**:
- Domain Storytelling → Pain Points für Feature-Identifikation
- Automation Opportunities (Annotationen) → Direkter Input für AI-Features
- Ubiquitous Language → Feature-Benennung (fachlich korrekt)

---

### Input aus Maskenanalyse

**Was wir nutzen**:
- 3-5 MVP-Masken → Basis für Feature-Zuordnung
- RICE-Framework → Wird wiederverwendet (nicht neu gelehrt!)
- Quick Wins Mindset → Auch bei Features Quick Wins suchen

---

### Input aus UI/UX Skizze (falls bereits durchgeführt)

**Was wir nutzen**:
- Hybrid UI-Konzept (Chatbot vs. Forms) → Informiert Interaction-Features
- Power User Workflows → Welche Features passen zu Power Users?
- Pain Points in User Journeys → Feature-Opportunities

---

### Output für "Initial Scope Discussion" (~1h später)

**Was wir übergeben**:
- 3-5 MVP-Features → Erweitern den Scope (Masken + Features)
- Feature-Mask-Mapping → Vollständiges MVP-Bild
- RICE-Scores → Priorisierung für Roadmap

---

### Output für Tag 2

**Was Tag 2 nutzt**:
- **3-5 MVP-Features** → Technische Validierung (Ist das machbar?)
- **AI-Feature-Katalog** → Input für "AI Integration" Session (~1.5h)
- **Confidence-Scores** → Identifikation von Spikes/Prototypes (wo unsicher?)
- **Effort-Schätzungen** → Input für Roadmap/Timeline-Planung

---

## Materialien & Templates

### Checkliste für Facilitator

**Vor dem Workshop**:
- [ ] Domain Storytelling Ergebnisse bereithalten (Pain Points)
- [ ] Maskenanalyse-Ergebnisse bereithalten (3-5 MVP-Masken)
- [ ] Whiteboard/Miro vorbereiten:
  - [ ] 5 Kategorien (Automation, Augmentation, Intelligence, Interaction, Integration)
  - [ ] Feature-Katalog-Template
  - [ ] RICE-Scoring-Template (analog zu Maskenanalyse)
- [ ] AI-Feature-Beispiele vorbereiten (Insurance-Domain-spezifisch)
- [ ] Realismus-Check vorbereitet (Effort-Schätzungen für typische AI-Features)

**Während des Workshops**:
- [ ] Pain Point Mapping durchführen (10min)
- [ ] Brainstorming alle 5 Kategorien (15min)
- [ ] Feature-Katalog strukturieren (10-15 Features)
- [ ] RICE-Scoring live durchführen (10-15min)
- [ ] Top 3-5 Features auswählen und dokumentieren
- [ ] Feature-Mask-Mapping erstellen
- [ ] Screenshots/Fotos von allen Whiteboards

**Nach dem Workshop**:
- [ ] Feature-Katalog finalisieren (Excel/Confluence)
- [ ] RICE-Scores dokumentieren
- [ ] MVP-Features Liste an WGV senden
- [ ] Input für Tag 2 vorbereiten (AI Integration Session)

---

### Template Files (Deliverables)

**File 1: `WGV_AI_Feature_Catalog.xlsx`**

Spalten:
- Feature ID
- Feature Name
- Kategorie (Dropdown: Automation / Augmentation / Intelligence / Interaction / Integration)
- Beschreibung (Text)
- Relevante Maske(n) (Multiple Choice)
- User Type (Dropdown: Power User / Gelegenheitsnutzer / Beide)
- Reach (Nutzer)
- Impact (1-5, Dropdown)
- Confidence (%, Slider)
- Effort (Wochen)
- RICE Score (Formel)
- Status (Dropdown: MVP / Phase 2 / Backlog / Won't do)

---

**File 2: `WGV_Feature_Mask_Mapping.pptx`**

Slide 1: Übersicht

```
MVP-Scope = Masken + Features

Masken (3-5):
├─ Adressänderung
├─ Vertragsabschluss
└─ Schadenanlage

Features (3-5):
├─ Chatbot für Adressänderung
├─ Semantic Search
└─ Auto-fill aus PDF
```

Slide 2-4: Detail pro Maske

```
Maske: Adressänderung

Features:
├─ Chatbot für einfache Änderungen (RICE: 106.7)
│  - Kategorie: Interaction
│  - Effort: 3 Wochen
│  - Business Value: Zeitersparnis 40%
│
└─ Auto-Vervollständigung (RICE: 45)
   - Kategorie: Augmentation
   - Effort: 2 Wochen
   - Business Value: Tippfehler ↓ 60%
```

---

**File 3: `WGV_AI_Features_Rationale.md`**

Markdown-Dokument mit Begründung:

```markdown
# AI Features für WGV ICIS Modernisierung - Rationale

## Ausgewählte Features für MVP

### 1. Chatbot für Adressänderung (RICE: 106.7)

**Warum ausgewählt?**
- Quick Win: Low Effort (3 Wochen), High Reach (200 Nutzer)
- Passt perfekt zu MVP-Maske "Adressänderung"
- Bewährte Technologie (Confidence: 80%)
- Zeigt Hybrid UI-Konzept (Chatbot + Forms)

**Business Value:**
- Zeitersparnis: 40% für einfache Adressänderungen
- Self-Service-Potenzial (weniger Support-Anfragen)
- Proof-of-Concept für Conversational UI

**Risiken:**
- NLP-Training für Versicherungs-Domain nötig
- Fallback zu Forms-UI muss funktionieren

---

### 2. Semantic Search (RICE: 35)

...
```

---

## Referenzen & Verbindungen zu anderen Dokumenten

### Facilitator-Referenzen

- **Decision Frameworks**: `facilitation/decision_frameworks.md`
  - RICE Scoring (bereits in Maskenanalyse gelehrt!)
  - Impact/Effort Matrix (Reuse)
- **Maskenanalyse**: `facilitation/tag1_maskenanalyse_guide.md`
  - RICE-Framework (Input)
  - 3-5 MVP-Masken (Input für Feature-Mapping)
- **Domain Mapping**: `facilitation/tag1_domain_mapping_guide.md`
  - Domain Storytelling Pain Points (Input für Feature-Discovery)

---

## Anpassungen & Varianten

### Variant A: Mehr Zeit verfügbar (90min statt 45min)

**Änderungen**:
- Part 1 (Discovery): 60min statt 40min
  - Alle 5 Kategorien tiefer durcharbeiten
  - Mehr Features sammeln (20-30 statt 10-15)
- Part 2 (Prioritization): 30min statt 15min
  - Mehr Features scoren (15-20 statt 10-15)
  - Detailliertere Feature-Mask-Mapping

---

### Variant B: Weniger Zeit verfügbar (30min statt 45min)

**Änderungen**:
- Part 1 (Discovery): 20min statt 40min
  - Nur 3 Kategorien (Automation, Augmentation, Interaction)
  - Schnelleres Brainstorming (8-10 Features)
- Part 2 (Prioritization): 10min statt 15min
  - Nur Top 5 Features scoren
  - Quick Selection ohne ausführliche Diskussion

**Trade-off**: Weniger Features, aber Fokus auf Quick Wins

---

### Variant C: Remote Workshop

**Anpassungen**:
- **Miro statt physischem Whiteboard**
- **Breakout Rooms** für paralleles Brainstorming (je Kategorie)
- **Digitale Voting** für Feature-Priorisierung (Dot-Voting)
- **Screen Sharing** für RICE-Scoring (alle sehen Excel)

---

### Variant D: AI-skeptisches Publikum

**Symptom**: WGV ist unsicher/skeptisch gegenüber AI

**Anpassungen**:
- **Mehr Zeit für Realitäts-Check**: Zeigen, was heute möglich ist (Demos!)
- **Konservative Features zuerst**: Chatbot, Auto-Vervollständigung (bewährt)
- **Keine Hype-Features**: Nicht mit "AGI löst alles" argumentieren
- **Managed Services betonen**: "Ihr baut nicht selbst AI, nutzt Azure/OpenAI"
- **Augmentation > Automation**: "AI unterstützt Menschen, ersetzt sie nicht"

---

## Kommunikations-Snippets

### Opening Statement

> "Wir haben jetzt 3-5 Masken für das MVP. Die Frage ist: **Was soll das modernisierte System können, was das alte nicht konnte?**
> 
> Besonders spannend: **Wo kann AI helfen?**
> - Manuelle Prozesse beschleunigen?
> - Sachbearbeiter bei Entscheidungen unterstützen?
> - Daten intelligenter durchsuchen?
> 
> In den nächsten 45 Minuten:
> 1. Sammeln wir AI-Feature-Ideen (35min)
> 2. Priorisieren wir mit RICE - dem Framework, das wir eben gelernt haben (15min)
> 
> Los geht's!"

---

### Transition zu RICE (Part 2)

> "Super, wir haben jetzt 15 coole Feature-Ideen.
> 
> Jetzt die Frage: **Welche bauen wir zuerst?**
> 
> Erinnern Sie sich an RICE von vorhin? Genau dasselbe Prinzip, jetzt auf Features angewendet. Reach, Impact, Confidence, Effort - los geht's!"

---

### Closing Statement

> "Perfekt! Wir haben:
> - ✅ 15 AI-Features identifiziert
> - ✅ Mit RICE priorisiert
> - ✅ Top 3-5 für MVP ausgewählt
> - ✅ Features zu Masken zugeordnet
> 
> **MVP-Scope jetzt komplett**:
> - 3-5 Masken (aus Maskenanalyse)
> - 3-5 Features (aus dieser Session)
> 
> **Nächster Schritt**: Initial Scope Discussion - validieren wir diesen Scope gemeinsam!
> 
> **Morgen (Tag 2)**: Technische Validierung - ist das alles machbar?"

---

**Erstellt**: 2026-04-14  
**Autor**: Sócrates Ponce (codecentric)  
**Workshop**: WGV ICIS Modernisierung, 28-30 April 2026  
**Version**: 1.0
