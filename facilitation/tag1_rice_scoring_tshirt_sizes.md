# Tag 1: RICE Scoring - T-Shirt Sizing Approach

**Workshop**: WGV ICIS Modernisierung  
**Aktivität**: Analyse von Masken (Tier 3: RICE Scoring)  
**Verwendung**: Priorisierung von 10-15 MVP-Kandidaten  
**Zielgruppe**: Nutzer, Architekten, Developer

---

## Zweck dieses Dokuments

Dieses Dokument definiert die **RICE-Priorisierungsmethode** mit **T-Shirt Sizing** für die Maskenanalyse im WGV Workshop.

**Warum T-Shirt Sizes statt numerischer Skalen?**
- ✅ Weniger Diskussionen ("S vs. M" statt "2 vs. 3 vs. 4")
- ✅ Schnellere Entscheidungen im Workshop
- ✅ Intuitive Kategorien (XS/S/M/L/XL)
- ✅ Trotzdem objektive Berechnung möglich (Fibonacci-Mapping)

**Verwendung:**
- ✅ **Während Tag 1 Maskenanalyse** (Tier 3: RICE Scoring Deep Dive)
- ✅ **Ergänzt**: `tag1_maskenanalyse_guide.md` (Methodik) und `tag1_maskenanalyse_fragenkatalog.md` (26 Fragen)
- ✅ **Post-Workshop**: WGV kann RICE selbständig auf weitere Masken anwenden

---

## RICE Methodik - Überblick

**RICE** ist ein Priorisierungs-Framework, das vier Dimensionen objektiv bewertet:

### **Formel**

```
RICE Score = (Reach × Impact × Confidence) / Effort
```

**Interpretation:**
- **Höherer Score** = **Höhere Priorität**
- Score vergleicht Masken objektiv (Business Value vs. Aufwand)

### **Die 4 RICE-Dimensionen**

| Dimension | German One-Liner | Einheit |
|-----------|------------------|---------|
| **R** = Reach | "Wie viele Nutzer/Monat sind betroffen?" | Nutzer/Monat |
| **I** = Impact | "Wie stark verbessert sich deren Arbeit?" | 1-5 (Minimal → Massive) |
| **C** = Confidence | "Wie sicher sind unsere Schätzungen?" | 0-100% (Decimal: 0.3-1.0) |
| **E** = Effort | "Wie viel Aufwand kostet die Umsetzung?" | Person-Wochen |

---

## T-Shirt Sizing - Konvertierung zu Fibonacci

Alle RICE-Dimensionen (außer Confidence) verwenden **T-Shirt Größen**, die zu **Fibonacci-Zahlen** konvertiert werden:

| T-Shirt Size | Fibonacci | Verwendung |
|--------------|-----------|------------|
| **XS** | 1 | Sehr klein/gering |
| **S** | 2 | Klein |
| **M** | 3 | Mittel |
| **L** | 5 | Groß |
| **XL** | 8 | Sehr groß |

**Warum Fibonacci?**
- Nicht-lineare Skala (reflektiert Unsicherheit bei größeren Werten)
- Standard in agilen Methoden (Story Points)
- Verhindert Schein-Genauigkeit ("3.7" suggeriert falsche Präzision)

---

## R = Reach (Reichweite)

### **Was wird gemessen?**
Wie viele Nutzer verwenden diese Maske **mindestens einmal pro Monat**?

### **T-Shirt Skala**

| Größe | Nutzer/Monat | Fibonacci | Beschreibung | Beispiel |
|-------|--------------|-----------|--------------|----------|
| **XS** | < 10 | 1 | Seltene Admin-Maske | Jahresabschluss-Report (nur Controlling) |
| **S** | 10-50 | 2 | Abteilungs-spezifisch | Interne Buchhaltungsmaske |
| **M** | 50-100 | 3 | Regelmäßig genutzt | Fachmaske (bestimmte Produktlinie) |
| **L** | 100-200 | 5 | Häufig genutzt | Standard-Prozess (alle Sachbearbeiter) |
| **XL** | > 200 | 8 | Tägliche Kern-Maske | Kundensuche, Adressänderung (alle nutzen täglich) |

