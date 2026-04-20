# Agenda-Miro-Aktivitäten Abgleich

**Zweck**: Abgleich zwischen committeter Agenda (`2026-04-15_Entwurf_Agenda_v3.md`) und geplanten Miro-Aktivitäten (`miro_board_structure.md`)

**Status**: Vor Sanity-Check mit Client (Meeting heute)

**Erstellt**: 2026-04-18

---

## Tag 1 - Discovery & Scoping

| Agenda-Punkt (Committed) | Miro Frame | Zeit | Typ | Arbeitsmodell (Facilitation Guide) |
|---|---|---|---|---|
| Domäne erkennen & ICIS-System Verständnis | Frame 3: Domain Map | 120 min | CAPTURE | Event Storming Light + Bounded Context Discovery (tag1_domain_mapping_guide.md, tag1_bounded_context_session_guide.md) |
| Analyse von Masken | Frame 4: Mask Analysis Matrix | 90 min | CAPTURE | Strukturiertes Interview, kollaborative Bewertungsmatrix (tag1_maskenanalyse_guide.md) |
| Anwendungskonzept (UI/UX) Skizze | Frame 5: UI/UX Patterns Comparison | 90 min | HYBRID | Pattern-Vergleich, Mockup-Diskussion (tag1_uiux_konzept_guide.md) |
| Diskussion AI Features | Frame 6: AI Features Brainstorm | 45 min | CAPTURE | Brainstorming mit Kategorien, Voting (tag1_features_ai_guide.md) |
| Initial Scope Discussion | Frame 7: Initial Scope Decision | 45 min | CAPTURE | Priorisierung, Entscheidungsfindung |

**Tag 1 Gesamt:** 390 min (6h 30min) - **⚠️ Überlauf: +10-30 min** bei 380 min verfügbarer Zeit

---

## Tag 2 - Architecture & Technology

| Agenda-Punkt (Committed) | Miro Frame | Zeit | Typ | Arbeitsmodell (Facilitation Guide) |
|---|---|---|---|---|
| Recap Tag 1 & Scope-Verschärfung | (Kein Frame - verbal) | 10 min ⚠️ (Agenda: 30 min) | - | Kurze Rückschau, Frames 1-7 referenzieren |
| Vorstellung Services/SP | Frame 8 Part 1: Services/SP Overview | 60 min | HYBRID | WGV präsentiert, codecentric dokumentiert (tag2_architecture_decisions_guide.md Activity 2) |
| Technische Machbarkeitsanalyse | Frame 9 Part 1: Technical Feasibility | 35 min ⚠️ (Agenda: 60 min) | CAPTURE | Kollaborative Bewertungsmatrix mit 6 Kriterien (tag2_architecture_decisions_guide.md Activity 3) |
| Integration von AI | Frame 13: AI Integration Patterns | 45 min ⚠️ (Agenda: 60 min) | HYBRID | 4 Pattern-Vergleich, RBAC/Hosting-Entscheidung |
| Integrationsschicht-Ansätze | Frame 8 Part 2 + Frame 9 Part 2 | 55 min (25+30) | HYBRID + CAPTURE | Tech-Vergleich (Spring/ORDS/Hybrid), Entscheidung + REST API Standards (tag2_architecture_decisions_guide.md Activity 4) |
| Deployment-Ansätze | Frame 10 + Frame 11 | 45 min (20+25) | INPUT + CAPTURE | Deployment-Vergleich (VMs/Docker/K8s/ACA), Entscheidung (tag2_architecture_decisions_guide.md Activity 5) |
| Architekturdiagramm | Frame 12: Architecture Diagram Canvas | 60 min | CAPTURE | Kollaboratives Zeichnen, 4-Layer-Struktur (tag2_architecture_diagram_foundation.md) |

**Tag 2 Gesamt:** 310 min (5h 10min) - innerhalb Budget (380 min)

---

## Tag 3 - Frontend & AI-Driven Dev

