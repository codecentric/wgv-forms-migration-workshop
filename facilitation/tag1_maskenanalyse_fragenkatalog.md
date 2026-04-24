# Tag 1: Maskenanalyse - Fragenkatalog

**Workshop**: WGV ICIS Modernisierung  
**Aktivität**: Analyse von Masken (stichprobenartig)  
**Dauer**: ~1.5h  
**Zielgruppe**: Nutzer, Architekten, (optional: PO, Developer)

---

## Zweck dieses Dokuments

Dieser Fragenkatalog unterstützt Facilitators während der Maskenanalyse-Session am Tag 1.

**Verwendung**:
- ✅ **Während Tier 2 (Pattern-Based Sampling)**: Strukturierte Befragung für 10-15 repräsentative Masken
- ✅ **Während Tier 3 (RICE Scoring)**: Datenerhebung für RICE-Komponenten (Reach, Impact, Effort, Confidence)
- ✅ **Als Template für WGV**: Post-Workshop Selbstbewertung weiterer Masken

**NICHT verwenden für**:
- ❌ UI/UX Design-Fragen (gehören zur späteren "Anwendungskonzept UI/UX" Session)
- ❌ Detaillierte technische Architektur (gehört zu Tag 2)

**Ergänzt**: `facilitation/tag1_maskenanalyse_guide.md` (Methodik-Guide)

---

## Fragenkategorien

Die 26 Fragen sind in 4 Kategorien organisiert:

1. **Business Value & Nutzung** (7 Fragen) → Für RICE: Reach + Impact
2. **Funktionalität & Komplexität** (7 Fragen) → Für 2×2 Complexity Matrix + Pattern-Matching
3. **Technische Migration** (7 Fragen) → Für RICE: Effort + Confidence
4. **Priorisierung & Patterns** (5 Fragen) → Für Clustering + MVP-Auswahl

---

## Kategorie 1: Business Value & Nutzung

**Ziel**: RICE-Komponenten **Reach** und **Impact** schätzen

### Frage 1.1: Wer nutzt diese Maske?
**Format**: Rolle(n), Abteilung(en), Anzahl Nutzer  
**Beispiel**: "~50 Sachbearbeiter Vertrieb"  
**RICE-Mapping**: → **Reach** (Basis für Nutzer/Monat)

---

### Frage 1.2: Wie oft wird diese Maske genutzt?
**Format**: Dropdown (täglich / wöchentlich / monatlich / selten)  
**Beispiel**: "Täglich"  
**RICE-Mapping**: → **Reach** (Multiplikator für Nutzungshäufigkeit)

**Umrechnung für RICE**:
- Täglich → Nutzer × 20 (Arbeitstage/Monat)
- Wöchentlich → Nutzer × 4
- Monatlich → Nutzer × 1
- Selten → Nutzer × 0.25

---

### Frage 1.3: Wie viele Transaktionen/Vorgänge pro Monat?
**Format**: Zahl oder Schätzbereich  
**Beispiel**: "~200 Vertragsabschlüsse/Monat"  
**RICE-Mapping**: → **Reach** (alternativ zu Nutzerzahl, falls genauer)

**Hinweis**: Falls WGV konkrete Transaktionszahlen hat, diese statt Nutzerzahl verwenden.

---

### Frage 1.4: Was passiert, wenn diese Maske nicht verfügbar ist?
**Format**: Beschreibung der Business-Konsequenz  
**Beispiel**: "Neugeschäft stoppt, Revenue-Verlust"  
**RICE-Mapping**: → **Impact** (Indikator für Business Criticality)

**Impact-Skala**:
- **1 (Minimal)**: Verzögerung, aber Workaround möglich
- **2 (Low)**: Beeinträchtigt Workflow, aber nicht kritisch
- **3 (Medium)**: Wichtiger Prozess, spürbare Auswirkung
- **4 (High)**: Geschäftskritisch, Revenue-Auswirkung
- **5 (Massive)**: Mission-critical, regulatorisch erforderlich

---

### Frage 1.5: Ist diese Maske geschäftskritisch?
**Format**: Ja / Nein + Begründung  
**Beispiel**: "Ja – Kern-Prozess für Neugeschäft (Revenue)"  
**RICE-Mapping**: → **Impact** (Ja → Impact ≥ 4)