### **Leitfrage für WGV**
> "Wie viele Sachbearbeiter nutzen diese Maske mindestens einmal pro Monat?"

### **Tipp für Schätzung**
- Falls User Count unbekannt: Frage nach **Abteilungen** oder **Rollen** (z.B. "Alle Schadensbearbeiter" = ~50)
- Monatliche Nutzung zählt (nicht täglich)

---

## I = Impact (Geschäftswert)

### **Was wird gemessen?**
Wie stark verbessert die Migration die Arbeit der Nutzer? Business Value der Maske?

### **T-Shirt Skala**

| Größe | Beschreibung | Fibonacci | Merkmale | Beispiel |
|-------|--------------|-----------|----------|----------|
| **XS (Minimal)** | Nice-to-have, kaum Verbesserung | 1 | Selten genutzt, kein kritischer Prozess | Seltenes Report-Template |
| **S (Low)** | Kleine Verbesserung, Komfort | 2 | Datenpflege, einfache Änderungen | Adressänderung |
| **M (Medium)** | Wichtiger Workflow, spürbare Verbesserung | 3 | Standard-Geschäftsprozess | Kundensuche mit Filtern |
| **L (High)** | Geschäftskritischer Prozess | 5 | Revenue-relevant, häufig genutzt | Vertragsabschluss, Schadenanlage |
| **XL (Massive)** | Mission-critical, strategisch | 8 | Kernprozess, direkter Umsatz/Compliance-Einfluss | Tarifberechnung, Risiko-Prüfung |

### **Leitfragen für WGV**

1. "Wie wichtig ist dieser Prozess für das Tagesgeschäft?"
2. "Was passiert, wenn diese Maske 1 Tag ausfällt?"
3. "Beeinflusst die Maske direkt Umsatz, Kundenzufriedenheit oder Compliance?"
4. "Ist das ein Kern-Prozess oder Support-Prozess?"

### **Klassifikation nach Prozess-Typ**

| Impact | Prozess-Typ | Beispiel |
|--------|-------------|----------|
| **XL (8)** | Core Domain (Revenue/Compliance) | Vertragsabschluss, Schadensabwicklung, Tarifberechnung |
| **L (5)** | Core Domain (operativ kritisch) | Kundenanlage, Risikoprüfung |
| **M (3)** | Supporting Domain | Dokumentenverwaltung, Reporting |
| **S (2)** | Supporting Domain (Komfort) | Adressänderung, einfache Suche |
| **XS (1)** | Generic Subdomain | Admin-Tools, Config |

---

## C = Confidence (Sicherheit der Schätzung)

### **Was wird gemessen?**
Wie sicher sind wir mit unseren Schätzungen (Reach, Impact, Effort)?

### **T-Shirt Skala**

| Größe | Prozent | Decimal (für Formel) | Beschreibung | Merkmale |
|-------|---------|---------------------|--------------|----------|
| **XS (Very Low)** | < 30% | **0.3** | Komplett unbekannt | Keine Doku, kein Experte, Legacy-Code |
| **S (Low)** | 30-50% | **0.5** | Wenig Wissen | Nur 1 Experte, veraltete Doku, viele Annahmen |
| **M (Medium)** | 50-70% | **0.7** | Grundwissen vorhanden | Basis-Doku, 1-2 Experten, einige Unsicherheiten |
| **L (High)** | 70-90% | **0.8** | Gut dokumentiert | Mehrere Experten, ähnlich zu bekannten Masken |
| **XL (Very High)** | > 90% | **1.0** | Sehr gut verstanden | Exzellente Doku, viele Experten, niedrige Risiken |

### **Baseline: 70% (M = Medium)**

Start bei **M (0.7)**, dann adjustieren basierend auf Faktoren:

**Confidence wird REDUZIERT durch:**
- ❌ **Knowledge Risk**: Nur 1 Experte kennt die Maske (−20%)
- ❌ **Undokumentiert** oder veraltete Doku (−10%)
- ❌ **Externe Abhängigkeiten** (SAP, GDV, COR Life, etc.) (−10%)
- ❌ **Legacy-Code**, technische Schulden (−10%)
- ❌ **Keine Tests** vorhanden (−10%)

**Confidence wird ERHÖHT durch:**
- ✅ **Gut dokumentiert** (Prozess + Technik) (+10%)
- ✅ **Ähnlich zu ICIS+ Vaadin-Masken** (+10%)
- ✅ **Bereits migrierte Pattern** erkennbar (P1-P8) (+10%)
- ✅ **Mehrere Experten** verfügbar (+10%)
- ✅ **Einfache Schnittstellen**, keine externen Abhängigkeiten (+10%)

### **Leitfragen für WGV**

1. "Wie gut kennen wir diese Maske?"
2. "Ist sie dokumentiert (Prozess + Code)?"
3. "Wie viele Experten kennen sie?"
4. "Gibt es versteckte Komplexität oder Risiken?"
5. "Haben wir ähnliche Masken schon migriert?"

### **Beispiel-Adjustierung**

```
Baseline: 70% (M)

Maske: "Vertragsabschluss Neugeschäft"
- Nur 1 Experte (−20%) → 50%
- Externe Abhängigkeit zu SAP (−10%) → 40%
- Legacy-Code, technische Schulden (−10%) → 30%

→ Finale Confidence: S (0.5 = 50%)
```

---

## E = Effort (Aufwand)

### **Was wird gemessen?**
Wie viel **Person-Wochen** kostet die Migration (Frontend + Backend + Testing)?

### **T-Shirt Skala**

| Größe | Wochen | Fibonacci | Beschreibung | Typisches Pattern |
|-------|--------|-----------|--------------|-------------------|
| **XS** | 0.5w | 1 | Triviale Maske | Einfaches Lookup, Read-Only |
| **S** | 1w | 2 | Einfache CRUD-Maske | P1 (Simple CRUD), P2 (Search & Filter) |
| **M** | 2w | 3 | Standard-Maske mit Validation | P3 (Multi-Tab), P4 (Wizard), P7 (Report) |
| **L** | 4w | 5 | Komplexe Maske | P5 (Calculation-Heavy), P6 (Complex Workflow) |
| **XL** | 8w+ | 8 | Sehr komplex, Full Custom | P6, P8 (Conversational Candidate) |

### **Effort basiert auf 2×2 Complexity Matrix**

| Quadrant | UI Complexity | Logic Complexity | Typical Effort | Pattern |
|----------|---------------|------------------|----------------|---------|
| **Q1** | Simple | Simple | **S (1w)** oder **M (2w)** | P1, P2 |
| **Q2** | Complex | Simple | **M (2w)** oder **L (4w)** | P3 |
| **Q3** | Simple | Complex | **M (2w)** oder **L (4w)** | P5 |
| **Q4** | Complex | Complex | **L (4w)** oder **XL (8w+)** | P6, P8 |

### **Effort wird ERHÖHT durch (Multiplikatoren)**

| Faktor | Erhöhung | Beschreibung |
|--------|----------|--------------|
| **Multi-Domain** | +50% | Maske überschreitet Bounded Context-Grenzen |
| **Externe Integration** | +50% | SAP, COR Life, GDV, DMS, etc. |
| **Fehlende/Unvollständige SPs** | +30% | Mask-Funktionalität existiert, aber keine entsprechende SP → Neue SP nötig |
| **Custom UI Components** | +30% | Spezielle Widgets, nicht Standard-UI-Library |
| **SP-Orchestrierung** | +20% | Multiple SPs mit Business Logic koordinieren (war in Forms, jetzt Integration Layer) |
| **Komplexe Validierung** | +20% | Cross-Field-Validation, Business Rules Engine |

### **Beispiel-Berechnung mit Multiplikatoren**