| Agenda-Punkt (Committed) | Miro Frame | Zeit | Typ | Arbeitsmodell (Facilitation Guide) |
|---|---|---|---|---|
| Einordnung Frontend Frameworks | Frame 14 + Frame 15 | 70-80 min (50+20-30) ⚠️ (Agenda: 60 min) | INPUT + CAPTURE | Framework-Vergleich (React/Angular/Vue), Entscheidung |
| AI-Driven Development Workshop | Frame 16: AI-Driven Dev Workshop | TBD (Agenda: 5h / 300 min) | CAPTURE | **TBD - Kollege definiert Inhalt** |
| Next Steps & Roadmap | Frame 17: Next Steps & Roadmap | 30-45 min | CAPTURE | Action Planning, Timeline, Follow-ups |

**Tag 3 Gesamt:** 100-125 min (ohne Frame 16) + TBD

---

## ⚠️ Identifizierte Diskrepanzen

### 1. Tag 1 Frame 3 Überlauf
- **Facilitation Guides**: 150-175 min (Event Storming 45-60 + Bounded Context 105-115)
- **Miro Board Structure**: 120 min
- **Committete Agenda**: 120 min
- **Diskrepanz**: +30-55 min Überlauf
- **Frage**: Komprimieren oder Überlauf akzeptieren?

### 2. Tag 2 Recap-Dauer
- **Committete Agenda**: 30 min
- **Miro Board Structure**: 10 min (kein dedizierter Frame, verbal)
- **Diskrepanz**: -20 min
- **Frage**: Welche Dauer ist korrekt? Soll Recap ausführlicher sein?

### 3. Tag 2 Machbarkeitsanalyse
- **Committete Agenda**: 60 min
- **Miro Frame 9 Part 1**: 35 min
- **Diskrepanz**: -25 min
- **Frage**: Zeitbudget anpassen oder Scope der Analyse reduzieren?

### 4. Tag 2 AI Integration
- **Committete Agenda**: 60 min
- **Miro Frame 13**: 45 min
- **Diskrepanz**: -15 min
- **Frage**: Bewusste Kürzung oder Agenda-Zeit unterschätzt?

### 5. Tag 3 Frontend Frameworks
- **Committete Agenda**: 60 min
- **Miro Frames 14 + 15**: 70-80 min
- **Diskrepanz**: +10-20 min Überlauf
- **Frage**: Leicht über Budget, akzeptabel?

---

## Zeitbudget-Übersicht

| Tag | Verfügbare Zeit | Geplante Aktivitäten (Miro) | Committete Agenda | Status |
|-----|-----------------|------------------------------|-------------------|--------|
| Tag 1 | 380 min (6h 20min) | 390 min (6h 30min) | 375 min (6h 15min) | ⚠️ +10-30 min Überlauf |
| Tag 2 | 380 min (6h 20min) | 310 min (5h 10min) | 390 min (6h 30min) | ✅ Innerhalb Budget (70 min Buffer) |
| Tag 3 | 380 min (6h 20min) | 100-125 min + TBD | 390 min (6h 30min) | ⚠️ Frame 16 TBD |

**Frame 16 (AI-Driven Dev Workshop)**: Kollege definiert Inhalt, committete Agenda plant 5h (300 min)

---

## Nächste Schritte

- [ ] Sanity-Check mit Client durchführen (heute)
- [ ] Diskrepanzen mit Kollegen besprechen
- [ ] Frame 3 (Domain Map) Zeitbudget klären
- [ ] Tag 2 Recap-Dauer finalisieren
- [ ] Frame 16 Inhalt und Zeitplan vom Kollegen einholen
- [ ] Miro Board Structure und Facilitation Guides entsprechend anpassen
- [ ] Finale Agenda-Version nach Client-Feedback erstellen

---

## Referenzen

- **Committete Agenda**: `/angebot/2026-04-15_Entwurf_Agenda_v3.md`
- **Miro Board Structure**: `/angebot/miro_board_structure.md`
- **Facilitation Guides**: `/facilitation/tag1_*.md`, `/facilitation/tag2_*.md`
- **Workshop Mapping**: `/context/workshop_mapping.md` (WGV Erwartungen)