---

### Frage 1.6: Welchen fachlichen Prozess unterstützt diese Maske?
**Format**: Prozessname oder Bounded Context  
**Beispiel**: "Vertragsabschluss Neugeschäft" (Bounded Context: Vertragsverwaltung)  
**RICE-Mapping**: → **Impact** (Core Domain Prozesse → höherer Impact)

**Hinweis**: Nutze Ergebnisse aus "Domain Mapping" Session (~1.5h vorher) für Bounded Context.

---

### Frage 1.7: Gibt es regulatorische oder Compliance-Anforderungen?
**Format**: Ja / Nein + Standard (z.B. GDV, DSGVO, VAG)  
**Beispiel**: "Ja – GDV-Normen für Vertragsabschluss"  
**RICE-Mapping**: → **Impact** (Regulatorisch erforderlich → Impact = 5)

---

## Kategorie 2: Funktionalität & Komplexität

**Ziel**: 2×2 Complexity Matrix Klassifikation (UI Complexity × Logic Complexity) + Pattern-Matching

### Frage 2.1: Was macht diese Maske?
**Format**: Funktionale Beschreibung (1-2 Sätze)  
**Beispiel**: "Erfasst Kundendaten für Neugeschäft, ruft Tarifberechnung auf, erstellt Vertrag"  
**Complexity Classification**: Hilft bei initialer Einordnung + Pattern-Erkennung

---

### Frage 2.2: Ist das eine CRUD-Maske oder ein Workflow?
**Format**: Dropdown (CRUD / Workflow / Suche-Abfrage / Report / Hybrid)  
**Beispiel**: "Workflow (Multi-Step)"  
**Complexity Classification**:
- CRUD → Tendenz **Simple Logic**
- Workflow (linear) → Tendenz **Simple bis Medium Logic**
- Workflow (komplex, bedingt) → Tendenz **Complex Logic**

**Pattern-Hinweis**: Hilft bei Pattern-Matching (P1: CRUD, P4: Wizard, P6: Complex Workflow)

---

### Frage 2.3: Wie viele Felder/Eingaben gibt es (grobe Schätzung)?
**Format**: Zahl oder Bereich  
**Beispiel**: "~50-60 Felder (über 4 Tabs verteilt)"  
**Complexity Classification**: → **UI Complexity**
- <20 Felder → **Simple UI**
- 20-30 Felder → **Medium UI**
- >30 Felder → **Complex UI**

**Relevanz**:
- Haupt-Kriterium für **UI Complexity-Achse** der 2×2 Matrix
- Auch **Effort-Indikator** für RICE

---

### Frage 2.4: Welche Business Rules sind implementiert?
**Format**: Liste oder Kategorien (Validierungen, Berechnungen, Regeln)  
**Beispiel**: "Tarifberechnung, Risikoprüfung, Plausibilitätschecks, GDV-Validierung"  
**Complexity Classification**: → **Logic Complexity**
- Wenige, einfache Validierungen → **Simple Logic**
- Berechnungen oder mehrere Business Rules → **Medium Logic**
- Viele interdependente Regeln, komplexe Berechnungen → **Complex Logic**

**Relevanz**: Haupt-Kriterium für **Logic Complexity-Achse** der 2×2 Matrix

---

### Frage 2.5: Gibt es komplexe Abhängigkeiten?
**Format**: Ja / Nein + Beschreibung  
**Beispiel**: "Ja – Tarifauswahl beeinflusst verfügbare Zusatzoptionen, die wiederum Prämie ändern"  
**Complexity Classification**: → **Logic Complexity** (erhöht)
- Keine Abhängigkeiten → **Simple Logic**
- Vorhersehbare Abhängigkeiten (A beeinflusst B) → **Medium Logic**
- Viele interdependente Abhängigkeiten (A↔B↔C) → **Complex Logic**

**Relevanz**: Indikator für Logic Complexity + Erhöht Effort-Schätzung

---