```
Maske: "Vertragsabschluss mit Tarifberechnung"

Basis (Quadrant Q4): L (4w)
+ Multi-Domain (Vertrag + Tarif + Produkt): +50% → 6w
+ Externe Integration (SAP für Buchhaltung): +50% → 9w
+ Komplexe Validierung (Risiko-Checks): +20% → 10.8w

→ Effort: XL (8w+) → Fibonacci: 8
```

**Hinweis:** Runde auf nächste T-Shirt Size (hier: XL)

### **Leitfragen für WGV**

1. "In welchem Quadrant (Q1-Q4) ist die Maske?" (aus 2×2 Matrix)
2. "Gibt es externe Abhängigkeiten (SAP, COR Life, GDV)?"
3. "Existieren Stored Procedures für alle Mask-Funktionen?"
4. "Enthält die Forms-Maske Business Logic (Triggers, Blocks), die ins Integration Layer muss?"
5. "Gibt es Custom UI Components oder komplexe Validierungen?"
6. "Überschreitet die Maske Bounded Context-Grenzen?"

---

## Workshop-Nutzung: Schritt-für-Schritt

### **Phase 1: Qualitative Diskussion (T-Shirt Sizes)**

Für jede Maske (10-15 Kandidaten aus Tier 2):

**Schritt 1: Reach schätzen**
- Frage WGV: "Wie viele Nutzer/Monat?"
- Einigung auf T-Shirt Size: XS/S/M/L/XL

**Schritt 2: Impact schätzen**
- Frage WGV: "Wie wichtig ist der Prozess?" (Leitfragen siehe oben)
- Einigung auf T-Shirt Size: XS/S/M/L/XL

**Schritt 3: Effort schätzen**
- Basis: 2×2 Matrix Quadrant (Q1-Q4)
- Adjustierung: Multiplikatoren (Multi-Domain, Externe Integration, etc.)
- Einigung auf T-Shirt Size: XS/S/M/L/XL

**Schritt 4: Confidence adjustieren**
- Baseline: M (0.7 = 70%)
- Adjustierung: Knowledge Risk, Doku, Experten, etc. (siehe Faktoren oben)
- Einigung auf T-Shirt Size: XS/S/M/L/XL

**Dauer pro Maske:** ~1-2 Minuten

---

### **Phase 2: Konvertierung zu Fibonacci (für Berechnung)**

| Dimension | T-Shirt | Fibonacci/Decimal |
|-----------|---------|------------------|
| Reach | M | 3 |
| Impact | S | 2 |
| Confidence | L | 0.8 (80%) |
| Effort | S | 2 |

**RICE-Berechnung:**
```
RICE = (Reach × Impact × Confidence) / Effort
RICE = (3 × 2 × 0.8) / 2
RICE = 4.8 / 2
RICE = 2.4
```

---

### **Phase 3: Sortierung & Priorisierung**

Alle 10-15 Masken nach **RICE Score** sortieren (höchste zuerst):

| Rang | Mask ID | Name | Reach | Impact | Conf. | Effort | RICE | Quadrant | Pattern |
|------|---------|------|-------|--------|-------|--------|------|----------|---------|
| **1** | M001 | Vertragsabschluss | L (5) | L (5) | M (0.7) | L (5) | **3.5** | Q4 | P6 |
| **2** | M089 | Schadenanlage | M (3) | L (5) | S (0.5) | M (3) | **2.5** | Q3 | P5 |
| **3** | M042 | Adressänderung | M (3) | S (2) | L (0.8) | S (2) | **2.4** | Q1 | P1 |
| 4 | M123 | Partnersuche | L (5) | S (2) | L (0.8) | M (3) | 2.67 | Q1 | P2 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

**Top 3-5 = MVP-Kandidaten** (höchste RICE Scores)

---

### **Phase 4: Impact/Effort Matrix Visualisierung**

Nach RICE-Scoring: Platziere Masken auf **Impact/Effort Matrix** (für visuelle Bestätigung):

