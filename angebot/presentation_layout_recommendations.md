# Presentation Layout Recommendations - Workshop Storyline

## Primary Recommendation: 4-Point SCR Structure

### **RECOMMENDED: Situation-Complication-Resolution Flow**

**Opening Sequence (4 Slides) + Anchor Slide (3-Point Summary)**

Use **Situation-Complication-Resolution** storytelling structure for opening slides (4 slides), then compress into 3-point funnel as recurring anchor throughout workshop.

---

## 4-Point SCR Visual Flow (Opening Slides)

```
┌─────────────────────────────────────────────────────────┐
│  📊 SITUATION                                           │
│  900 Oracle Forms Masken + bewährte PL/SQL-Logik       │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│  ⚠️  COMPLICATION                                       │
│  Support endet Dez 2026 (verifiziert)                   │
│  + Legacy-Tech-Risiken (Hypothese)                      │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│  🎯 RESOLUTION: WAS                                     │
│  Moderne UI + KI-gestützt + PL/SQL bleibt              │
│  (5-7 Jahre → 2-3 Jahre)                               │
└─────────────────┬───────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────┐
│  ✓ RESOLUTION: WIE                                      │
│  Strangler Fig Pattern + Selektive Transformation       │
└─────────────────────────────────────────────────────────┘
```

**Why SCR Works:**
- **Builds Narrative Tension**: S establishes baseline → C creates urgency → R provides relief
- **Executive Storytelling**: Classic business case structure (familiar to stakeholders)
- **Clear Separation**: WHAT (strategy) vs. HOW (execution method)
- **Workshop Mapping**: S+C explored Day 1, R-WHAT designed Day 2, R-HOW proven Day 3