### Frage 2.6: Wird externe Logik aufgerufen?
**Format**: Ja / Nein + Art (Stored Procedures, Web Services, etc.)  
**Beispiel**: "Ja – 3 Stored Procedures (Tarif, Vertrag, Risiko)"  
**Complexity Classification**: → **Logic Complexity**
- Keine externe Logik (0 SPs) → **Simple Logic**
- 1-2 Stored Procedures (dokumentiert) → **Medium Logic**
- 3+ Stored Procedures oder externe Services → **Complex Logic**

**RICE-Mapping**: → **Effort** (mehr SPs = mehr Aufwand) + **Confidence** (Black Box = Risk)

---

### Frage 2.7: Gibt es Integrationen mit anderen Systemen?
**Format**: Ja / Nein + Systeme (SAP, GDV, DMS, etc.)  
**Beispiel**: "Ja – SAP (Kundendaten), DMS (Vertragsdokumente)"  
**Complexity Classification**: → **Logic Complexity** (erhöht)
- Keine externen Systeme → **Simple/Medium Logic**
- 1 externe Integration → **Medium/Complex Logic**
- 2+ externe Integrationen → **Complex Logic**

**RICE-Mapping**: → **Effort** (+30-50% pro externe Integration)

---

## Kategorie 3: Technische Migration

**Ziel**: RICE-Komponenten **Effort** und **Confidence** schätzen

### Frage 3.1: Wie gut ist diese Maske dokumentiert?
**Format**: Dropdown (Gut / Mittel / Schlecht / Gar nicht)  
**Beispiel**: "Mittel – Fachliches Konzept vorhanden, Code nicht dokumentiert"  
**RICE-Mapping**: → **Confidence**
- Gut → +10% Confidence
- Mittel → Baseline (80%)
- Schlecht → -10% Confidence
- Gar nicht → -20% Confidence

---

### Frage 3.2: Gibt es Experten, die diese Maske kennen?
**Format**: Anzahl Experten + Namen (optional)  
**Beispiel**: "2 Personen (Herr Müller, Frau Schmidt)"  
**RICE-Mapping**: → **Confidence** (Knowledge Risk)
- ≥3 Experten → Baseline
- 1-2 Experten → -20% Confidence
- 0 Experten → -30% Confidence (High Risk!)

---

### Frage 3.3: Ist die Maske ähnlich zu ICIS+ Komponenten?
**Format**: Ja / Nein + Beschreibung  
**Beispiel**: "Nein – Nur in ICIS-Klassik (Oracle Forms), keine Vaadin-Entsprechung"  
**RICE-Mapping**:
- → **Confidence**: Ähnlich zu ICIS+ → +10% (Wiederverwendbarkeit)
- → **Effort**: Ähnlich zu ICIS+ → -20% Aufwand (Komponenten nutzbar)

---

### Frage 3.4: Welche Stored Procedures werden aufgerufen?
**Format**: Liste (SP-Namen oder Anzahl)  
**Beispiel**: "SP_TARIF_BERECHNUNG, SP_VERTRAG_ANLEGEN, SP_RISIKO_PRUEFEN (3 SPs)"  
**RICE-Mapping**: → **Effort**
- Basis: 1 Woche (ohne SPs)
- +0.5 Wochen pro SP-Call (REST API Entwicklung)

**Hinweis**: Diese Info wird am Tag 2 vertieft ("Vorstellung Stored Procedures").

---

### Frage 3.5: Wie komplex ist die Integration zum Backend?
**Format**: Dropdown (Einfach / Mittel / Komplex)  
**Beispiel**: "Komplex – 3 SPs, Parameter-Mapping nicht-trivial, Transaktionssteuerung"  
**RICE-Mapping**: → **Effort**
- Einfach (1 SP, Standard CRUD) → +0.5 Wochen
- Mittel (2-3 SPs, Standard-Parameter) → +1-1.5 Wochen
- Komplex (>3 SPs, komplexe Parameter, Transaktionen) → +2-3 Wochen

---

### Frage 3.6: Gibt es bekannte technische Probleme?
**Format**: Ja / Nein + Beschreibung  
**Beispiel**: "Ja – Performance-Problem bei Tarifberechnung (Legacy-Code, ineffiziente Query)"  
**RICE-Mapping**:
- → **Effort**: Technische Probleme → +20-50% Aufwand (Refactoring nötig)
- → **Confidence**: Unbekannte Probleme → -10% Confidence