```
        High Impact
            │
     ┌──────┼──────┐
     │  ■   │  ●   │  ■ Strategic Projects (High Effort, High Impact)
     │ Strat│Quick │  ● Quick Wins (Low Effort, High Impact) ← MVP!
     │      │ Wins │  ▲ Fill-ins (Low Effort, Low Impact)
  ───┼──────┼──────┼─── (Effort)
     │      │      │  ✖ Avoid / Time Wasters (High Effort, Low Impact)
     │  ▲   │  ✖   │
     │ Fill │Avoid │
     └──────┴──────┘
            │
        Low Impact
```

**Zuordnung:**
- **Impact** = Reach × Impact (aus RICE)
  - High: RICE Impact ≥ M (3) UND Reach ≥ M (3)
  - Low: sonst
- **Effort** = Effort (aus RICE)
  - High: ≥ L (5)
  - Low: ≤ M (3)

**Beispiel-Platzierung:**

| Maske | Reach × Impact | Effort | Quadrant | MVP? |
|-------|----------------|--------|----------|------|
| M042 (Adressänderung) | M × S = Low | S (Low) | ✖ Avoid | **Nein** |
| M001 (Vertragsabschluss) | L × L = High | L (High) | ■ Strategic | **Ja** (Phase 2) |
| M089 (Schadenanlage) | M × L = High | M (Low) | ● Quick Win | **Ja** (MVP!) |

**RICE Score entscheidet finale Reihenfolge**, Impact/Effort Matrix ist visuelle Bestätigung.

---

## Beispiel-Tabelle (vollständig)

**10 repräsentative Masken** aus Tier 2, bewertet mit RICE:

| Rank | ID | Name | Reach | Impact | Conf | Effort | RICE | Q | Pattern | MVP? |
|------|----|------|-------|--------|------|--------|------|---|---------|------|
| **1** | M001 | Vertragsabschluss | L (5) | L (5) | M (0.7) | L (5) | **3.5** | Q4 | P6 | Phase 2 |
| **2** | M123 | Partnersuche | L (5) | S (2) | L (0.8) | M (3) | **2.67** | Q1 | P2 | **MVP** |
| **3** | M089 | Schadenanlage | M (3) | L (5) | S (0.5) | M (3) | **2.5** | Q3 | P5 | **MVP** |
| **4** | M042 | Adressänderung | M (3) | S (2) | L (0.8) | S (2) | **2.4** | Q1 | P1 | **MVP** |
| 5 | M067 | Tarifberechnung | S (2) | XL (8) | M (0.7) | L (5) | 2.24 | Q3 | P5 | Phase 2 |
| 6 | M201 | Multi-Tab Vertrag | L (5) | M (3) | M (0.7) | L (5) | 2.1 | Q2 | P3 | Backlog |
| 7 | M156 | Schadensbericht | M (3) | M (3) | L (0.8) | L (5) | 1.44 | Q2 | P7 | Backlog |
| 8 | M099 | Kundenanlage | M (3) | M (3) | S (0.5) | L (5) | 0.9 | Q4 | P6 | Backlog |
| 9 | M234 | Admin-Config | S (2) | XS (1) | XL (1.0) | S (2) | 0.5 | Q1 | P1 | Defer |
| 10 | M178 | Legacy Report | XS (1) | S (2) | S (0.5) | M (3) | 0.33 | Q1 | P7 | Sunset |

**MVP-Auswahl (Top 3-5):**
1. M123 (Partnersuche) - RICE 2.67
2. M089 (Schadenanlage) - RICE 2.5
3. M042 (Adressänderung) - RICE 2.4

**Strategic Projects (Phase 2):**
- M001 (Vertragsabschluss) - High Impact, High Effort
- M067 (Tarifberechnung) - XL Impact, High Effort

---

## Häufige Fragen (FAQs)

### **F1: Was, wenn WGV zwischen zwei T-Shirt Sizes schwankt?**

