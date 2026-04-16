# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **documentation and planning repository** for a codecentric workshop with WGV (Württembergische Gemeinde-Versicherung a.G.) focused on modernizing their Oracle Forms-based insurance software system (ICIS).

**Not a code repository** - contains workshop materials, proposals, and planning documents.

## Project Context

### WGV Modernization Challenge

- **Current System**: ICIS - Oracle-based insurance software with ~900 Oracle Forms masks
- **Goal**: Modernize frontend and integration layer while keeping Oracle DB and PL/SQL backend unchanged
- **Approach**: AI-driven development to efficiently migrate masks
- **Target Environment**: Azure Cloud with containerization (Kubernetes)

### Key Technical Decisions to Explore in Workshop

1. **Integration Layer**: REST APIs to expose PL/SQL service stored procedures
2. **Frontend Technology**: Modern framework (React/Angular) with consideration for:
   - AI tool support (LLM training data availability)
   - Integration with existing Vaadin components from ICIS+
   - Long-term stability
3. **Hybrid UI Concept**: Combination of chatbot-style interactions and traditional forms for power users
4. **AI Integration**: MCP, RBAC, hosting considerations
5. **Low-Code Option**: Oracle APEX for simple CRUD masks

### Strategic Considerations

- Not all 900 masks will be migrated 1:1; some processes may be replaced by AI agents
- Strong focus on AI-driven development workflow
- Power user requirements (insurance specialists) must be balanced with conversational UI elements
- Long-term solution needed (API versioning, stable technology choices)

## Repository Structure

```
/
├── angebot/                    # Workshop proposals and materials
│   ├── 2026-03-02_Entwurf_Agenda_v2.md    # Latest workshop agenda (use this)
│   ├── Entwurf_Agenda.md                   # Initial agenda draft
│   ├── Ausgangslage_no_image.md            # Project situation analysis
│   ├── Ausgangaslage_WGV_Modernisierung.md # Extended situation (with images)
│   └── WGV_Workshop_Outline_Mail.md        # Initial email outline
├── rollen/                     # Role definitions for workshop experts
│   ├── ux_ui_expert.md                     # UX/UI Expert role
│   ├── solution_architect.md               # Solution Architect role
│   ├── system_architect.md                 # System Architect (Frontend & Backend) role
│   ├── oracle_forms_specialist.md          # Oracle Forms Specialist role
│   ├── staff_frontend_developer.md         # Staff Frontend Developer role
│   ├── staff_backend_developer.md          # Staff Backend Developer role
│   └── power_user_domain_expert.md         # Power User / Domain Expert (WGV side)
├── diagrams/                   # Visual diagrams (SVG, PNG, etc.)
│   ├── icis_oracle_forms_architektur.svg        # Current ICIS Oracle Forms architecture (detail)
│   └── architektur_schaubild_icis_gesamt.svg    # Complete ICIS system architecture
├── context/                    # Interpretations and explanations of diagrams
│   ├── DIAGRAM_REFERENCES.md                    # Registry mapping diagrams to interpretations
│   ├── icis_oracle_forms_architektur.md         # Interpretation of Oracle Forms architecture
│   ├── architektur_schaubild_icis_gesamt.md     # Interpretation of complete ICIS architecture
│   ├── Modernisierungsworkshop-Draft.md         # WGV's detailed workshop expectations
│   └── workshop_mapping.md                      # Mapping of committed agenda to WGV expectations
├── facilitation/               # Workshop facilitation methods and frameworks
│   └── decision_frameworks.md                   # Decision-making frameworks for IT transformation
└── wgv_attachments/           # Supporting media
    ├── *_ICIS-*.jpg           # Screenshots of current ICIS system
    └── *.mp4                  # Demo videos of Oracle Forms workflows
```

## Workshop Structure (3 Days)

**Day 1**: Discovery & Scoping (Users, Architects, optional PO/Developer)
- Domain mapping
- Mask analysis and UI/UX concept development
- AI feature identification
- Initial scope definition (3-5 candidate masks for MVP)

**Day 2**: Technical Validation & Architecture (Architects, Developers)
- Scope refinement based on technical feasibility
- Review existing service stored procedures
- AI integration planning
- Architecture diagram creation
- Technology stack decisions

**Day 3**: Frontend Technology & AI-Driven Development (Developers, optional Architects)
- Frontend framework evaluation
- Hands-on AI-driven development workshop
- Practical migration exercise with sample mask
- Next steps and roadmap

## Expert Role Definitions

The `/rollen` directory contains detailed role definitions for the key expert personas involved in the workshop:

**codecentric Team:**
- **UX/UI Expert**: User experience and interface design, hybrid UI concepts (conversational + forms)
- **Solution Architect**: Overall architecture, technology evaluation, migration strategy
- **System Architect**: Frontend & backend implementation details, framework choices, deployment
- **Oracle Forms Specialist**: ICIS knowledge, mask analysis, legacy migration expertise
- **Staff Frontend Developer**: Hands-on frontend development, AI-driven development, code quality
- **Staff Backend Developer**: Integration layer, REST APIs, PL/SQL integration, AI gateway, security

**WGV Side (Hypothetical):**
- **Power User / Domain Expert**: Insurance domain knowledge, current ICIS workflows, user perspective (hypothetical definition based on typical power user characteristics)

These role definitions are used to:
1. Model expert perspectives when creating workshop content
2. Ensure comprehensive coverage of different stakeholder viewpoints
3. Guide discussion topics and technical depth for each workshop day
4. Define success criteria and collaboration patterns

## Working with Workshop Materials

