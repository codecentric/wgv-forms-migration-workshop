# Miro Board Structure - WGV ICIS Workshop

## Workshop Design Philosophy

**Time-Constrained, High-Interaction Format:**
- Minimize presentation slides (read-only content)
- Maximize collaboration frames (capture WGV input)
- Use comparison frameworks to structure discussions
- Document decisions and insights in real-time

**Two Frame Types:**
1. **INPUT Frames**: Comparison matrices, frameworks, reference materials (codecentric presents)
2. **CAPTURE Frames**: Templates for documenting WGV's responses, decisions, ideas (WGV + codecentric collaborate)

---

## Miro Board Structure Overview

### **Board 1: Storyline & Context (Opening - Day 0/1)**
- Frame 1: SCR 4-Point Storyline (INPUT - read once, then anchor)
- Frame 2: Workshop Journey Map (INPUT - orientation)

### **Board 2: Tag 1 - Discovery & Scoping**
- Frame 3: Domain Map (CAPTURE - Event Storming Lite results)
- Frame 4: Mask Analysis - Three-Tier Funnel (CAPTURE - 2×2 Matrix, RICE Scoring, Pattern Matching → 3-5 MVP masks)
- Frame 5: UI/UX Patterns Comparison (INPUT + CAPTURE hybrid)
- Frame 6: AI Features Brainstorm (CAPTURE - sticky notes)
- Frame 7: Initial Scope Decision (CAPTURE - voting + rationale)

### **Board 3: Tag 2 - Architecture & Technology**
- Opening: Recap Tag 1 & Scope refinement (10 min verbal, no dedicated frame)
- Frame 7.5: Migration Strategy - Strangler Fig Validation (HYBRID - codecentric recommendation + WGV objections/additions)
- Frame 8: Services/SP Overview + Integration Layer Comparison (HYBRID - WGV presents SPs, codecentric presents tech comparison)
- Frame 9: Technical Feasibility + Integration Layer Decision (CAPTURE - MVP mask assessment + decision + ADR)
- Frame 10: Deployment Options Comparison (INPUT - VMs, Docker, K8s, ACA)
- Frame 11: Deployment Decision (CAPTURE - decision + ADR)
- Frame 12: Architecture Diagram Canvas (CAPTURE - collaborative drawing)
- Frame 13: AI Integration Patterns (HYBRID - 4 patterns + decision)

### **Board 4: Tag 3 - Frontend & AI-Driven Dev**
- Frame 14: Frontend Framework Comparison (INPUT - React vs. Angular vs. other)
- Frame 15: Frontend Decision (CAPTURE - decision + ADR)
- Frame 16: AI-Driven Dev Workshop Space (CAPTURE - hands-on notes)
- Frame 17: Next Steps & Roadmap (CAPTURE - action items, timeline)

**Total: ~18 frames** (lean, focused)

---

## Detailed Frame Designs

---

## BOARD 1: Storyline & Context

### **Frame 1: SCR 4-Point Storyline (INPUT)**

**Purpose:** Set context, align on "why we're here"

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  WGV ICIS MODERNISIERUNG - WARUM DIESER WORKSHOP?          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  📊 SITUATION                                               │
│  └─ 900 Oracle Forms + bewährte PL/SQL-Logik               │
│                                                             │
│          ▼                                                  │
│                                                             │
│  ⚠️  COMPLICATION                                           │
│  └─ Support endet Dez 2026 (verifiziert) + Legacy-Risiken  │
│                                                             │
│          ▼                                                  │
│                                                             │
│  🎯 RESOLUTION: WAS                                         │
│  └─ Moderne UI + KI-gestützt + PL/SQL bleibt               │
│                                                             │
│          ▼                                                  │
│                                                             │
│  ✓ RESOLUTION: WIE                                          │
│  └─ Strangler Fig + Selektive Transformation               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- Use Miro sticky notes for each stage (large font)
- Arrows connecting stages
- Keep text minimal (this is shown once at start, then referenced)

**Time:** 5 minutes presentation

---

### **Frame 2: Workshop Journey Map (INPUT)**

**Purpose:** Orient participants on 3-day agenda - preview of expected outputs (actual outputs created in later CAPTURE frames)

**Layout:**
```
┌──────────────┬──────────────┬──────────────┐
│  TAG 1       │  TAG 2       │  TAG 3       │
│  28.04.      │  29.04.      │  30.04.      │
├──────────────┼──────────────┼──────────────┤
│ 📊 SITUATION │ 🎯 RESOLUTION│ ✓ RESOLUTION │
│ ⚠️ COMPLIC.  │    WAS       │    WIE       │
├──────────────┼──────────────┼──────────────┤
│ Domäne       │ Architektur  │ Frontend     │
│ Masken       │ Integration  │ AI-Driven Dev│
│ UI/UX        │ AI Gateway   │ Hands-on     │
│ AI Features  │ Deployment   │ Roadmap      │
│ Scope        │ Diagramm     │              │
├──────────────┼──────────────┼──────────────┤
│ OUTPUT:      │ OUTPUT:      │ OUTPUT:      │
│ • ICIS/ICIS+ │ • Architektur-│ • Frontend   │
│   Verständnis│   diagramm   │   Tech-Stack │
│ • Domänenkarte│ • Integration-│ • Validierter│
│ • 3-5 Masken │   Layer-     │   KI-Workflow│
│   + Migrations│  Entscheid. │ • Roadmap   │
│   ansätze    │ • API-Standards│   (Entwurf)  │
│ • UX Konzept │ • Deployment │              │
│              │   Konzept    │              │
└──────────────┴──────────────┴──────────────┘
```

**Miro Elements:**
- 3-column layout (one per day)
- Color-coded by storyline stage
- Expected outputs clearly listed

**Time:** 3 minutes presentation

---

## BOARD 2: Tag 1 - Discovery & Scoping

### **Frame 3: Domain Map (CAPTURE)**

**Purpose:** Capture Event Storming Lite results and identify bounded contexts within icis-forms

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  DOMÄNENKARTE - WGV ICIS                                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┏━━━━━━━━━━━━━━━━━━ LEITFRAGE ━━━━━━━━━━━━━━━━━━┓        │
│  ┃                                                 ┃        │
│  ┃  "Innerhalb der ~900 ICIS-Forms-Masken:        ┃        │
│  ┃   Welche fachlichen Domänen existieren,        ┃        │
│  ┃   und wie können wir sie voneinander           ┃        │
│  ┃   abgrenzen?"                                   ┃        │
│  ┃                                                 ┃        │
│  ┃  WHY: icis-forms ist EIN technisches System,   ┃        │
│  ┃  das MEHRERE Geschäftsdomänen abdeckt.         ┃        │
│  ┃  Wir brauchen fachliche Grenzen für die        ┃        │
│  ┃  schrittweise Migration.                       ┃        │
│  ┃                                                 ┃        │
│  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛        │
│                                                             │
│  BOUNDED CONTEXTS:                                          │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │  VERTRAG    │  │   PARTNER   │  │   SCHADEN   │        │
│  │             │  │             │  │             │        │
│  │ [sticky]    │  │ [sticky]    │  │ [sticky]    │        │
│  │ [notes]     │  │ [notes]     │  │ [notes]     │        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
│                                                             │
│  WEITERE KONTEXTE:                                          │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │             │  │             │  │             │        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
│                                                             │
│  INTEGRATIONEN (extern):                                    │
│  [SAP] [COR Life] [GDV] [DMS] [andere...]                  │
│                                                             │
│  ERKENNUNGSMERKMALE (Kriterien für Bounded Contexts):      │
│  • Prozess-Gruppierung (Vertrag vs. Schaden vs. Kunde)     │
│  • Produktlinien (Leben vs. KFZ vs. Sach/Haftpflicht)      │
│  • Datenbank-Schema-Cluster (welche Tabellen gehören wo)   │
│  • Team-Ownership (wer ist verantwortlich)                 │
│  • Externe Integrationen (wer nutzt welches System)        │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  INFORMATION ARCHITECTURE (HIGH-LEVEL):                     │
│                                                             │
│  CORE ENTITIES & BEZIEHUNGEN:                               │
│  ┌──────────┐                                               │
│  │  KUNDE   │ (Master: Partner Context)                     │
│  └────┬─────┘                                               │
│       │                                                     │
│       ├─→ VERTRAG (Master: Vertrag Context, 1:N)           │
│       │   └─→ SCHADEN (Master: Schaden Context, 1:M)       │
│       │                                                     │
│       └─→ PARTNER (Master: Partner Context, M:N)           │
│                                                             │
│  SHARED DATA (über alle Contexts):                          │
│  • ADRESSE, BANKVERBINDUNG, DOKUMENT, PRODUKTKATALOG        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- **LEITFRAGE Box**: Prominent displayed at top (use colored frame/shape)
- Empty boxes for bounded contexts (filled during workshop)
- Sticky notes for key domain events
- Arrows/connections between contexts
- Color coding: Core domains (orange), Supporting (blue), Generic (gray)
- Criteria checklist at bottom (helps guide discussion)
- **Information Architecture Diagramm**: Entity boxes with relationship arrows, Shared Data highlighted