---

### Frage 3.7: Wurde diese Maske kürzlich geändert?
**Format**: Ja / Nein + Zeitpunkt  
**Beispiel**: "Ja – Letzte Änderung vor 3 Monaten (GDV-Norm-Update)"  
**RICE-Mapping**: → **Confidence**
- Aktiv gepflegt → +10% Confidence (Code vermutlich sauberer)
- Nicht geändert seit >3 Jahren → -10% Confidence (Legacy-Code-Risiko)

---

## Kategorie 4: Priorisierung & Patterns

**Ziel**: Pattern-Erkennung, Clustering, MVP-Auswahl

### Frage 4.1: Ist das ein Quick Win?
**Format**: Ja / Nein (basierend auf Impact/Effort Matrix)  
**Beispiel**: "Ja – Hoher Business Value (Impact 4), geringer Aufwand (1 Woche)"  
**Verwendung**: Priorisierung für MVP-Auswahl

**Quick Win Kriterien**:
- ✅ Impact ≥ 3 (High Business Value)
- ✅ Effort ≤ 2 Wochen (Low Effort)
- ✅ Confidence ≥ 70% (Low Risk)

---

### Frage 4.2: Zu welchem Bounded Context gehört diese Maske?
**Format**: Bounded Context-Name (aus Domain Mapping)  
**Beispiel**: "Vertragsverwaltung"  
**Verwendung**: Clustering für Pattern-Based Sampling

**Hinweis**: Nutze Ergebnisse aus "Domain Mapping" Session (~1.5h vorher).

---

### Frage 4.3: Welchem Pattern entspricht diese Maske?

**Format**: Dropdown (Pattern-Typen)  
**Beispiel**: "Komplexer Workflow mit Berechnung"

**Pattern-Katalog** (siehe `tag1_masken_pattern_katalog.md` für Details):

| Pattern ID | Pattern Name | Quadrant | Migrations-Ansatz | Aufwand |
|------------|--------------|----------|-------------------|---------|
| **P1** | Simple CRUD | Q1 (Simple/Simple) | React/Angular (AI-generiert) | 1-2w |
| **P2** | Search & Filter | Q1/Q2 | React/Angular + Data Grid | 1-2w |
| **P3** | Multi-Tab Form | Q2 (Complex/Simple) | React/Angular (Tabs) | 2-3w |
| **P4** | Wizard Workflow | Q1-Q3 | React/Angular (Stepper) | 2-4w |
| **P5** | Calculation-Heavy | Q3 (Simple/Complex) | Backend-First + Simple UI | 2-3w |
| **P6** | Complex Workflow | Q4 (Complex/Complex) | Full Custom (AI-assisted) | 4-8w |
| **P7** | Report Generator | Q1 | React/Angular + Template Engine | 2-3w |
| **P8** | Conversational Candidate | Q4 | Chatbot + Form Hybrid (MCP) | 4-8w |

**Verwendung**: Pattern-Matching für Migrations-Ansatz + Aufwand-Schätzung

**Hinweis**: Detaillierter Pattern-Katalog in `facilitation/tag1_masken_pattern_katalog.md`

---

### Frage 4.4: Gibt es ähnliche Masken?
**Format**: Ja / Nein + Beispiele  
**Beispiel**: "Ja – 5 weitere Vertragsabschluss-Masken (unterschiedliche Sparten)"  
**Verwendung**: Clustering, Aufwandsschätzung skalieren

**Implikation**:
- Ähnliche Masken → **Pattern etabliert**, Aufwand sinkt ab 2. Maske
- Einzigartige Maske → **Custom Pattern**, höherer initialer Aufwand

---

### Frage 4.5: Sollte diese Maske 1:1 migriert oder neu gedacht werden?

**Format**: Dropdown (1:1 Migration / Vereinfachung / AI-Automatisierung / Hybride Lösung)  
**Beispiel**: "Hybride Lösung – Routine-Fälle per Chatbot, komplexe Fälle per Formular"

**Optionen**:

| Ansatz | Beschreibung | Wann verwenden? |
|--------|--------------|-----------------|
| **1:1 Migration** | Oracle Forms → Modern UI (gleiche Funktionalität) | Business-kritisch, etablierter Prozess, Power User |
| **Vereinfachung** | Reduziertes UI, unnötige Felder entfernen | Over-engineered Forms, viele ungenutzte Features |
| **AI-Automatisierung** | Prozess teilweise durch AI-Agent ersetzt | Repetitive Aufgaben, regelbasiert, Daten-intensiv |
| **Hybride Lösung** | Conversational UI + Formular (je nach Kontext) | Unterschiedliche User-Typen, variable Komplexität |

**Verwendung**: Input für "AI Features Discussion" (~1h später am Tag 1)

---

## Beispiel: Ausgefüllter Fragenkatalog

**Maske**: "Vertragsabschluss Neugeschäft"

### Kategorie 1: Business Value & Nutzung

| Frage | Antwort |
|-------|---------|
| 1.1 Wer nutzt? | ~50 Sachbearbeiter Vertrieb |
| 1.2 Wie oft? | Täglich |
| 1.3 Transaktionen/Monat? | ~200 Vertragsabschlüsse |
| 1.4 Konsequenz bei Ausfall? | Neugeschäft stoppt, Revenue-Verlust |
| 1.5 Geschäftskritisch? | Ja – Kern-Prozess für Neugeschäft (Revenue) |
| 1.6 Fachlicher Prozess? | Vertragsabschluss Neugeschäft (Bounded Context: Vertragsverwaltung) |
| 1.7 Regulatorisch? | Ja – GDV-Normen, VAG-Anforderungen |

**RICE Ableitung**:
- **Reach**: 200 (Transaktionen/Monat)
- **Impact**: 5 (Geschäftskritisch, Revenue, Regulatorisch)

---

### Kategorie 2: Funktionalität & Komplexität

| Frage | Antwort |
|-------|---------|
| 2.1 Was macht sie? | Erfasst Kundendaten, Vertragsdaten, berechnet Prämie, erstellt Vertrag |
| 2.2 CRUD oder Workflow? | Workflow (Multi-Step: Kunde → Tarif → Prämie → Abschluss) |
| 2.3 Anzahl Felder? | ~50-60 Felder (über 4 Tabs verteilt) |
| 2.4 Business Rules? | Tarifberechnung, Risikoprüfung, Plausibilitätsprüfungen, GDV-Validierung |
| 2.5 Abhängigkeiten? | Ja – Tarifauswahl beeinflusst Optionen, die wiederum Prämie ändern |
| 2.6 Externe Logik? | Ja – 3 Stored Procedures (SP_TARIF_BERECHNUNG, SP_VERTRAG_ANLEGEN, SP_RISIKO_PRUEFEN) |
| 2.7 System-Integrationen? | Ja – SAP (Kundendaten), Tarifrechner (SP), DMS (Vertragsdokumente) |

**2×2 Matrix Ableitung**:
- **UI Complexity**: Complex (50-60 Felder, 4 Tabs)
- **Logic Complexity**: Complex (3 SPs, SAP-Integration, komplexe Berechnungen)
- **Quadrant**: **Q4** (Complex UI, Complex Logic)
- **Pattern**: **P6** (Complex Workflow)

---

### Kategorie 3: Technische Migration

| Frage | Antwort |
|-------|---------|
| 3.1 Dokumentation? | Mittel – Fachliches Konzept vorhanden, Code kaum dokumentiert |
| 3.2 Experten? | 2 Personen (Herr Müller, Frau Schmidt) |
| 3.3 ICIS+ ähnlich? | Nein – Nur in ICIS-Klassik, keine Vaadin-Entsprechung |
| 3.4 Stored Procedures? | 3 SPs (siehe 2.6) |
| 3.5 Backend-Integration Komplexität? | Komplex – 3 SPs, Parameter-Mapping nicht-trivial, Transaktionssteuerung |
| 3.6 Technische Probleme? | Ja – Performance-Problem bei Tarifberechnung (ineffiziente Query) |
| 3.7 Kürzlich geändert? | Ja – Letzte Änderung vor 6 Monaten (GDV-Norm-Update) |