**A:** Wähle die **konservativere** (kleinere) Size bei Unsicherheit:
- Reach: Schwankung zwischen M und L → Wähle **M**
- Impact: Schwankung zwischen L und XL → Wähle **L**

**Rationale:** Vermeidet Überschätzung, Confidence adjustiert bereits für Unsicherheit.

---

### **F2: Was, wenn Reach sehr hoch, aber Impact niedrig ist (oder umgekehrt)?**

**A:** RICE balanciert automatisch:
- **High Reach, Low Impact** → Moderater Score (viele Nutzer, aber kleiner Effekt)
- **Low Reach, High Impact** → Moderater Score (wenige Nutzer, aber großer Effekt)

**Beispiel:**
- M042 (Adressänderung): Reach M (3), Impact S (2) → RICE 2.4
- M067 (Tarifberechnung): Reach S (2), Impact XL (8) → RICE 2.24

Beide ähnlich priorisiert, obwohl sehr unterschiedlich!

---

### **F3: Was, wenn Effort sehr hoch ist, aber auch Impact?**

**A:** Das sind **Strategic Projects** (hoher Business Value, hoher Aufwand):
- Nicht für MVP (Phase 1)
- Für Phase 2-3 einplanen
- Ggf. in kleinere Teile zerlegen (Strangler Fig)

**Beispiel:**
- M001 (Vertragsabschluss): Impact L (5), Effort L (5) → RICE 3.5 (höchster Score!)
- Trotzdem nicht MVP → zu riskant für Phase 1
- Stattdessen: Erst Quick Wins (M042, M089, M123) validieren, dann M001 in Phase 2

---

### **F4: Sollten wir T-Shirt Sizes oder Fibonacci-Zahlen in Miro zeigen?**

**A:** **Beide**:
- **Während Diskussion:** T-Shirt Sizes (intuitiver für WGV)
- **In RICE-Tabelle:** T-Shirt Size + Fibonacci in Klammern

**Beispiel-Tabelle:**
```
| Reach   | Impact  | Confidence | Effort  | RICE |
|---------|---------|------------|---------|------|
| M (3)   | S (2)   | L (0.8)    | S (2)   | 2.4  |
```

---

### **F5: Wie gehen wir mit Masken um, die AI-Substitution-Potential haben?**

**A:** RICE bewertet **aktuellen** Prozess, nicht AI-Ersatz:
- Wenn Maske durch AI ersetzt werden kann → **Effort = XS (1)** (nur Chatbot-Integration)
- Pattern = **P8 (Conversational Candidate)**
- RICE Score kann trotzdem hoch sein (High Impact, Low Effort)

**Aber:** AI-Substitution ist separate Entscheidung (nicht alle Prozesse können durch AI ersetzt werden)

**Empfehlung:**
1. RICE-Score beide Varianten:
   - **Variante A:** Migration als Forms (Pattern P1-P7)
   - **Variante B:** AI-Substitution (Pattern P8)
2. Vergleiche RICE Scores
3. Entscheidung: Whichever hat höheren RICE Score

---

## Referenzen

**Ergänzende Dokumente:**
- `/facilitation/tag1_maskenanalyse_guide.md` - Gesamte Maskenanalyse-Methodik (3-Tier Funnel)
- `/facilitation/tag1_maskenanalyse_fragenkatalog.md` - 26 Fragen für detaillierte Mask Assessment
- `/facilitation/tag1_masken_pattern_katalog.md` - 8 Migration Patterns (P1-P8)
- `/facilitation/decision_frameworks.md` - Weitere Frameworks (Impact/Effort Matrix, Cynefin, etc.)

**Externe Quellen:**
- RICE Framework: [Intercom Product Management Blog](https://www.intercom.com/blog/rice-simple-prioritization-for-product-managers/)
- T-Shirt Sizing: Agile Estimation Technique (Standard in Scrum/Kanban)

---

## Changelog

| Version | Datum | Änderung |
|---------|-------|----------|
| 1.0 | 2026-04-23 | Initial version - T-Shirt Sizing RICE für WGV Workshop |