**Facilitator Input:**
- Use `/facilitation/tag1_domain_mapping_guide.md` to guide discussion
- **Use `/facilitation/bounded_context_discovery_questionnaire.md` as structured interview guide**
  - **Kategorie 2.2 (Information Architecture)**: Dokumentiere Core Entities, Beziehungen, Shared Data
- Activity: Event Storming Light (~45-60min)
- Activity: Context Mapping (~30-45min)
- Activity: Bounded Context Discovery (~60-90min)
  - **Inkludiert: Information Architecture Mapping (~15-20min innerhalb Kategorie 2)**
- **Note:** These sub-activities are included within the total time below

**Key Insight to Communicate:**
The architecture diagrams (`architektur_schaubild_icis_gesamt.svg`, `icis_oracle_forms_architektur.svg`) show **technical structure**, not business domain boundaries. The ~900 icis-forms masks are one monolithic technical component that likely spans multiple bounded contexts. We need WGV's domain expertise to discover these boundaries. **Information Architecture** (Entity-Beziehungen) hilft, sowohl fachliche als auch technische System-Grenzen zu verstehen.

**Time:** ~2.5 hours (150 min) - aligned with committed agenda "Domäne erkennen & ICIS-System Verständnis" (2h) + vollständiger ICIS Deep Dive aus Facilitation Guide

---

### **Frame 4: Mask Analysis - Three-Tier Funnel (CAPTURE)**

**Purpose:** Apply systematic methodology to select 3-5 MVP masks from ~900 using 2×2 Complexity Matrix, RICE Scoring, and Pattern Matching

**Note:** This frame captures the output of the three-tier funnel approach from `/facilitation/tag1_maskenanalyse_guide.md`