**RICE Ableitung**:
- **Effort**: 4 Wochen (Basis 2 Wochen + 3 SPs à 0.5 Wochen + Komplexität +0.5 Wochen)
- **Confidence**: 60%
  - Start: 80%
  - Dokumentation Mittel: -0%
  - 2 Experten (Knowledge Risk): -20%
  - Technische Probleme: -10%
  - Kürzlich geändert: +10%
  - = 60%

---

### Kategorie 4: Priorisierung & Patterns

| Frage | Antwort |
|-------|---------|
| 4.1 Quick Win? | Nein – Hoher Impact (5), aber hoher Effort (4 Wochen) → **Strategic Project** |
| 4.2 Bounded Context? | Vertragsverwaltung |
| 4.3 Pattern? | Komplexer Workflow mit Berechnung |
| 4.4 Ähnliche Masken? | Ja – 3 weitere Vertragsabschluss-Masken (Sparten: Leben, KFZ, Sach) |
| 4.5 1:1 oder neu gedacht? | 1:1 Migration (etablierter Prozess, Power User gewöhnt) |

---

### RICE Berechnung

```
RICE Score = (Reach × Impact × Confidence) / Effort
           = (200 × 5 × 0.6) / 4
           = 600 / 4
           = 150
```

**Einordnung**: **Strategic Project** (High Impact, High Effort)  
**MVP-Empfehlung**: Phase 1 oder 2 (wichtig, aber kein Quick Win)

---

## Nutzung im Workshop

### Timing: Wann welche Fragen?

| Workshop-Phase | Fragen-Kategorien | Dauer |
|----------------|-------------------|-------|
| **Tier 2: Pattern-Based Sampling** | Kategorie 2 (Funktionalität) + Kategorie 4 (Patterns) | ~25-30min |
| **Tier 3: RICE Scoring Deep Dive** | Kategorie 1 (Business Value) + Kategorie 3 (Technisch) | ~15-20min |

**Empfehlung**: Nicht alle 26 Fragen pro Maske! Pragmatisch anpassen:
- **Quick Assessment** (5min/Maske): Nur Kern-Fragen (1.1, 1.2, 2.1, 2.2, 4.3) + grobe RICE-Schätzung
- **Deep Dive** (10-15min/Maske): Alle Kategorien für MVP-Kandidaten

---

### Format: Wie Fragen stellen?

**Option A: Kollaboratives Ausfüllen** (empfohlen)
- Fragenkatalog als Excel/Google Sheet geteilt
- WGV füllt live aus (Screenshare)
- codecentric moderiert, stellt Fragen
- **Vorteil**: Gemeinsames Verständnis, transparenter Prozess

**Option B: Interview-Stil**
- codecentric stellt Fragen mündlich
- WGV antwortet
- codecentric notiert in Template
- **Vorteil**: Schneller, strukturierter

**Option C: Vorab-Homework**
- WGV füllt Fragenkatalog vor Workshop aus (für 10-15 Masken)
- Workshop = Review und Diskussion
- **Vorteil**: Spart Zeit im Workshop, mehr Masken möglich

**Empfehlung für Tag 1**: Option A (kollaborativ) für Methodik-Vermittlung

---

## Template für Post-Workshop Nutzung

**File**: `WGV_Maskenanalyse_Fragenkatalog.xlsx`

**Struktur**:

| Spalte | Inhalt | Format |
|--------|--------|--------|
| **A: Mask ID** | Eindeutige Kennung | Text |
| **B: Mask Name** | Funktionale Bezeichnung | Text |
| **C-I: Kategorie 1** | Fragen 1.1 - 1.7 | Dropdown / Text / Zahl |
| **J-P: Kategorie 2** | Fragen 2.1 - 2.7 | Dropdown / Text |
| **Q-W: Kategorie 3** | Fragen 3.1 - 3.7 | Dropdown / Text |
| **X-AB: Kategorie 4** | Fragen 4.1 - 4.5 | Dropdown / Text |
| **AC: RICE - Reach** | Berechnet aus 1.2 + 1.3 | Formel |
| **AD: RICE - Impact** | Abgeleitet aus 1.4 + 1.5 + 1.7 | Dropdown (1-5) |
| **AE: RICE - Confidence** | Berechnet aus 3.1 + 3.2 + 3.3 + 3.6 + 3.7 | Formel (%) |
| **AF: RICE - Effort** | Berechnet aus 2.2 + 2.6 + 2.7 + 3.5 | Formel (Wochen) |
| **AG: RICE Score** | =(AC × AD × AE) / AF | Formel |
| **AH: Quadrant** | Quick Win / Strategic / Fill-in / Avoid | Formel (IF) |