### Current Status
- **Committed agenda**: `20260303_commited_agend.md` (agreed with WGV for 28-30 April 2026)
- **Detailed draft**: `angebot/2026-03-02_Entwurf_Agenda_v2.md` (reference for time estimates and detailed structure)
- Workshop materials are in **German**
- Modified files in git: Check `Entwurf_Agenda.md` for recent changes
- **Role definitions**: See `/rollen` directory for expert personas (currently without workshop day-specific goals)

### When Updating Workshop Content

1. **Agenda files**: Keep both versions for reference; v2 is the active version
2. **Language**: All content should be in German
3. **Technical depth**: Balance business stakeholder and developer audiences
4. **Time estimates**: Include realistic timing for each workshop section
5. **Outputs & Decisions**: Clearly mark expected outputs and decision points for each day

### Key Stakeholders
- Herr Bechtold (WGV)
- Herr Machowetz (WGV)
- codecentric team: Herr Ponce (Sócrates), Herr Engelen

## Facilitation Methods & Frameworks

The `/facilitation` directory contains methods, frameworks, and tools for facilitating the workshop:

- **decision_frameworks.md**: Collection of decision-making frameworks from IT transformation (Weighted Decision Matrix, ADR, RICE Scoring, Technology Radar, Cynefin, etc.) with practical application guidance for each workshop day

### Tag 1 Facilitation Guides

- **tag1_domain_mapping_guide.md**: Domain-Driven Design (DDD) methodology for domain discovery (~1.5-2h):
  - Activity 1: Event Storming Light (~45-60min)
  - Activity 2: Context Mapping Interview (~30-45min)
  - Activity 3: Core Domain Chart (~15-20min)
  - Activity 4: Domain Storytelling (~20-30min)
  - Complete with guiding questions, expected outputs, templates, and integration with other Day 1 activities

- **tag1_icis_deep_dive_guide.md**: Structured information gathering on ICIS-Klassik and ICIS+ (~90-120min):
  - Part A: ICIS-Klassik (Oracle Forms) Deep Dive - 35 questions across 5 categories (~40-50min)
  - Part B: ICIS+ (Vaadin) Deep Dive - 25 questions across 4 categories (~30-40min)
  - Part C: Comparative Analysis & Migration Strategy (~20-30min)
  - 9 ready-to-use templates (service catalogs, component inventories, comparison matrices)
  - Facilitator role: WGV presents, we ask structured questions and document
  - Expected outputs: Service inventory, reusability assessment, pain points catalog, migration strategy canvas

These frameworks help us facilitate structured discussions and decision-making processes with WGV during the workshop.

## Diagrams and Context Documentation

### Available Diagrams

**Conceptual Reference**:
1. **`tier_architecture.svg`**: Generic 3-tier architecture pattern (Client-Middle-Database) in Oracle Forms context - conceptual reference without metadata, useful for understanding architectural principles

**ICIS-Specific Architectures**:
2. **`icis_oracle_forms_architektur.svg`**: Detailed Oracle Forms 3-tier architecture diagram showing UI Presentation, Application Logic, Data Manager, and PL/SQL Engine layers
3. **`architektur_schaubild_icis_gesamt.svg`**: Complete ICIS system architecture showing all components (ICIS+, Forms, APEX), external integrations (SAP, COR Life, GDV, DMS), and middleware (dated May 2022, most recent overview)
4. **`icis_plus_jee_architekture.svg`**: ICIS+ JEE architecture showing Vaadin/Sencha UI, Spring-based service layer, backend adapters (icis-anbindung, odsp-anbindung, fe-generierungs-anbindung, csipjax-persistent), and dual-database architecture (dated Feb 2021, ICIS Legacy + ICIS+ Modern)

### Technical Reference Documents

Technical reference documents and architecture interpretations explain concepts, technologies, and best practices relevant to the WGV ICIS modernization project:

**Conceptual Architecture References:**
1. **`tier_architecture.md`**: Generic 3-tier architecture pattern explanation (conceptual, no metadata) - useful for understanding architectural principles before diving into ICIS-specific implementations

**ICIS-Specific Architecture Interpretations:**
2. **`icis_oracle_forms_architektur.md`**: Interpretation of ICIS-Klassik Oracle Forms 3-tier architecture
3. **`architektur_schaubild_icis_gesamt.md`**: Interpretation of complete ICIS system architecture (May 2022, most recent)
4. **`icis_plus_jee_architekture.md`**: Interpretation of ICIS+ JEE architecture (Feb 2021, Vaadin, Spring, dual-database)

**Technical References:**
5. **`plsql_functions_vs_procedures.md`**: Oracle PL/SQL fundamentals - differences between functions and procedures (language specification vs. best practices), RETURN vs. OUT parameters, integration layer examples

### Convention: Separating Visual and Textual Documentation

- **`diagrams/` directory**: Contains only renderable diagram files (`.svg`, `.png`, etc.)
- **`context/` directory**: Contains markdown interpretations of diagrams AND technical reference documents
- **Naming convention**: Interpretation files have the same name as their diagram (e.g., `icis_oracle_forms_architektur.md` interprets `icis_oracle_forms_architektur.svg`)
- **Diagram Registry**: `context/DIAGRAM_REFERENCES.md` maintains a table mapping each interpretation to its source diagram
- **Technical References Registry**: `context/TECH_REFERENCES.md` maintains a table of all technical reference documents organized by category

This separation keeps visual assets clean while providing detailed textual explanations in a searchable format.

## Document Conventions

- Use German for all workshop materials
- Include time estimates for workshop sections (e.g., `~1.5h`)
- Mark outputs clearly: `**Output:**` and `**Entscheidung:**` (Decision)
- Consider different participant groups when structuring content
- Reference attachments in `wgv_attachments/` for context on current ICIS system
- When adding new diagrams: Create matching interpretation in `context/` and update `DIAGRAM_REFERENCES.md`
- When adding technical reference documents: Create in `context/` and update `TECH_REFERENCES.md`