**Layout:**
```
┌──────────────────────────────────────────────────────────────────────────────────┐
│  MASKEN-ANALYSE: DREI-STUFEN-TRICHTER                                            │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  TIER 1: QUICK CATEGORIZATION (~20-25min)                                       │
│  900 Masken → ~50-80 Kandidaten (Filter: Frequency, User Count, Critical, Active)│
│                                                                                  │
│  📊 FILTER RESULTS:                                                              │
│  [Text box: "Nach Filtern: X Masken übrig"]                                     │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│  TIER 2: PATTERN-BASED SAMPLING (~25-30min)                                     │
│  ~50-80 → 10-15 Representative (Clustering: Bounded Context × 2×2 Matrix)       │
│                                                                                  │
│  ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ │
│  ┃  2×2 COMPLEXITY MATRIX - BOUNDED CONTEXT CLUSTERING                       ┃ │
│  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ │
│                                                                                  │
│                    LOGIC COMPLEXITY                                              │
│                          │                                                       │
│              ┌───────────┼───────────┐                                           │
│              │  Q2       │    Q4     │                                           │
│         UI   │ UI-Heavy  │  Full     │  Q1: Quick Wins (Simple UI + Logic)      │
│              │           │  Custom   │  Q2: UI-Heavy (Complex UI + Simple Logic)│
│      C    ───┼───────────┼───────────┼─ Q3: Logic-Heavy (Simple UI + Complex)   │
│      o       │  Q1       │    Q3     │  Q4: Full Custom (Complex UI + Logic)    │
│      m       │ Quick     │  Logic-   │                                           │
│      p       │ Wins      │  Heavy    │                                           │
│      l       │           │           │                                           │
│      e       └───────────┴───────────┘                                           │
│      x             │                                                             │
│      i       Simple      Complex                                                 │
│      t                                                                           │
│      y                                                                           │
│                                                                                  │
│  MASKEN-CLUSTERING (Sticky Notes auf Matrix platzieren):                        │
│                                                                                  │
│  Bounded Context: VERTRAG                                                       │
│  • [Maske 1] → Q1 | [Maske 2] → Q2 | [Maske 3] → Q4                            │
│                                                                                  │
│  Bounded Context: SCHADEN                                                       │
│  • [Maske 4] → Q1 | [Maske 5] → Q3 | [Maske 6] → Q4                            │
│                                                                                  │
│  Bounded Context: KUNDE/PARTNER                                                 │
│  • [Maske 7] → Q1 | [Maske 8] → Q2                                             │
│                                                                                  │
│  [Weitere Bounded Contexts...]                                                  │
│                                                                                  │
│  📋 REPRÄSENTATIVE AUSWAHL: 10-15 Masken (1-2 pro Zelle)                        │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│  TIER 3: RICE SCORING DEEP DIVE (~15-20min)                                     │
│  10-15 → 3-5 MVP-Kandidaten                                                     │
│                                                                                  │
│  ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ │
│  ┃  RICE SCORING TABLE                                                        ┃ │
│  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ │
│                                                                                  │
│  ┌──────────┬────────┬──────┬────────┬──────────┬──────┬──────┬─────────┬────┐ │
│  │ Mask ID  │ Name   │Reach │Impact  │Confidence│Effort│ RICE │Quadrant │Pat-│ │
│  │          │        │(User/│(1-5)   │(%)       │(weeks│Score │(Q1-Q4)  │tern│ │
│  │          │        │month)│        │          │)     │      │         │    │ │
│  ├──────────┼────────┼──────┼────────┼──────────┼──────┼──────┼─────────┼────┤ │
│  │ M001     │[Name]  │      │        │          │      │      │ Q1      │ P1 │ │
│  ├──────────┼────────┼──────┼────────┼──────────┼──────┼──────┼─────────┼────┤ │
│  │ M042     │[Name]  │      │        │          │      │      │ Q1      │ P1 │ │
│  ├──────────┼────────┼──────┼────────┼──────────┼──────┼──────┼─────────┼────┤ │
│  │ M089     │[Name]  │      │        │          │      │      │ Q4      │ P6 │ │
│  ├──────────┼────────┼──────┼────────┼──────────┼──────┼──────┼─────────┼────┤ │
│  │ ...      │        │      │        │          │      │      │         │    │ │
│  └──────────┴────────┴──────┴────────┴──────────┴──────┴──────┴─────────┴────┘ │
│                                                                                  │
│  **RICE Formula:** (Reach × Impact × Confidence) / Effort                       │
│                                                                                  │
│  **Effort Estimation Guidance (based on 2×2 Matrix):**                          │
│  • Q1 (Simple/Simple): 1-2 weeks                                                │
│  • Q2 (Complex UI/Simple): 2-3 weeks                                            │
│  • Q3 (Simple/Complex Logic): 2-3 weeks                                         │
│  • Q4 (Complex/Complex): 4-8 weeks                                              │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│  PATTERN CATALOG MATCHING (P1-P8)                                               │
│                                                                                  │
│  ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ │
│  ┃  8 MIGRATIONS-PATTERNS (codecentric Vorschlag)                            ┃ │
│  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ │
│                                                                                  │
│  ┌─────┬───────────────────┬──────────┬─────────────────────┬─────────────┐    │
│  │ ID  │ Pattern Name      │ Quadrant │ Migrations-Ansatz   │ Aufwand     │    │
│  ├─────┼───────────────────┼──────────┼─────────────────────┼─────────────┤    │
│  │ P1  │ Simple CRUD       │ Q1       │ React/Angular (AI)  │ 1-2w        │    │
│  │ P2  │ Search & Filter   │ Q1/Q2    │ React + Data Grid   │ 1-2w        │    │
│  │ P3  │ Multi-Tab Form    │ Q2       │ React/Angular (Tabs)│ 2-3w        │    │
│  │ P4  │ Wizard Workflow   │ Q1-Q3    │ React (Stepper)     │ 2-4w        │    │
│  │ P5  │ Calculation-Heavy │ Q3       │ Integration-Layer-First │ 2-3w    │    │
│  │ P6  │ Complex Workflow  │ Q4       │ Full Custom (AI)    │ 4-8w        │    │
│  │ P7  │ Report Generator  │ Q1       │ React + Template    │ 2-3w        │    │
│  │ P8  │ Conversational    │ Q4       │ Chatbot + Form      │ 4-8w        │    │
│  └─────┴───────────────────┴──────────┴─────────────────────┴─────────────┘    │
│                                                                                  │
│  📌 PATTERN-MATCHING WORKFLOW:                                                  │
│  1. 2×2 Matrix klassifiziert → Quadrant (Q1-Q4)                                │
│  2. Pattern-Matching innerhalb Quadrant → Konkreter Ansatz (P1-P8)             │
│  3. Pattern → Automatisch: Technology Stack + Aufwand                           │
│                                                                                  │
│  ⚡ MIGRATIONS-VARIANTE: P3 kann auch inkrementell migriert werden              │
│     • Phase 1: N × P1 (jeder Tab als separate Maske, schnellere Releases)      │
│     • Phase 2: P3-Integration (Tab-Navigation + koordinierte Transaktionen)     │
│     • Sinnvoll bei: 4+ Tabs, wenig Cross-Tab-Validierung, Time-to-Market-Druck │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────┤
│  IMPACT/EFFORT MATRIX - QUICK WINS VISUALISIERUNG                               │
│                                                                                  │
│  ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ │
│  ┃  QUICK WINS IDENTIFIKATION                                                 ┃ │
│  ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ │
│                                                                                  │
│        High Impact                                                               │
│            │                                                                     │
│     ┌──────┼──────┐                                                             │
│     │      │      │                                                              │
│     │  ■   │  ●   │  ■ Strategic Projects (High Effort, High Impact)           │
│     │ Quick│Strat │  ● Quick Wins (Low Effort, High Impact) ← MVP!             │
│     │ Wins │ Proj │  ▲ Fill-ins (Low Effort, Low Impact)                       │
│  ───┼──────┼──────┼─── (Effort)                                                 │
│     │      │      │  ✖ Avoid / Time Wasters (High Effort, Low Impact)          │
│     │  ▲   │  ✖   │                                                             │
│     │ Fill │Avoid │                                                              │
│     └──────┴──────┘                                                             │
│            │                                                                     │
│        Low Impact                                                                │
│                                                                                  │
│  MASKEN PLATZIERT (basierend auf RICE Score + Effort):                          │
│  • Quick Wins: [Maske A, Maske B, Maske C] → **MVP-Kandidaten!**               │
│  • Strategic: [Maske D, Maske E] → Phase 2                                     │
│  • Fill-ins: [Maske F] → Backlog                                               │
│  • Avoid: [Maske G] → Nicht migrieren (AI-Ersatz oder Sunset)                  │
│                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────┘

ANALYSE-LOGIK (codecentric Vorschlag):
1. 2×2 Complexity Matrix → Klassifiziert Komplexität (Q1-Q4)
2. RICE Scoring → Priorisiert nach Business Value (Effort basiert auf Q1-Q4)
3. Pattern Catalog → Matched Migration-Ansatz (P1-P8, codecentric Vorschlag)
4. Impact/Effort Matrix → Visualisiert Quick Wins für MVP
```

**Miro Elements:**
- **Tier 1:** Text box for filter results
- **Tier 2:** Interactive 2×2 Matrix with sticky notes (masks placed in quadrants by Bounded Context)
- **Tier 3:** RICE Scoring table (fillable cells), Pattern Catalog reference table (pre-populated INPUT)
- **Impact/Effort Matrix:** 2×2 grid with sticky notes for masks (drag-and-drop from RICE table)
- **Color coding:** 
  - Green sticky notes = Quick Wins (MVP candidates)
  - Orange = Strategic Projects (Phase 2)
  - Yellow = Fill-ins (Backlog)
  - Red = Avoid (AI-Ersatz or Sunset)

**Facilitator Input:**
- Use `/facilitation/tag1_maskenanalyse_guide.md` for step-by-step guidance (Part 2: Funnel Approach)
- Use `/facilitation/tag1_maskenanalyse_fragenkatalog.md` for 26-question assessment
- Use `/facilitation/tag1_masken_pattern_katalog.md` for Pattern P1-P8 definitions (codecentric Vorschlag)
- **Tier 1:** WGV applies filters on their Excel spreadsheet (pre-workshop homework)
- **Tier 2:** Collaborative clustering - WGV places masks on 2×2 Matrix, grouped by Bounded Context
- **Tier 3:** Collaborative RICE scoring - WGV estimates Reach/Impact, codecentric guides Effort (based on Q1-Q4), Pattern Matching (codecentric Vorschlag), calculate together

**Time:** ~60-70 minutes (90-120 min total Maskenanalyse session minus 20 min Framework Introduction = 70-100 min, compressed to 60-70 min for Miro frame work)

---

### **Frame 5: UI/UX Transformation Approach (INPUT)**

**Purpose:** codecentric präsentiert Approach für UX/UI Transformation (Methodologie-Präsentation, nicht kollaborative Session)

**Note:** WGV PM Feedback: UX/UI als "approach presentation", Fokus auf technische Machbarkeit. Keine ausführliche kollaborative UX-Session.

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  CODECENTRIC APPROACH: UI/UX TRANSFORMATION                 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  METHODOLOGIE:                                              │
│  1. User Research & Journey Mapping                         │
│  2. Information Architecture                                │
│  3. Pattern Library Entwicklung                             │
│  4. Iteratives Mockup & Prototyping                         │
│  5. User Testing & Feedback Loops                           │
│                                                             │
│  UI/UX PATTERNS (Beispiele):                                │
│  📝 Traditionelle Forms (Power User, hohe Datendichte)      │
│  💬 Conversational UI (Self-Service, einfache Prozesse)     │
│  🔀 Hybrid (Forms + AI-Assistent, Best of Both)             │
│                                                             │
│  PROJEKTERFAHRUNG:                                          │
│  • [Projekt 1: Oracle Forms → React Migration]             │
│  • [Projekt 2: Insurance Platform Modernisierung]          │
│                                                             │
│  FÜR WGV EMPFOHLEN:                                         │
│  • Hybrid Approach (Forms + AI-Assistent für Power User)   │
│  • Schrittweise Migration (nicht Big Bang)                 │
│  • User Testing mit echten Sachbearbeitern                  │
│                                                             │
│  Q&A                                                        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- Präsentations-Folien (INPUT von codecentric)
- Keine CAPTURE-Bereiche (keine sticky notes, keine kollaborative Entscheidung)
- Q&A Bereich für Fragen