**Conditional Formatting**:
- Grün: RICE > 100 (Quick Wins)
- Gelb: RICE 50-100 (Strategic)
- Rot: RICE < 50 (Low Priority)

---

## Integration mit anderen Dokumenten

### Input aus vorherigen Aktivitäten

**Domain Mapping** (`facilitation/tag1_domain_mapping_guide.md`, ~1.5h vorher):
- Frage 1.6 nutzt **Bounded Contexts**
- Frage 1.6 nutzt **Core Domain Chart** (für Impact-Bewertung)
- Frage 4.2 nutzt **Context Map** (für Integration Complexity)

**ICIS Deep Dive** (`facilitation/tag1_icis_deep_dive_guide.md`, optional):
- Frage 3.4 nutzt **Service-Inventar** (Stored Procedures)
- Frage 3.3 nutzt **ICIS+ Komponenten-Katalog**

---

### Output für folgende Aktivitäten

**UI/UX Konzept** (~1.5h später, Tag 1):
- Frage 4.3 (Pattern) → Informiert UI-Pattern-Auswahl
- Frage 4.5 (1:1 vs. neu gedacht) → Chatbot vs. Form Diskussion

**AI Features Discussion** (~1h später, Tag 1):
- Frage 4.5 (AI-Automatisierung) → Kandidaten für AI-Features
- Frage 2.4 (Business Rules) → AI Decision Support Kandidaten

**Tag 2: Technische Validierung**:
- Frage 3.4 (Stored Procedures) → Scope für SP Review
- RICE Scores → Priorisierung für technische Analyse

---

## Häufige Fragen (FAQ)

### F: Müssen wir alle 26 Fragen für jede Maske stellen?

**A**: Nein! Pragmatisch anpassen:
- **Quick Assessment** (5min): Nur 5-7 Kern-Fragen
- **Deep Dive** (10-15min): Alle Fragen für MVP-Kandidaten
- **Post-Workshop**: WGV füllt vollständig aus

---

### F: Was, wenn WGV eine Frage nicht beantworten kann?

**A**: 
- **Option 1**: "Wissen wir nicht" dokumentieren → **Confidence reduzieren** (−20%)
- **Option 2**: Als **Open Question** markieren für Tag 2 (technische Validierung)
- **Option 3**: Grobe Schätzung + niedrige Confidence (50%)

**Wichtig**: Unsicherheit ist OK! Confidence-Faktor reflektiert genau das.

---

### F: Wie gehen wir mit Uneinigkeit im Team um?

**A**: 
- **Moderieren**: Verschiedene Perspektiven hören (Nutzer vs. Architekt vs. Developer)
- **Durchschnitt**: Bei Zahlen (z.B. Effort) → Durchschnittswert
- **Konservativ**: Bei Unsicherheit → Höherer Effort, niedrigere Confidence
- **Dokumentieren**: "Team uneinig → Confidence 50%"

---

### F: Ändern sich die Antworten zwischen Workshop und Post-Workshop?

**A**: **Ja, und das ist OK!** RICE ist iterativ:
- Workshop Tag 1: Grobe Schätzungen (Confidence 50-70%)
- Tag 2 (Technische Validierung): Effort-Schätzungen verfeinert
- Post-Workshop: WGV lernt dazu, passt Schätzungen an

**Best Practice**: RICE Scores regelmäßig aktualisieren (monatlich)

---

## Änderungshistorie

| Version | Datum | Änderung | Autor |
|---------|-------|----------|-------|
| 1.0 | 2026-04-22 | Initiale Erstellung | Sócrates Ponce (codecentric) |

---

**Nächste Schritte**:
1. ✅ Excel-Template erstellen (`WGV_Maskenanalyse_Fragenkatalog.xlsx`)
2. ✅ Im Workshop testen (Tag 1, 28. April 2026)
3. ✅ Basierend auf Feedback anpassen
4. ✅ An WGV übergeben für Post-Workshop Nutzung