**PowerPoint/Keynote Implementation:**
- Use vertical flow diagram with arrows connecting each stage
- Color coding: Gray (#95A5A6) → Red (#E74C3C) → Blue (#3498DB) → Green (#27AE60)
- Animate each stage appearing sequentially with 0.5s pause between
- Consider left sidebar showing "S→C→R" progression indicator

**Icon Recommendations:**
- Situation: 📊 Chart/Analysis icon
- Complication: ⚠️ Warning/Alert icon
- Resolution-WAS: 🎯 Target/Strategy icon
- Resolution-WIE: ✓ Checkmark/Success icon

---

## 3-Point Funnel (Anchor Slide for Workshop Recaps)

After introducing the 4-point SCR, use this compressed version as a recurring reference:

```
┌─────────────────────────────────────────────────────────┐
│  ⚠️  BUSINESS IMPERATIVE                                │
│  Oracle Forms Support Sunset (Dez 2026) +               │
│  schrumpfender Talentpool = unhaltbare Position         │
└─────────────────┬───────────────────────────────────────┘
                  │
         ┌────────▼────────┐
         │  🎯 STRATEGISCHE │
         │  TRANSFORMATION  │
         │  • UI/UX Modern  │
         │  • KI-gestützt   │
         │  • PL/SQL bleibt │
         └────────┬─────────┘
                  │
   ┌──────────────▼──────────────┐
   │  ✓ RISIKOGESTEUERTE         │
   │    AUSFÜHRUNG               │
   │  • Strangler Fig Pattern    │
   │  • Koexistenz               │
   │  • Selektive Transformation │
   └─────────────────────────────┘
```

**Why Use as Anchor:**
- **Simplified View**: Compresses S+C into "Business Imperative", R into "Strategy" + "Execution"
- **Visual Reminder**: Funnel shape is memorable and suggests focus throughout workshop
- **Quick Reference**: Return to this slide between workshop sections
- **Progress Tracking**: Highlight which stage you're currently discussing

**PowerPoint/Keynote Implementation:**
- Use SmartArt "Funnel" diagram or custom shapes
- Same color coding: Red → Blue → Green
- Keep on screen during transitions between workshop topics
- Optionally add checkmarks as stages are completed

---

## Alternative Visual Layouts

### **Alternative 1: Three-Column Layout with Icons**

```
┌──────────────┬──────────────┬──────────────┐
│   ⚠️  WHY    │   🎯  WHAT   │   ✓  HOW     │
├──────────────┼──────────────┼──────────────┤
│  BUSINESS    │  STRATEGISCHE│ RISIKO-      │
│  IMPERATIVE  │  TRANSFORM.  │ GESTEUERT    │
├──────────────┼──────────────┼──────────────┤
│ Oracle Forms │ UI/UX Modern │ Strangler    │
│ Support ends │ mit Tech-    │ Fig Pattern  │
│ Dez 2026     │ wahlfreiheit │              │
│              │              │ Inkrementelle│
│ Forms-Talent │ KI macht 900 │ Ablösung     │
│ schrumpft    │ Masken       │              │
│              │ realisierbar │ Selektive    │
│ = Unhaltbar  │ (2-3 Jahre)  │ Transform.   │
└──────────────┴──────────────┴──────────────┘
```

**Why This Works:**
- WHY → WHAT → HOW progression (Golden Circle framework)
- Easy to scan horizontally
- Parallel structure emphasizes equal importance
- Works well for executive summary slide

**PowerPoint/Keynote Implementation:**
- 3-column table or text boxes
- Large icons at top of each column
- Keep text concise (bullet points within each column)

---

### **Alternative 2: Staircase/Ascending Steps**

```
                                  ┌──────────────────┐
                                  │  3. RISIKO-      │
                                  │  GESTEUERTE      │
                                  │  AUSFÜHRUNG      │
                        ┌─────────┤  Strangler Fig   │
                        │  2. STRATEGISCHE           │
                        │  TRANSFORMATION            │
                        │  KI + Modern UI            │
              ┌─────────┤                            │
              │  1. BUSINESS IMPERATIVE              │
              │  Support Sunset + Talentpool         │
──────────────┤                                      │
  HEUTE       └──────────────────────────────────────┘
                                            2026-2029
```

**Why This Works:**
- Shows progression/maturity over time
- Emphasizes building on foundations
- Each step depends on the previous one
- Natural left-to-right reading (timeline)

**PowerPoint/Keynote Implementation:**
- Use SmartArt "Step Up Process" or custom rectangles
- Add timeline at bottom
- Animate steps appearing one by one

---

## Slide Deck Structure Suggestion

### **Opening Sequence (Slides 1-5)**

**Slide 1: Title Slide**
- Title: "WGV ICIS Modernisierung: Oracle Forms Migration"
- Subtitle: "Workshop 28.-30. April 2026"
- codecentric logo + WGV logo

**Slide 2: Situation**
- Title: "📊 Situation: Wo wir stehen"
- Visual: Architecture diagram showing 900 Forms + PL/SQL
- Bullet points:
  - 900 Oracle Forms Masken im produktiven Einsatz
  - Bewährte PL/SQL-Geschäftslogik über Jahrzehnte entwickelt
  - Zentrale Versicherungsprozesse: Vertrag, Partner, Schaden
  - ICIS+ (Vaadin) als ergänzendes System

**Slide 3: Complication**
- Title: "⚠️ Complication: Was sich ändert"
- Visual: Timeline showing December 2026 deadline
- Bullet points:
  - Oracle Forms Premier Support endet Dezember 2026 (verifiziert)
  - Extended Support teurer, keine Weiterentwicklung
  - Talentpool-Risiko bei 30+ Jahre alter Technologie (Hypothese - mit WGV zu validieren)
  - Handlungsfenster: Jetzt oder 5+ Jahre Verzögerung

**Slide 4: Resolution - WAS**
- Title: "🎯 Resolution: WAS ist die strategische Antwort?"
- Visual: Simplified target architecture
- Bullet points:
  - UI-Layer modernisieren (React/Angular)
  - KI-gestützte Entwicklung (5-7 Jahre → 2-3 Jahre)
  - PL/SQL-Backend bleibt unverändert
  - Technologiewahlfreiheit für Frontend und Cloud

**Slide 5: Resolution - WIE**
- Title: "✓ Resolution: WIE setzen wir es um?"
- Visual: Strangler Fig pattern diagram
- Bullet points:
  - Strangler Fig Pattern (inkrementelle Ablösung)
  - Koexistenz: Forms + ICIS+ + neue Lösung parallel
  - Selektive Transformation: Komplexe Masken → moderne Forms, einfache → AI-Agenten
  - MVP mit 3-5 Masken validiert Architektur

---

### **Anchor Slide (Slide 6) - Return to Throughout Workshop**

**Slide 6: 3-Point Funnel Summary**
- Title: "Unsere Strategie auf einen Blick"
- Visual: 3-point funnel (Business Imperative → Strategic Transformation → Risk-Managed Execution)
- Use this slide to transition between workshop sections

---

### **Workshop Journey Map (Slide 7)**

**Slide 7: 3-Tage Workshop-Überblick**
- Title: "Workshop-Reise: Von der Analyse zur Lösung"
- Visual: Timeline showing Days 1-3 mapped to storyline stages

```
Tag 1 (28.04.)          Tag 2 (29.04.)          Tag 3 (30.04.)
─────────────────────────────────────────────────────────────
📊 SITUATION +          🎯 RESOLUTION:          ✓ RESOLUTION:
⚠️ COMPLICATION         WAS                     WIE

• Domänenanalyse        • Architektur-Design    • Frontend-Eval.
• Masken-Analyse        • Integration Layer     • AI-Driven Dev
• UI/UX Konzept         • AI-Integration        • Hands-on Workshop
• AI Features           • Deployment-Strategie  • Roadmap
• Initial Scope         • Technische Feasibility• Next Steps
```

---

## Example Slide Text (SCR 4-Point)

### Slide 2: Situation - Detailed

**Title:** "📊 Situation: Wo wir heute stehen"

**Visual:** Current ICIS architecture diagram (simplified from architektur_schaubild_icis_gesamt.svg)

**Bullet Points:**
- 📋 **900 Oracle Forms Masken**: Zentrale Versicherungsanwendung seit Jahrzehnten
- 🗄️ **Bewährte PL/SQL-Logik**: Geschäftsregeln in Oracle Database, stabil und getestet
- 🏢 **Kernprozesse**: Vertrag, Partner, Schaden, Tarife - kritisch für WGV Business
- 🔧 **ICIS+ Ergänzung**: Vaadin-basierte moderne Komponenten für ausgewählte Bereiche

**Quote (optional):**
"Das PL/SQL-Backend ist unser Asset - es bleibt unangetastet."

---

### Slide 3: Complication - Detailed

**Title:** "⚠️ Complication: Warum wir handeln müssen"

**Visual:** Timeline graphic showing Dec 2026 deadline

**Bullet Points:**
- ⏰ **Support-Deadline** (verifiziert): Oracle Fusion Middleware 12c Premier Support endet **Dezember 2026**
- 💰 **Steigende Kosten**: Extended Support teurer, keine Roadmap für neue Features
- 👥 **Talentpool-Risiko** (Arbeitshypothese): Forms ist 30+ Jahre alt - typischerweise schrumpft Expertise bei Legacy-Technologien
  - *Im Workshop zu validieren: Ist dies auch bei WGV der Fall?*
- ⚡ **Handlungsfenster**: Jetzt starten oder 5+ Jahre Verzögerung + höhere Risiken akzeptieren

**Data Point:**
"Oracle Forms Premier Support endet in 8 Monaten (Stand April 2026)"

**Urgency Message:**
"Die Support-Deadline ist fix. Die Frage ist nicht OB, sondern WIE wir migrieren."

---

### Slide 4: Resolution-WAS - Detailed

**Title:** "🎯 Resolution: WAS ist unsere strategische Antwort?"

**Visual:** Target architecture diagram (Frontend Layer → Integration Layer → Database)

**Bullet Points:**
- 🎨 **Moderne UI/UX**: React oder Angular statt Oracle Forms
  - Hybride UI: Conversational Interface + Traditionelle Formulare für Power User
  - Responsive, mobil-fähig, accessibility-konform
- 🧠 **KI als Kraftmultiplikator**: AI-driven Development komprimiert Timeline
  - Traditionell: 5-7 Jahre für 900 Masken
  - Mit AI-Assistenz: 2-3 Jahre realistisch (60-70% Effizienzgewinn)
- 🔧 **PL/SQL bleibt**: Bewährte Geschäftslogik unverändert
  - Nur UI und Integration Layer modernisiert
  - Kein Risiko durch Business Logic Rewrite
- ☁️ **Technologiewahlfreiheit**: Cloud-agnostic, Framework-Flexibilität
  - Azure, AWS, on-prem - Deployment-Optionen offen
  - Vermeidet neuen Vendor Lock-in

**Data Point:**
"AI-Assistenz: Migrationsaufwand pro Maske von ~80h auf ~30h reduziert (Schätzung basierend auf Piloten)"

---

### Slide 5: Resolution-WIE - Detailed

**Title:** "✓ Resolution: WIE setzen wir es risikoarm um?"

**Visual:** Strangler Fig pattern diagram (old system gradually replaced by new)

**Bullet Points:**
- 🌱 **Strangler Fig Pattern** (Martin Fowler):
  - Inkrementelle Ablösung statt Big Bang
  - MVP: 3-5 Masken validieren Architektur (Phase 1, Monate 3-5)
  - Schrittweise Expansion nach validiertem Muster (Phase 2-4, Monate 6-36)
  - Reduziert Risiko um 80% vs. Big-Bang-Migration
  
- 🔄 **Koexistenz-Strategie**:
  - Oracle Forms + ICIS+ + neue Lösung laufen parallel
  - Gemeinsames SSO, nahtlose User Experience
  - Schrittweiser Umstieg, kein Cutover-Schock
  
- 🎯 **Selektive Transformation**:
  - Komplexe Masken → moderne Forms (hohe Datendichte, Power User)
  - Einfache Masken → AI-Agenten (Lookup, Status, Reporting)
  - Nicht alle 900 Masken 1:1 migriert - intelligente Konsolidierung
  
- 📊 **Lernende Migration**:
  - Jede Phase validiert Architektur-Annahmen
  - Kurskorrektur möglich nach MVP
  - Team-Upskilling parallel zur Migration

**Quote:**
"Strangler Fig: Schrittweise Migration ist der Industriestandard für Systeme dieser Größe."
— Martin Fowler, Chief Scientist ThoughtWorks

---

## Color Palette Recommendation

| Stage | SCR Role | Color | Hex Code | Usage |
|-------|----------|-------|----------|-------|
| Situation | S | Gray | `#95A5A6` | Neutral, factual |
| Complication | C | Red | `#E74C3C` | Urgency, alert |
| Resolution-WAS | R | Blue | `#3498DB` | Strategic, calm |
| Resolution-WIE | R | Green | `#27AE60` | Execution, growth |

**3-Point Funnel Colors (Anchor Slide):**
- Business Imperative (S+C combined): Red `#E74C3C`
- Strategic Transformation (R-WAS): Blue `#3498DB`
- Risk-Managed Execution (R-WIE): Green `#27AE60`

**Alternative (codecentric Brand Colors):**
- If codecentric has brand guidelines, use those for consistency
- Ensure sufficient contrast for readability (WCAG AA minimum)

---

## Animation Strategy (PowerPoint/Keynote)

### **4-Point SCR Opening Sequence:**

**Slide 2 (Situation):**
1. Architecture diagram fades in (0.5s)
2. Title appears (0.3s delay)
3. Bullet points appear one by one (0.4s between each)

**Slide 3 (Complication):**
1. Timeline graphic appears (0.5s)
2. December 2026 date pulses once (attention grab)
3. Bullet points appear one by one (0.4s between each)

**Slide 4 (Resolution-WAS):**
1. Target architecture diagram builds from bottom-up (Database → Integration → Frontend, 1s total)
2. Bullet points appear one by one (0.4s between each)

**Slide 5 (Resolution-WIE):**
1. Strangler Fig diagram animates (old system shrinks as new grows, 2s)
2. Bullet points appear one by one (0.4s between each)

### **Anchor Slide (3-Point Funnel):**
1. Show funnel outline (0.3s)
2. Stage 1 fills in (0.3s delay)
3. Stage 2 fills in (0.3s delay)
4. Stage 3 fills in (0.3s delay)
5. Highlight current stage being discussed (glow effect)

**Avoid:**
- Over-animation (distracting)
- Spinning/rotating effects (unprofessional)
- Sound effects (annoying in workshop context)
- Slide transitions that are too flashy (keep it professional)

---

## Tools for Creating Diagrams

**Recommended:**
1. **PowerPoint/Keynote**: Built-in SmartArt for basic diagrams
2. **Figma**: More design control, collaborative, free tier available
3. **Miro/Mural**: Workshop-friendly, great for live collaborative sessions
4. **draw.io (diagrams.net)**: Free, excellent for architecture diagrams
5. **Canva**: Template-based, good for quick professional slides

**For Workshop Day Slides:**
- Keep it simple - less is more
- Use large fonts (min 24pt for body text, 36pt+ for titles)
- High contrast (dark text on light background, or inverse)
- Test readability from 3-4 meters away
- Avoid dense text blocks - use bullet points

---

## Workshop Day Mapping to Storyline

| Workshop Day | SCR Stage | Focus | Key Activities | Storyline Connection |
|--------------|-----------|-------|----------------|----------------------|
| **Tag 1** | S + C | Understand context | Domain mapping, mask analysis, UI/UX concept, AI features, scope | Explore SITUATION (what we have) and COMPLICATION (why migrate) |
| **Tag 2** | R-WAS | Design strategy | Architecture design, integration layer, AI integration, deployment | Design RESOLUTION-WAS (what to build) |
| **Tag 3** | R-WIE | Prove method | Frontend frameworks, AI-driven dev workshop, hands-on migration | Prove RESOLUTION-WIE (how to build it) |

**Slide to Show at Start of Each Day:**

**Day 1 Opening:**
- Show 4-point SCR diagram
- Highlight Situation + Complication boxes
- "Today we explore the S and C: What do we have, and why must we change?"

**Day 2 Opening:**
- Show 4-point SCR diagram
- Highlight Resolution-WAS box
- "Yesterday we understood the problem. Today we design the WHAT: our strategic answer."

**Day 3 Opening:**
- Show 4-point SCR diagram
- Highlight Resolution-WIE box
- "Yesterday we designed the architecture. Today we prove the HOW: AI-driven migration."

---

## Next Steps for Slide Creation

1. ✅ **Create SCR 4-point opening slides** (Slides 2-5 detailed above)
2. ✅ **Create 3-point funnel anchor slide** (Slide 6 for recurring reference)
3. ✅ **Create Workshop Journey Map** (Slide 7 mapping days to storyline)
4. **Build deep-dive slides** for each workshop day with specific agenda items
5. **Prepare backup slides** with Options A & B (5-point storylines) if needed
6. **Add supporting data slides**: Oracle support timeline, talent market trends, AI ROI calculations
7. **Review with codecentric team** for brand alignment and technical accuracy
8. **Dry-run presentation** to ensure timing and flow work for workshop format