**Facilitator Approach:**
- codecentric präsentiert Methodologie und Beispiele
- WGV stellt Verständnisfragen
- **KEINE** detaillierte User Journey Analyse
- **KEINE** Mockup-Erstellung im Workshop
- Ziel: WGV versteht, WIE codecentric UX/UI Transformation angeht (für spätere Projekt-Phasen)

**Time:** 45-60 min (30-40 min Präsentation + 15-20 min Q&A)

---

### **Frame 6: AI Features Brainstorm (CAPTURE)**

**Purpose:** Identify AI opportunities in WGV processes

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  AI FEATURES - WO KANN KI HELFEN?                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  KATEGORIE 1: PROZESS-AUTOMATISIERUNG                       │
│  ┌────────┐ ┌────────┐ ┌────────┐                          │
│  │[sticky]│ │[sticky]│ │[sticky]│ ...                      │
│  └────────┘ └────────┘ └────────┘                          │
│                                                             │
│  KATEGORIE 2: DATEN-ANREICHERUNG / VORSCHLÄGE               │
│  ┌────────┐ ┌────────┐ ┌────────┐                          │
│  │[sticky]│ │[sticky]│ │[sticky]│ ...                      │
│  └────────┘ └────────┘ └────────┘                          │
│                                                             │
│  KATEGORIE 3: KONVERSATIONELLE INTERFACES                   │
│  ┌────────┐ ┌────────┐ ┌────────┐                          │
│  │[sticky]│ │[sticky]│ │[sticky]│ ...                      │
│  └────────┘ └────────┘ └────────┘                          │
│                                                             │
│  KATEGORIE 4: REPORTING / ANALYTICS                         │
│  ┌────────┐ ┌────────┐ ┌────────┐                          │
│  │[sticky]│ │[sticky]│ │[sticky]│ ...                      │
│  └────────┘ └────────┘ └────────┘                          │
│                                                             │
│  KATEGORIE 5: ANDERE                                        │
│  ┌────────┐ ┌────────┐                                      │
│  │[sticky]│ │[sticky]│ ...                                 │
│  └────────┘ └────────┘                                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘

VOTIERUNG: Jeder Teilnehmer bekommt 5 Punkte (Dots) zum Verteilen
```

**Miro Elements:**
- Open brainstorm space with categories
- Sticky notes added by participants
- Voting dots to prioritize ideas

**Time:** ~45 minutes

---

### **Frame 7: Initial Scope Decision (CAPTURE)**

**Purpose:** Select 3-5 masks for MVP

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  SCOPE ENTSCHEIDUNG: MVP MASKEN                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  AUSGEWÄHLTE MVP-MASKEN (3-5):                              │
│                                                             │
│  1. [Maske Name]                                            │
│     Begründung: [text]                                      │
│     Risiken: [text]                                         │
│                                                             │
│  2. [Maske Name]                                            │
│     Begründung: [text]                                      │
│     Risiken: [text]                                         │
│                                                             │
│  3. [Maske Name]                                            │
│     Begründung: [text]                                      │
│     Risiken: [text]                                         │
│                                                             │
│  [Optional: 4., 5.]                                         │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  PHASE 2 KANDIDATEN (BACKLOG):                              │
│  • [Maske]                                                  │
│  • [Maske]                                                  │
│  • ...                                                      │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  NICHT MIGRIEREN (AI-Ersatz oder Sunset):                   │
│  • [Maske]                                                  │
│  • ...                                                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- Text boxes for mask names + rationale
- Drag-and-drop from Frame 4 (Mask Analysis Matrix)
- Color coding: Green (MVP), Yellow (Phase 2), Red (defer/sunset)

**Time:** ~45 minutes - aligned with committed agenda "Initial Scope Discussion"

**End of Day 1 Checkpoint:** Frame 7 completed = clear MVP scope for Day 2

---

## BOARD 3: Tag 2 - Architecture & Technology

**Opening (no dedicated frame):** Recap Tag 1 & Scope refinement - 10 min verbal discussion referencing Day 1 Miro frames

---

### **Frame 7.5: Migration Strategy - Strangler Fig Validation (HYBRID)**

**Purpose:** Validate Strangler Fig migration strategy recommendation and capture WGV-specific objections or additions

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  MIGRATIONSSTRATEGIE - UNSERE EMPFEHLUNG                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  KONTEXT:                                                   │
│  "Die Frontend-Migration muss möglichst schnell Mehrwert   │
│   für WGV-Mitarbeiter liefern. Gleichzeitig ist die        │
│   Zielrichtung nicht von Anfang an klar: Komplexe          │
│   Geschäftslogik (abgebildet in Stored Procedures) und     │
│   spezialisierte Power-User-Anforderungen erfordern        │
│   iteratives Lernen. Strangler Fig ermöglicht kurze        │
│   Feedback-Zyklen, um Risiken zu minimieren und            │
│   Abweichungen von Business-Zielen frühzeitig zu erkennen."│
│                                                             │
│  ═══════════════════════════════════════════════════════   │
│                                                             │
│  STRANGLER FIG + BOUNDED CONTEXT + FEATURE TOGGLES          │
│                                                             │
│  ✅ PRO-ARGUMENTE:                                          │
│  1. Risikominimierung durch inkrementellen Ansatz           │
│     (Rollback einzelner Module möglich)                     │
│  2. Schnelle Time-to-Market                                 │
│     (Erste Features nach 3-5 Masken produktiv)              │
│  3. Kontinuierliches Lernen & Kurskorrekturen               │
│     (Feedback aus frühen Migrationen verbessert Folge-Phase)│
│  4. Schrittweiser Kompetenzaufbau im Team                   │
│     (Neue Technologien graduell lernen)                     │
│  5. Kein "Flagday"-Risiko                                   │
│     (Vermeidung des klassischen Cutover-Disasters)          │
│                                                             │
│  ❌ CON-ARGUMENTE:                                          │
│  1. Längere Parallelbetriebs-Phase (2-3 Jahre)              │
│  2. Doppelte Systempflege                                   │
│     (Bugfixes ggf. in Alt- UND Neu-System)                  │
│  3. Navigation & UX-Komplexität                             │
│     (Routing zwischen Systemen, kritisch bei fragiler IA)   │
│  4. Governance-Overhead                                     │
│     (Priorisierung & architektonische Konsistenz sichern)   │
│                                                             │
│  ─────────────────────────────────────────────────────────  │
│                                                             │
│  🎯 CODECENTRIC EMPFEHLUNG: STRANGLER FIG                   │
│                                                             │
│  Begründung:                                                │
│  • 900 Masken → Big Bang unrealistisch                      │
│  • Parallel-Systeme bereits vorhanden (ICIS+, APEX)         │
│  • Lernen aus frühen Migrationen verbessert Folge-Phasen    │
│  • Reduziert Cutover-Risiko (kein "Alles-oder-Nichts")      │
│                                                             │
│  ═══════════════════════════════════════════════════════   │
│                                                             │
│  💬 DISKUSSION: SEHEN SIE DAS ANDERS?                       │
│                                                             │
│  Gibt es Faktoren, die gegen Strangler Fig sprechen?       │
│  (z.B. Deadlines, Budget, Governance, Politik)              │
│                                                             │
│  [CAPTURE Bereich: Sticky Notes für Einwände/Ergänzungen]  │
│                                                             │
│  Zusätzliche PROs/CONs aus WGV Sicht:                       │
│  [CAPTURE Bereich: Sticky Notes]                            │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- INPUT: PRO/CON analysis (pre-populated)
- INPUT: Recommendation with rationale (pre-populated)
- CAPTURE: Sticky notes area for objections
- CAPTURE: Sticky notes area for additional PROs/CONs from WGV perspective

**Facilitation Approach:**
1. **Present (5-8 min):** Walk through PROs/CONs and recommendation
2. **Check for Objections (5-10 min):** "Sehen Sie Faktoren, die dagegen sprechen?" (deadlines, budget, political constraints)
3. **Invite Additional Insights (5 min):** "Welche PROs/CONs würden Sie aus WGV-Perspektive ergänzen?"

**This is NOT:**
- A brainstorming session comparing multiple strategies
- An open-ended "which strategy should we choose" debate
- A 50/50 decision where codecentric is neutral

**This IS:**
- Expert recommendation with transparent reasoning
- Validation checkpoint: "Challenge us if we missed something critical"
- Space for WGV to surface unknown constraints (regulatory, budget, political)

**Time:** 15-20 min

**Reference:**
- `/context/oracle_forms_migration_options_reference.md` (Strangler Fig pattern)
- `/context/migration_risk_assessment.md` (R1-R10 risks)

---

### **Frame 8: Services/SP Overview + Integration Layer Comparison (HYBRID)**

**Purpose:** Understand existing backend landscape (Services/Stored Procedures) before choosing integration technology

**Structure:**
- **Part 1 (60 min):** WGV presents Services/Stored Procedures (MVP-relevant only)
- **Part 2 (25 min):** codecentric presents Integration Layer technology comparison

---

**Part 1 Layout: Services/Stored Procedures Overview**
```
┌─────────────────────────────────────────────────────────────┐
│  SERVICE/STORED PROCEDURES - MVP SCOPE                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  PRESENTER: WGV Architekten/Entwickler                      │
│  FORMAT: Signature-level documentation (see guide)          │
│                                                             │
│  SP-TYPEN (für MVP-Masken):                                 │
│                                                             │
│  BSP (Berichts-SP):                                         │
│  • [SP Name] - Signature, Zweck, Abhängigkeiten            │
│  • ...                                                      │
│                                                             │
│  DSP (Daten-SP):                                            │
│  • [SP Name] - Signature, Zweck, Abhängigkeiten            │
│    Example: SP_KUNDE_SUCHEN                                 │
│    - Input: Suchkriterien (Name, PLZ)                       │
│    - Output: KundenListe                                    │
│    - **Entities: KUNDE (Read), ADRESSE (Read)**             │
│  • ...                                                      │
│                                                             │
│  GSP (Geschäftslogik-SP):                                   │
│  • [SP Name] - Signature, Zweck, Abhängigkeiten            │
│    Example: SP_SCHADEN_ANLEGEN                              │
│    - Input: SchadenArt, Datum, BeschreibungText            │
│    - Output: SchadenID                                      │
│    - **Entities: SCHADEN (Create), KUNDE (Read-only)**      │
│  • ...                                                      │
│                                                             │
│  TSP (Transaktions-SP):                                     │
│  • [SP Name] - Signature, Zweck, Abhängigkeiten            │
│  • ...                                                      │
│                                                             │
│  WIEDERVERWENDUNG:                                          │
│  • Welche SPs aus ICIS+ können wiederverwendet werden?      │
│  • Welche müssen neu exponiert werden?                      │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  INFORMATION ARCHITECTURE (DETAIL-EBENE):                   │
│                                                             │
│  ENTITY-ZUGRIFF pro SP (dokumentiert während Präsentation): │
│  • SP_KUNDE_SUCHEN → Read: KUNDE, ADRESSE                  │
│  • SP_SCHADEN_ANLEGEN → Create: SCHADEN, Read: KUNDE       │
│  • SP_VERTRAG_ÄNDERN → Update: VERTRAG, Read: PRODUKT      │
│                                                             │
│  DATEN-FLUSS-MUSTER:                                        │
│  • Welche SPs greifen auf Shared Entities zu? (z.B. KUNDE) │
│  • Welche SPs sind Bounded-Context-spezifisch?              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Facilitator Reference:** 
- Use Service-SP-Katalog template from `/facilitation/tag2_architecture_decisions_guide.md` Activity 2
- **Information Architecture**: Dokumentiere Entity-Zugriff (CRUD-Operations) für jede SP - verbindet Business-Sicht (Frame 3) mit technischer Detail-Sicht

**Text Blocks for Information Architecture Analysis (Miro Board / Facilitator Script):**

**Block 1 - Zweck der IA-Analyse:**
"Die Core-Entitäten Ihrer Datenarchitektur (KUNDE, VERTRAG, SCHADEN, etc.) definieren die REST API-Struktur und Frontend-Datenmodelle. → Dokumentieren Sie: Welche Entitäten sind zentral für die MVP-Masken?"

**Block 2 - Entity-Zugriff Dokumentation:**
"FÜR JEDE SP: Notieren Sie CRUD-Operationen auf Entitäten (z.B. SP_KUNDE_SUCHEN → Read: KUNDE, ADRESSE). Diese Information bestimmt die API-Endpunkt-Struktur im Integration Layer und die Datenmodelle im Frontend."

**Block 3 - Shared Entities & Data Flow:**
"SHARED ENTITIES: Entitäten wie KUNDE, die von mehreren SPs verwendet werden, zeigen uns, wo einheitliche API-Contracts notwendig sind. Bounded-Context-spezifische SPs können eigenständige REST-Ressourcen werden."

---

**Part 2 Layout: Integration Layer Comparison**
```
┌────────────────────────────────────────────────────────────────────────────────┐
│  INTEGRATION LAYER: TECHNOLOGIE-VERGLEICH                                      │
├──────────────┬────────────────────┬────────────────────┬─────────────────────┤
│ KRITERIUM    │ SPRING BOOT        │ ORACLE ORDS        │ HYBRID              │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Flexibilität │ ★★★★★              │ ★★☆☆☆              │ ★★★★☆               │
│              │ Java-Ecosystem,    │ Oracle-spezifisch, │ ORDS für einfache,  │
│              │ alle Frameworks    │ REST-only          │ Spring für komplexe │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ PL/SQL       │ ★★★☆☆              │ ★★★★★              │ ★★★★☆               │
│ Integration  │ JDBC, manuell      │ Auto-generiert     │ Best of both        │
│              │ Type-Mapping       │ aus SP             │                     │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Vendor       │ ★★★★★              │ ★☆☆☆☆              │ ★★★☆☆               │
│ Lock-In      │ Cloud-agnostic     │ Oracle-locked      │ Teils locked        │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Team Skills  │ ★★★★☆              │ ★★☆☆☆              │ ★★★☆☆               │
│              │ Java verbreitet    │ ORDS-Spezialisten  │ Beide Skills nötig  │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ AI Gateway   │ ★★★★★              │ ★★☆☆☆              │ ★★★★☆               │
│ Integration  │ Spring AI, MCP     │ Begrenzt           │ Spring für AI       │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Entwicklungs-│ ★★★☆☆              │ ★★★★★              │ ★★★★☆               │
│ geschwindig. │ Mehr Code          │ Wenig Code         │ Balanced            │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ REST API     │ ★★★★★              │ ★★★★☆              │ ★★★★☆               │
│ Standards    │ OpenAPI/Swagger    │ Auto-generiert     │ Hybrid Approach     │
│              │ Volle Kontrolle    │ Begrenzte          │ ORDS auto-gen +     │
│              │ über Versionierung │ Anpassung          │ Spring custom APIs  │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ EMPFEHLUNG   │ Für umfassende     │ Für APEX-Fokus,    │ Pragmatisch:        │
│              │ Modernisierung,    │ schneller Proof    │ Start mit ORDS,     │
│              │ AI-Integration     │ of Concept         │ expand zu Spring    │
└──────────────┴────────────────────┴────────────────────┴─────────────────────┘
```

**Miro Elements:**
- **Part 1:** Service-SP catalog template (fillable during WGV presentation)
- **Part 2:** Comparison table (INPUT from codecentric) with star ratings

**Supporting Reference:**
- `/facilitation/tag2_architecture_decisions_guide.md` Activity 2 (Service-SP-Katalog)
- `/context/oracle_forms_migration_options_reference.md` (Spring Boot vs. ORDS discussion)

**Time:** 85 min total (60 min Services/SP presentation + 25 min Integration Layer comparison) - aligned with committed agenda "Vorstellung bestehender Services / Stored Procedures" (partial) + "Diskussion von Ansätzen für die Integrationsschicht" (partial)

---

### **Frame 9: Technical Feasibility + Integration Layer Decision (CAPTURE)**

**Purpose:** Assess MVP mask feasibility and document integration technology decision

**Structure:**
- **Part 1 (35 min):** Technical Feasibility Matrix for MVP masks
- **Part 2 (30 min):** Integration Layer Decision + REST API Standards

---

**Part 1 Layout: Technical Feasibility Analysis**
```
┌──────────────────────────────────────────────────────────────────────────────────┐
│  MACHBARKEITSANALYSE - MVP MASKEN                                                 │
├─────────────┬──────────┬──────────┬──────────┬──────────┬──────────┬──────────┤
│ Maske       │SP-       │UI-       │Daten-    │Abhängig- │Risiko-   │MVP-      │
│             │Komplexität│Komplexität│Migration │keiten    │Score     │Eignung   │
│             │(1-3)     │(1-3)     │(1-3)     │(1-3)     │(Summe)   │(Ja/Nein) │
├─────────────┼──────────┼──────────┼──────────┼──────────┼──────────┼──────────┤
│[Maske 1]    │          │          │          │          │          │          │
├─────────────┼──────────┼──────────┼──────────┼──────────┼──────────┼──────────┤
│[Maske 2]    │          │          │          │          │          │          │
├─────────────┼──────────┼──────────┼──────────┼──────────┼──────────┼──────────┤
│...          │          │          │          │          │          │          │
└─────────────┴──────────┴──────────┴──────────┴──────────┴──────────┴──────────┘

RISIKO-SCORING (aus tag2_architecture_decisions_guide.md):
• 6-9 Punkte: MVP-ready (Low Risk)
• 10-13 Punkte: Risky (needs mitigation)
• 14-18 Punkte: Not suitable for MVP (defer)

6 KRITERIEN: SP-Komplexität, UI-Komplexität, Daten-Migration, Abhängigkeiten, 
             Vaadin-Wiederverwendung, AI-Substitution-Potential
```

**Facilitator Reference:** Use Machbarkeits-Matrix from `/facilitation/tag2_architecture_decisions_guide.md` Activity 3

---

**Part 2 Layout: Integration Layer Decision**
```
┌─────────────────────────────────────────────────────────────┐
│  INTEGRATION LAYER - ENTSCHEIDUNG                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  GEWÄHLTE TECHNOLOGIE:                                      │
│  ☐ Spring Boot                                              │
│  ☐ Oracle ORDS                                              │
│  ☐ Hybrid (ORDS + Spring Boot)                             │
│                                                             │
│  BEGRÜNDUNG:                                                │
│  [Large text area for rationale]                            │
│                                                             │
│  TRADE-OFFS AKZEPTIERT:                                     │
│  [Text area - what are we giving up?]                       │
│                                                             │
│  RISIKEN & MITIGATIONEN:                                    │
│  [Text area]                                                │
│                                                             │
│  NÄCHSTE SCHRITTE:                                          │
│  • [Action item]                                            │
│  • [Action item]                                            │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  REST API STANDARDS (Integration Layer Output)              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  VERSIONIERUNGSSTRATEGIE:                                   │
│  ☐ URL-basiert (/v1/, /v2/)                                │
│  ☐ Header-basiert (Accept: application/vnd.wgv.v1+json)   │
│  ☐ Query-Parameter (?version=1)                            │
│                                                             │
│  OPENAPI/SWAGGER SPEZIFIKATION:                             │
│  ☐ Ja - Tool: [Springdoc/Swagger UI/etc.]                 │
│  ☐ Nein - Manuell dokumentiert                             │
│                                                             │
│  BREAKING CHANGES POLICY:                                   │
│  [Text area - wie gehen wir mit Breaking Changes um?]       │
│  Beispiele:                                                 │
│  • Neue Major Version bei Breaking Changes                  │
│  • Deprecation Period: [X Monate]                           │
│  • Backwards Compatibility: [Strategie]                     │
│                                                             │
│  API DESIGN PRINCIPLES:                                     │
│  [Text area - RESTful best practices, Namenskonventionen]   │
│                                                             │
└─────────────────────────────────────────────────────────────┘

ADR (Architecture Decision Record) - wird nach Workshop formalisiert
```

**Miro Elements:**
- **Part 1:** Feasibility matrix table (fillable during collaborative assessment)
- **Part 2:** Integration decision checkboxes, text areas for rationale
- REST API standards capture section (versioning, OpenAPI, breaking changes)
- Reference to ADR template (will be written post-workshop)

**Facilitator Reference:**
- `/facilitation/tag2_architecture_decisions_guide.md` Activity 3 (Machbarkeits-Matrix with 6 criteria)
- `/facilitation/tag2_architecture_decisions_guide.md` Activity 4 (Integration Layer decision)

**Time:** 65 min total (35 min Technical Feasibility + 30 min Integration Decision incl. REST API standards) - aligned with committed agenda "Technische Machbarkeitsanalyse" (partial) + "Diskussion von Ansätzen für die Integrationsschicht" (partial)

---

### **Frame 10: Deployment Options Comparison (INPUT)**

**Purpose:** Compare deployment strategies

**Layout:**
```
┌────────────────────────────────────────────────────────────────────────────────┐
│  DEPLOYMENT: TECHNOLOGIE-VERGLEICH                                             │
├──────────────┬────────────────┬────────────────┬────────────────┬─────────────┤
│ KRITERIUM    │ VMs (klassisch)│ DOCKER         │ KUBERNETES     │ AZURE       │
│              │                │ (Docker Comp.) │ (AKS)          │ CONT. APPS  │
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ Komplexität  │ ★★☆☆☆          │ ★★★☆☆          │ ★★★★★          │ ★★★☆☆       │
│              │ Einfach        │ Mittel         │ Hoch           │ Mittel      │
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ Skalierung   │ ★★☆☆☆          │ ★★★☆☆          │ ★★★★★          │ ★★★★☆       │
│              │ Manuell        │ Orchestrierung │ Auto-scaling   │ Auto-scaling│
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ Cloud-       │ ★★★★★          │ ★★★★★          │ ★★★★★          │ ★★☆☆☆       │
│ Portabilität │ Überall        │ Überall        │ Jede Cloud     │ Azure-only  │
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ Ops-Aufwand  │ ★★★★☆          │ ★★★☆☆          │ ★★☆☆☆          │ ★★★★☆       │
│              │ Hoch (manuell) │ Mittel         │ Hoch (K8s)     │ Niedrig     │
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ Team Skills  │ ★★★★★          │ ★★★☆☆          │ ★★☆☆☆          │ ★★★☆☆       │
│              │ Vorhanden      │ Lernbar        │ Spezialisiert  │ Azure-Know  │
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ Kosten       │ ★★★☆☆          │ ★★★★☆          │ ★★☆☆☆          │ ★★★☆☆       │
│              │ Mittel         │ Niedrig        │ Hoch           │ Mittel      │
├──────────────┼────────────────┼────────────────┼────────────────┼─────────────┤
│ EMPFEHLUNG   │ Schneller Start│ Gute Balance   │ Wenn große     │ Wenn Azure  │
│              │ wenig Änderung │ Modernität vs. │ Skalierung     │ strategisch │
│              │                │ Komplexität    │ benötigt       │ gewählt     │
└──────────────┴────────────────┴────────────────┴────────────────┴─────────────┘
```

**Miro Elements:**
- Comparison table (INPUT - pre-populated)
- Star ratings
- Recommendation guidance

**Time:** 20 min (quick review of pre-populated comparison table) - aligned with committed agenda "Diskussion von Deploymentansätzen" (partial)

---

### **Frame 11: Deployment Decision (CAPTURE)**

**Purpose:** Document deployment decision

**Layout:** Same as Frame 9 Part 2, but for deployment (decision checkboxes, rationale, trade-offs, risks, next steps)

**Time:** 25 min - aligned with committed agenda "Diskussion von Deploymentansätzen" (partial, combined with Frame 10 = 45 min total)

---

### **Frame 12: Architecture Diagram Canvas (CAPTURE)**

**Purpose:** Collaborative architecture drawing

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  ZIELARCHITEKTUR - COLLABORATIVE DRAWING                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  [Large whiteboard area]                                    │
│                                                             │
│  LAYERS:                                                    │
│  • Frontend Layer (Browser)                                 │
│  • Integration Layer (Spring Boot / ORDS)                   │
│  • Database Layer (Oracle + PL/SQL)                         │
│                                                             │
│  EXTERNAL INTEGRATIONS:                                     │
│  • SAP, COR Life, GDV, DMS, etc.                            │
│                                                             │
│  DEPLOYMENT:                                                │
│  • Container orchestration                                  │
│  • Networking, Load Balancing                               │
│                                                             │
│  AI COMPONENTS:                                             │
│  • MCP Server / AI Gateway                                  │
│  • LLM Integration                                          │
│                                                             │
└─────────────────────────────────────────────────────────────┘

TEMPLATE: Use Miro shapes library (rectangles, arrows, icons)
```

**Miro Elements:**
- Large canvas for drawing
- Miro shapes library (boxes, arrows, clouds, etc.)
- Color coding by layer (e.g., blue for frontend, green for integration, orange for database)
- Icons for external systems

**Facilitator Approach:**
- Start with template skeleton (layers pre-drawn)
- WGV + codecentric fill in components collaboratively
- Use sticky notes for questions/open decisions

**Time:** ~1 hour

**Reference:**
- Use existing diagrams from `/context/` as inspiration, but draw WGV-specific architecture

---

### **Frame 13: AI Integration Patterns (INPUT + CAPTURE)**

**Purpose:** Decide how AI integrates into architecture

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  AI INTEGRATION - WIE INTEGRIEREN WIR KI?                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  PATTERN 1: MCP SERVER (Model Context Protocol)             │
│  [Diagram showing MCP server architecture]                  │
│  ✓ Pros: Standard protocol, tool access, RBAC               │
│  ✗ Cons: Additional component to maintain                   │
│                                                             │
│  PATTERN 2: SPRING AI INTEGRATION                           │
│  [Diagram showing Spring AI in integration layer]           │
│  ✓ Pros: Unified with backend, Java ecosystem               │
│  ✗ Cons: Tighter coupling                                   │
│                                                             │
│  PATTERN 3: DIRECT LLM CALLS (Frontend)                     │
│  [Diagram showing frontend → LLM API]                       │
│  ✓ Pros: Simple, fast prototyping                           │
│  ✗ Cons: No RBAC, security concerns, no tool access         │
│                                                             │
│  PATTERN 4: HYBRID                                          │
│  [Diagram showing combination]                              │
│  ✓ Pros: Flexibility, right tool for right job              │
│  ✗ Cons: More complexity                                    │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  WGV ENTSCHEIDUNG:                                          │
│  [Text area for decision + rationale]                       │
│                                                             │
│  RBAC ANFORDERUNGEN:                                        │
│  [Text area - who can access what?]                         │
│                                                             │
│  HOSTING:                                                   │
│  ☐ Cloud (Azure OpenAI, Anthropic)                         │
│  ☐ On-Premise (self-hosted LLM)                            │
│  ☐ Hybrid                                                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- INPUT: 4 pattern diagrams (small, schematic)
- CAPTURE: Decision area at bottom (RBAC, hosting)

**Time:** 45 min - aligned with committed agenda "Integration von AI ins System" (reduced from 60 min)

**End of Day 2 Checkpoint:** Architecture diagram + technology decisions documented

---

## BOARD 4: Tag 3 - Frontend & AI-Driven Dev

### **Frame 14: Frontend Framework Comparison (INPUT)**

**Purpose:** Compare frontend technology options

**Layout:**
```
┌────────────────────────────────────────────────────────────────────────────────┐
│  FRONTEND FRAMEWORK: TECHNOLOGIE-VERGLEICH                                     │
├──────────────┬────────────────────┬────────────────────┬─────────────────────┤
│ KRITERIUM    │ REACT              │ ANGULAR            │ VUE                 │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ LLM          │ ★★★★★              │ ★★★★☆              │ ★★★☆☆               │
│ Unterstützung│ Riesiger Korpus    │ Gut dokumentiert   │ Weniger Trainingsdat│
│              │ (Copilot, Claude)  │                    │                     │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Vaadin       │ ★★★☆☆              │ ★★☆☆☆              │ ★★☆☆☆               │
│ Koexistenz   │ Integration möglich│ Integration möglich│ Integration möglich │
│              │ (Web Components)   │                    │                     │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Langlebigkeit│ ★★★★★              │ ★★★★★              │ ★★★★☆               │
│              │ Meta-backed, 10+J. │ Google-backed, 8+J.│ Community, 10+J.    │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Team Skills  │ ★★★★☆              │ ★★★☆☆              │ ★★★☆☆               │
│              │ Sehr verbreitet    │ Enterprise-Welt    │ Leicht zu lernen    │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Komplexe     │ ★★★★☆              │ ★★★★★              │ ★★★☆☆               │
│ Forms        │ Bibliotheken nötig │ Built-in (Reactive)│ Bibliotheken nötig  │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ TypeScript   │ ★★★★★              │ ★★★★★              │ ★★★★☆               │
│              │ First-class        │ Built-in           │ Gut unterstützt     │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ Component    │ ★★★★★              │ ★★★★☆              │ ★★★★☆               │
│ Ecosystem    │ Riesig             │ Material, PrimeNG  │ Vuetify, Element    │
├──────────────┼────────────────────┼────────────────────┼─────────────────────┤
│ EMPFEHLUNG   │ Wenn AI-Assistenz  │ Wenn Enterprise-   │ Wenn einfachste     │
│              │ Priorität hat,     │ Patterns + Forms-  │ Lernkurve gewünscht │
│              │ große Community    │ Fokus wichtig      │                     │
└──────────────┴────────────────────┴────────────────────┴─────────────────────┘
```

**Miro Elements:**
- Comparison table (INPUT)
- Star ratings
- Link to article reference (Flynn Jones article mentions framework choice)

**Time:** 20 minutes presentation + 30 minutes discussion

---

### **Frame 15: Frontend Decision (CAPTURE)**

**Purpose:** Document frontend framework decision

**Layout:** Same as Frame 9, but for frontend

**Time:** 20-30 minutes

---

### **Frame 16: AI-Driven Dev Workshop Space (CAPTURE)**

**Purpose:** Hands-on AI-driven development workshop

**Note:** Content and activities for this frame will be defined by colleague.

**Time:** TBD (to be defined by content owner)

---

### **Frame 17: Next Steps & Roadmap (CAPTURE)**

**Purpose:** Define action items and timeline post-workshop

**Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  NEXT STEPS & ROADMAP                                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  IMMEDIATE NEXT STEPS (Wochen 1-4):                         │
│  ┌────────────────────────────────────────┬──────┬────────┐ │
│  │ Action Item                            │ Owner│ Deadline│ │
│  ├────────────────────────────────────────┼──────┼────────┤ │
│  │ 1. [Action]                            │[Name]│ [Date] │ │
│  │ 2. [Action]                            │      │        │ │
│  │ ...                                    │      │        │ │
│  └────────────────────────────────────────┴──────┴────────┘ │
│                                                             │
│  PHASE 0: FOUNDATION (Monate 1-2)                           │
│  • [Milestone]                                              │
│  • [Milestone]                                              │
│                                                             │
│  PHASE 1: MVP PILOT (Monate 3-5)                            │
│  • [Milestone]                                              │
│  • [Milestone]                                              │
│                                                             │
│  PHASE 2+: ACCELERATED MIGRATION                            │
│  • [High-level timeline]                                    │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  ENTSCHEIDUNGEN ZU KLÄREN (Open Items):                     │
│  • [Decision needed]                                        │
│  • [Decision needed]                                        │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  FOLLOW-UP WORKSHOPS / MEETINGS:                            │
│  • [Date + Topic]                                           │
│  • [Date + Topic]                                           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Miro Elements:**
- Action items table
- Timeline visualization (optional: Gantt-style bars)
- Open decisions list
- Follow-up meeting schedule

**Time:** ~30-45 minutes

**End of Day 3 Checkpoint:** Clear roadmap + action items with owners

---

## Miro Board Setup Checklist

### **Pre-Workshop (1 week before):**
- [ ] Create 4 Miro boards (Storyline, Day 1, Day 2, Day 3)
- [ ] Design INPUT frames (comparisons, frameworks) - fully populated
- [ ] Design CAPTURE frames (templates) - empty, ready to fill
- [ ] Add frame numbers and clear navigation
- [ ] Share Miro board link with WGV participants (view access for now)

### **Day 0 (Workshop Start):**
- [ ] Brief WGV on Miro navigation
- [ ] Explain INPUT vs. CAPTURE frame types
- [ ] Demonstrate sticky notes, voting, drawing tools
- [ ] Set collaboration permissions (edit access for all)

### **During Workshop:**
- [ ] Screen share Miro board throughout
- [ ] codecentric facilitator moves between frames
- [ ] WGV participants add content to CAPTURE frames
- [ ] Take screenshots at end of each day (backup)

### **Post-Workshop:**
- [ ] Export Miro boards as PDF (documentation)
- [ ] Formalize ADRs based on captured decisions
- [ ] Share Miro link with all participants (read-only post-workshop)
- [ ] Convert Frame 17 (Next Steps) into project plan

---

## Miro Tips for Time-Constrained Workshop

**Efficiency Tactics:**
1. **Pre-populate INPUT frames** - don't create content live
2. **Use templates** - sticky note colors, voting dots ready
3. **Frame navigation** - number frames clearly, use Miro's frame outline
4. **Parking Lot frame** - for off-topic ideas that arise
5. **Timer visible** - use Miro timer widget to keep on schedule
6. **Collaborative cursors** - show who's working on what (Miro feature)
7. **Mobile access** - participants can use Miro on phones for voting/stickies

**What NOT to do:**
- Don't create complex diagrams live (use templates or pre-drawn)
- Don't read text-heavy slides (if it's INPUT, send it ahead)
- Don't let discussions derail into rabbit holes (use parking lot)

---

## Total Frame Count: 18 Frames

**INPUT Frames (codecentric presents):** 6
- Frame 1: Storyline
- Frame 2: Workshop Journey
- Frame 8: Integration comparison
- Frame 10: Deployment comparison
- Frame 13: AI integration (partial INPUT)
- Frame 14: Frontend comparison

**HYBRID Frames (codecentric presents + WGV validates/adds):** 1
- Frame 7.5: Migration strategy validation (Strangler Fig recommendation + objections)

**CAPTURE Frames (WGV collaborates):** 11
- Frame 3: Domain map
- Frame 4: Mask analysis (Three-Tier Funnel: 2×2 Matrix, RICE Scoring, Pattern Matching, Impact/Effort Matrix)
- Frame 5: UI/UX patterns (hybrid)
- Frame 6: AI features brainstorm
- Frame 7: Scope decision
- Frame 9: Integration decision
- Frame 11: Deployment decision
- Frame 12: Architecture diagram
- Frame 13: AI integration (partial CAPTURE)
- Frame 15: Frontend decision
- Frame 16: AI-driven dev learnings
- Frame 17: Next steps

**Ratio: ~33% INPUT, ~6% HYBRID, ~61% CAPTURE** - highly collaborative!

---

## Time Allocation per Frame

| Frame | Type | Estimated Time |
|-------|------|----------------|
| 1 | INPUT | 5 min |
| 2 | INPUT | 3 min |
| 3 | CAPTURE | 150 min |
| 4 | CAPTURE | 60-70 min (Three-Tier Funnel: Tier 1 ~20-25min, Tier 2 ~25-30min, Tier 3 ~15-20min) |
| 5 | INPUT | 45-60 min |
| 6 | CAPTURE | 45 min |
| 7 | CAPTURE | 45 min |
| 7.5 | HYBRID | 15-20 min |
| 8 | HYBRID | 85 min |
| 9 | CAPTURE | 65 min |
| 10 | INPUT | 20 min |
| 11 | CAPTURE | 25 min |
| 12 | CAPTURE | 60 min |
| 13 | HYBRID | 45 min |
| 14 | INPUT | 50 min |
| 15 | CAPTURE | 20-30 min |
| 16 | CAPTURE | TBD (defined by colleague) |
| 17 | CAPTURE | 30-45 min |

**Total: ~18-20 hours** (fits comfortably in 3 days with breaks)

**Day 1 subtotal (Frames 1-7):** 353-378 min (5h 53min - 6h 18min) - Frame 3 extended to 150 min (full ICIS Deep Dive), Frame 4 updated to Three-Tier Funnel (60-70 min), Frame 5 reduced to INPUT-only (45-60 min)

**Day 2 subtotal (Opening + Frames 7.5, 8-13):** 325-330 min (5h 25min - 5h 30min) - committed agenda 6h 30min, actual 5h 25min-5h 30min (recap 10 min, migration strategy validation 15-20 min, AI integration 45 min), ~60 min gap covered by breaks + efficient facilitation + transitions

---

## Next Steps

1. Review frame designs with codecentric team
2. Adjust INPUT frames based on latest research/decisions
3. Create Miro boards (clone template if available)
4. Populate INPUT frames with content
5. Test navigation and flow
6. Share with WGV 1 week before workshop (read-only preview)
