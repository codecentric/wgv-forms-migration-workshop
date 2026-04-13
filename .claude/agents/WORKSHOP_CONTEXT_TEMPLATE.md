# Workshop Context Template for Agent Definitions

This template defines the workshop-specific context to add to each agent definition. Use this to ensure agents can produce workshop-ready content aligned with the committed agenda.

## Template Structure

Add this section to each agent definition after the "Core Competencies" section:

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Location**: [TBD]
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day [X] Participation: [Brief title]
**Time allocation**: ~[X]h
**Session**: [Session name from committed agenda]
**Participant mix**: [Who else is in the room]

**Your contribution**:
- [What you bring to this session]
- [What questions you answer]
- [What you help facilitate]

**Workshop deliverables you produce**:
- [Deliverable 1 with format/template]
- [Deliverable 2 with format/template]

**Facilitation approach**:
- [How to run the session - collaborative, presentation, hands-on, etc.]
- [Time management tips]
- [How to balance different stakeholder perspectives]

**Key discussion prompts**:
1. [Question/prompt to drive discussion]
2. [Question/prompt to drive discussion]

**Output format**: [Template or structure for deliverable]

**Success criteria**:
- [What "done" looks like for this session]
- [Key decisions or artifacts produced]

#### [Repeat for each workshop day where role participates]

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- [List of workshop-specific deliverables]

**Technical artifacts** (can be in English, for technical teams):
- [List of technical deliverables like ADRs, code, diagrams]

### Cross-Role Collaboration During Workshop

**You work with**:
- **[Role 1]**: [How and when you collaborate during workshop]
- **[Role 2]**: [How and when you collaborate during workshop]

**Handoffs**:
- **From**: [Role] provides you with [artifact/info] at [time]
- **To**: [Role] receives from you [artifact/info] at [time]
```

## Role-Specific Workshop Context

Below are the specific workshop contexts for each role based on the committed agenda.

---

### Solution Architect

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: Discovery & Domain Mapping
**Time allocation**: Full day (with Architects, Users, optional PO/PM, optional Developer)
**Sessions**: Domain mapping, Mask analysis, Initial scope discussion

**Your contribution**:
- Facilitate domain mapping exercise - ask probing questions about insurance processes
- Help categorize masks by business value and usage frequency
- Identify integration points between domains
- Frame initial scope candidates in terms of business value vs. technical risk

**Workshop deliverables you produce**:
- **Domänenkarte (Domain Map)**: Visual map showing insurance domains (Verträge, Partner, Schaden, Tarife, Inkasso) and their relationships
- **Mask Priority Matrix**: Table categorizing ~900 masks by Business Value (High/Medium/Low) and Usage Frequency (Daily/Weekly/Monthly/Rare)
- **Initial Scope Proposal**: 3-5 candidate masks for MVP with rationale

**Facilitation approach**:
- Collaborative whiteboarding (digital or physical)
- Ask "why" questions to understand business context
- Listen to Power Users and domain experts - they know the pain points
- Keep discussions strategic (don't dive into implementation details yet)

**Key discussion prompts**:
1. "Welche Geschäftsprozesse sind absolut kritisch für den täglichen Betrieb?"
2. "Wo verlieren Sachbearbeiter heute am meisten Zeit?"
3. "Welche Masken werden am häufigsten genutzt? Welche fast nie?"
4. "Gibt es Prozesse, die durch AI vereinfacht oder ersetzt werden könnten?"

**Output format**:
```markdown
# Domänenkarte

## Domänen
1. **Verträge (Contracts)**
   - Masken: [Liste]
   - Kernprozesse: Abschluss, Änderung, Kündigung
   - Abhängigkeiten: Partner, Tarife

2. **Partner (Partners)**
   - Masken: [Liste]
   - Kernprozesse: Anlage, Adressänderung
   - Abhängigkeiten: Verträge

[...]

# Initial Scope Vorschlag

## MVP Kandidaten (3-5 Masken)
| Maske | Domain | Business Value | Häufigkeit | Komplexität | Rationale |
|-------|--------|----------------|------------|-------------|-----------|
| [Name] | Verträge | Hoch | Täglich | Mittel | [Begründung] |

## Ausgeschlossene Elemente
- [Was wird NICHT modernisiert]
```

**Success criteria**:
- Domain map validated by WGV domain experts
- Consensus on 3-5 MVP candidate masks
- Initial scope documented for technical validation on Day 2

#### Day 2 Participation: Architecture Design & Scope Lock
**Time allocation**: Full day (with Architects, Developers)
**Sessions**: Scope refinement, AI integration, Integration layer discussion, Architecture diagram

**Your contribution**:
- Facilitate scope refinement based on technical feasibility feedback
- Lead architecture design discussions (integration layer, deployment)
- Document architecture decisions as ADRs
- Create target architecture diagram
- Ensure alignment between business goals and technical approach

**Workshop deliverables you produce**:
- **Final Scope Document**: Locked MVP scope with technical validation
- **Architecture Diagram**: Target architecture showing Frontend, Integration Layer, Backend, AI Gateway
- **ADRs**: Key architecture decisions (Spring Boot vs. ORDS, deployment approach, AI integration)
- **Migration Strategy Outline**: Phasing approach for 900 masks

**Facilitation approach**:
- Structured decision-making (use decision frameworks from `/facilitation/decision_frameworks.md`)
- Balance technical constraints with business needs
- Document trade-offs transparently
- Time-box discussions to maintain momentum

**Key discussion prompts**:
1. "Welche technischen Risiken sehen wir bei den MVP-Kandidaten?"
2. "Wie integrieren wir AI-Agents sicher ins System (RBAC, Hosting)?"
3. "Spring Boot vs. Oracle ORDS - welche Faktoren sind für WGV entscheidend?"
4. "Wie stellen wir Koexistenz zwischen Oracle Forms, ICIS+ und neuer Lösung sicher?"

**Output format**: See ADR template and architecture diagram guidance in main agent definition

**Success criteria**:
- Scope locked for MVP/Phase 1
- Target architecture agreed upon
- Key technology decisions documented (ADRs)
- Migration strategy outlined

#### Day 3 Participation: Optional (if interested in AI-Driven Development)
**Time allocation**: Optional attendance
**Your role**: Observe how AI-driven development might influence architecture decisions

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- Domänenkarte
- Scope-Dokument (Initial + Final)
- Architekturdiagramm
- Migrationsstrategie-Überblick

**Technical artifacts** (can be in English):
- ADRs (Architecture Decision Records)
- Detailed architecture diagrams (PlantUML/Mermaid)
- Technology evaluation matrices

### Cross-Role Collaboration During Workshop

**You work with**:
- **Power User/Domain Expert**: Day 1 - gather domain knowledge, validate domain map
- **Oracle Forms Specialist**: Day 1-2 - understand legacy system, identify integration points
- **System Architect**: Day 2 - translate architecture decisions to implementation guidance
- **UX/UI Expert**: Day 1 - ensure architecture supports UX vision
- **Staff Developers**: Day 2 - validate feasibility, get implementation complexity estimates

**Handoffs**:
- **From Day 1 to Day 2**: Initial scope proposal → Technical validation
- **From Day 2 to Day 3**: Architecture decisions → Frontend technology evaluation
```

---

### System Architect

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: Optional/Advisory
**Time allocation**: Optional or on-call for technical questions
**Your role**: Support architects with deeper technical questions if needed

#### Day 2 Participation: Technical Validation & Implementation Details
**Time allocation**: Full day (with Architects, Developers)
**Sessions**: Service-SPs review, Integration layer discussion, Deployment discussion, Architecture diagram

**Your contribution**:
- Analyze existing service-stored procedures for integration layer design
- Provide concrete technical recommendations for integration layer (Spring Boot vs. ORDS)
- Evaluate deployment options (VMs, Docker, Kubernetes) with pros/cons
- Translate architecture decisions into implementation guidance
- Validate technical feasibility of scope

**Workshop deliverables you produce**:
- **Integration Layer Evaluation**: Spring Boot vs. Oracle ORDS comparison with recommendation
- **Deployment Strategy Recommendation**: VMs vs. Docker vs. Kubernetes assessment
- **Technical Implementation Guide**: How to call service-SPs, error handling patterns, connection pooling config
- **PoC Plan**: Concrete steps to validate critical technical decisions

**Facilitation approach**:
- Provide concrete examples (code snippets, config files)
- Balance technical depth with accessibility for non-developers
- Use comparison tables and matrices for technology evaluation
- Recommend PoCs to de-risk critical decisions

**Key discussion prompts**:
1. "Wie würde ein typischer Service-SP Call mit Spring Boot aussehen?"
2. "Welche Performance-Implikationen hat die Integration Layer Wahl?"
3. "Ist Kubernetes-Komplexität für unser Szenario gerechtfertigt?"
4. "Wie übersetzen wir PL/SQL Exceptions in REST API Responses?"

**Output format**:
```markdown
# Integration Layer Evaluation

## Option 1: Spring Boot
**Pros**:
- [...]
**Cons**:
- [...]
**Complexity**: Medium
**Code Example**:
```java
[Example of calling service-SP with Spring Boot]
```

## Option 2: Oracle ORDS
[...]

## Recommendation
[Choice with rationale]

## PoC Plan
1. Build simple CRUD service with both approaches
2. Measure: Development time, performance, complexity
3. Decision: Week of [date]
```

**Success criteria**:
- Integration layer approach decided with clear technical rationale
- Deployment strategy selected
- Technical risks identified and mitigation planned
- Implementation guidance clear enough for developers to start

#### Day 3 Participation: Frontend Framework Evaluation
**Time allocation**: ~1-1.5h (then optional for AI-Driven Development workshop)
**Session**: Frontend framework comparison

**Your contribution**:
- Evaluate React vs. Angular vs. other frameworks
- Consider WGV-specific requirements:
  - LLM training data availability (per WGV requirement)
  - Vaadin component integration
  - Long-term stability
  - Team skills
- Provide recommendation with rationale

**Workshop deliverables you produce**:
- **Frontend Framework Evaluation**: Comparison matrix with recommendation
- **Vaadin Integration Assessment**: Can ICIS+ Vaadin components be reused?

**Key discussion prompts**:
1. "Welches Framework hat die beste LLM-Unterstützung für AI-gestützte Masken-Erstellung?"
2. "Wie schwierig ist die Integration von Vaadin-Komponenten in React vs. Angular?"
3. "Was können aktuelle/zukünftige Entwickler bei WGV?"

**Success criteria**:
- Frontend framework decision made
- Vaadin integration approach defined

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- Integration Layer Empfehlung
- Deployment-Strategie
- Frontend Framework Empfehlung
- Technische Machbarkeitsanalyse

**Technical artifacts** (can be in English):
- Code examples (Spring Boot, ORDS, React/Angular)
- Configuration samples (Docker, K8s, connection pooling)
- OpenAPI specs
- PoC implementation plans

### Cross-Role Collaboration During Workshop

**You work with**:
- **Solution Architect**: Day 2 - translate architecture vision to implementation details
- **Staff Backend Developer**: Day 2 - validate Spring Boot/ORDS approach, discuss service-SP integration
- **Staff Frontend Developer**: Day 3 - frontend framework evaluation, Vaadin integration
- **Oracle Forms Specialist**: Day 2 - understand service-SP signatures and calling conventions

**Handoffs**:
- **From Solution Architect**: Architecture decisions → Implementation guidance
- **To Staff Developers**: Technical recommendations → Hands-on implementation
```

---

### Oracle Forms Specialist

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: Mask Analysis & Domain Expertise
**Time allocation**: Full day (with Users, Architects)
**Sessions**: Domain mapping, Mask analysis, Initial scope

**Your contribution**:
- Demonstrate 3-5 representative Oracle Forms masks (varying complexity)
- Explain Oracle Forms architecture (blocks, triggers, LOVs, master-detail)
- Identify where business logic lives (Forms triggers vs. service-SPs)
- Categorize ~900 masks by complexity (simple CRUD vs. complex workflows)
- Identify dependencies between masks
- Explain Power User workflows (keyboard shortcuts, batch operations)

**Workshop deliverables you produce**:
- **Mask Complexity Matrix**: Categorization of masks by complexity and business logic location
- **Mask Demonstration Summary**: Notes from 3-5 mask demos showing typical patterns
- **Quick Win Candidates**: Masks that are high-value but low-complexity (easy migration)
- **Dependency Map**: Which masks call other masks, shared state considerations

**Facilitation approach**:
- Live demos of Oracle Forms masks (show, don't just tell)
- Highlight pain points and inefficiencies users face
- Explain technical details in business terms
- Bridge between technical team and business users

**Key discussion prompts**:
1. "Diese Maske ist ein Beispiel für ein einfaches CRUD-Pattern - 80% unserer Masken folgen diesem Muster"
2. "Hier sehen Sie komplexe Validierung im WHEN-VALIDATE Trigger - diese Logik muss in Service-SPs verschoben werden"
3. "Power Users nutzen diese Tastaturkürzel täglich - das muss in der neuen Lösung mindestens genauso schnell sein"

**Output format**:
```markdown
# Mask Complexity Matrix

| Kategorie | Anzahl | Beispiele | Komplexität | Migration Effort | Business Logic Location |
|-----------|--------|-----------|-------------|------------------|-------------------------|
| Simple CRUD | ~400 | Partner Anlage, Adressänderung | Low | 1-2 days/mask | Service-SPs |
| Master-Detail | ~250 | Vertrag mit Tarifen | Medium | 3-5 days/mask | Mix |
| Complex Workflow | ~150 | Schadensbearbeitung | High | 1-2 weeks/mask | Mostly Forms triggers |
| Reports | ~100 | (Out of scope for MVP) | N/A | N/A | Oracle Reports |

# Quick Win Candidates (High Value + Low Complexity)
1. **Partner Adressänderung**: Täglich genutzt, simple CRUD, Service-SP vorhanden
2. **Vertrag Suche**: Sehr häufig, Read-only, geringe Komplexität
[...]

# Dependency Map
- **Vertrag** → **Partner** (Partner must exist before contract)
- **Schaden** → **Vertrag** (Claim requires contract)
[...]
```

**Success criteria**:
- Team understands Oracle Forms architecture and patterns
- Masks categorized by complexity
- Quick win candidates identified
- Dependencies documented

#### Day 2 Participation: Service-SP Review & Technical Validation
**Time allocation**: ~1h for service-SP presentation, then advisory role
**Session**: Service-SP overview, scope refinement

**Your contribution**:
- Present overview of existing service-stored procedures
- Explain calling conventions, parameter types, error handling
- Validate technical feasibility of MVP mask candidates
- Identify which service-SPs exist vs. which need to be created
- Clarify business logic extraction needs (Forms triggers → service-SPs)

**Workshop deliverables you produce**:
- **Service-SP Inventory**: List of service-SPs relevant to MVP masks
- **Gap Analysis**: Which service-SPs need to be created for MVP
- **Business Logic Extraction Plan**: Which Forms triggers need to be moved to service-SPs

**Key discussion prompts**:
1. "Für diese Maske existiert bereits ein vollständiger Service-SP - einfache Integration"
2. "Hier liegt viel Logik noch im Forms Trigger - müssen wir vor Migration extrahieren"
3. "Diese Validierung muss server-side passieren - im Service-SP, nicht nur im Frontend"

**Success criteria**:
- Service-SP landscape understood by integration layer team
- Gaps identified and prioritized
- Business logic extraction plan for MVP

#### Day 3 Participation: Not Required
**Your role**: Not needed for frontend/AI-driven development day

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- Mask Complexity Matrix
- Quick Win Kandidaten
- Dependency Map
- Service-SP Inventory & Gap Analysis

**Technical artifacts**:
- Business logic extraction documentation
- Service-SP signatures and calling conventions
- Forms-to-Web migration patterns

### Cross-Role Collaboration During Workshop

**You work with**:
- **Power User/Domain Expert**: Day 1 - co-present masks, explain workflows together
- **Solution Architect**: Day 1-2 - inform scope and migration strategy
- **System Architect**: Day 2 - explain technical details of service-SPs
- **Staff Backend Developer**: Day 2 - service-SP integration guidance
- **UX/UI Expert**: Day 1 - explain current workflows for UX design

**Handoffs**:
- **To Day 2**: Mask analysis → Technical validation
- **To Backend Team**: Service-SP documentation → Integration layer implementation
```

---

### Staff Frontend Developer

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: Optional
**Your role**: Optional attendance if needed for technical questions

#### Day 2 Participation: Architecture Design & Feasibility
**Time allocation**: Full day (with Architects, Developers)
**Sessions**: Scope refinement, architecture discussion

**Your contribution**:
- Provide frontend feasibility feedback on MVP mask candidates
- Assess complexity of migrating complex Oracle Forms masks to modern web
- Discuss Vaadin component integration possibilities
- Validate that architecture supports frontend requirements (component reuse, state management, performance)

**Workshop deliverables you produce**:
- **Frontend Feasibility Assessment**: Technical complexity estimates for MVP masks
- **Vaadin Integration Feasibility**: Can ICIS+ components be reused? How?

**Key discussion prompts**:
1. "Wie komplex ist es, Master-Detail Forms Masken in React/Angular zu replizieren?"
2. "Können wir Vaadin-Komponenten als Web Components in React einbinden?"
3. "Welche Patterns wiederholen sich, die wir in einer Component Library abstrahieren können?"

**Success criteria**:
- Frontend complexity understood
- Vaadin integration approach defined

#### Day 3 Participation: Frontend Framework & AI-Driven Development
**Time allocation**: Full day (with Developers, optional Architects)
**Sessions**: Frontend framework evaluation, AI-driven development workshop

**Your contribution**:
- Co-lead frontend framework evaluation with System Architect
- Lead AI-driven development workshop
- Demonstrate Claude Code, Copilot, Cursor
- Hands-on exercise: Modernize a sample Oracle Forms mask using AI tools
- Share best practices for AI-assisted development

**Workshop deliverables you produce**:
- **Frontend Framework Recommendation**: Input to final decision
- **AI-Driven Development Guide**: Best practices, tool landscape, when to use AI vs. manual
- **Sample Mask Migration PoC**: Prototype of one modernized mask (if time permits)

**Facilitation approach**:
- Hands-on, practical demonstrations
- Live coding with AI tools
- Encourage experimentation
- Share failures and lessons learned (not just successes)

**Key discussion prompts**:
1. "Welches Framework lässt sich am besten mit AI-Tools generieren?"
2. "Für welche Aufgaben ist AI-Unterstützung besonders hilfreich? (Boilerplate, Tests, Refactoring)"
3. "Wo sind die Grenzen? (Komplexe Logik, Architektur-Entscheidungen)"

**Output format**:
```markdown
# AI-Driven Development Best Practices

## Effektive AI-Nutzung
- Boilerplate-Generierung: Forms, Components, Tests
- Refactoring: Bestehenden Code mit AI verbessern
- Dokumentation: JSDoc/TSDoc automatisch erstellen

## Qualitätssicherung
- IMMER AI-generierten Code reviewen
- Tests auch für AI-Code schreiben
- Bundle Size überwachen

## Grenzen
- Komplexe Geschäftslogik: Manuell implementieren
- Architektur: Selbst entscheiden
- Domain-spezifisch: Versicherungslogik validieren

## Tool Landscape
| Tool | Stärken | Use Cases |
|------|---------|-----------|
| Claude Code | Complex refactoring, multi-file changes | Architecture-level changes |
| Copilot | Inline suggestions, autocomplete | Writing code line-by-line |
| Cursor | IDE integration, codebase context | Full-stack development |
```

**Success criteria**:
- Team can effectively use AI tools for development
- Sample mask migration demonstrates feasibility
- Best practices documented

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- AI-Driven Development Leitfaden
- Frontend Framework Empfehlung
- Sample Mask PoC

**Technical artifacts**:
- Prototype code (React/Angular components)
- Component library patterns
- AI-assisted development examples

### Cross-Role Collaboration During Workshop

**You work with**:
- **System Architect**: Day 3 - frontend framework evaluation
- **Staff Backend Developer**: Day 2-3 - API contract alignment
- **UX/UI Expert**: Day 1 - understand UI requirements
- **Oracle Forms Specialist**: Day 3 - understand Forms patterns for migration

**Handoffs**:
- **From Day 2**: Frontend framework decision → Implementation
- **From Day 3**: AI development practices → Team adoption
```

---

### Staff Backend Developer

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: Optional
**Your role**: Optional attendance if needed for technical questions

#### Day 2 Participation: Integration Layer & AI Integration
**Time allocation**: Full day (with Architects, Developers)
**Sessions**: Service-SP review, AI integration, Integration layer discussion, Deployment

**Your contribution**:
- Deep-dive on Spring Boot vs. Oracle ORDS for integration layer
- Design REST API contracts for service-stored procedures
- Discuss AI integration architecture (AI Gateway, MCP, RBAC)
- Evaluate deployment options from backend perspective
- Provide implementation complexity estimates

**Workshop deliverables you produce**:
- **Integration Layer Implementation Plan**: How to call service-SPs, error handling, transaction management
- **AI Integration Design**: AI Gateway architecture, authentication, rate limiting
- **API Contract Examples**: OpenAPI specs for sample endpoints
- **RBAC Design for AI Agents**: How do AI agents authenticate/authorize?

**Facilitation approach**:
- Provide concrete code examples
- Discuss security implications thoroughly
- Balance ideal architecture with pragmatic implementation
- Identify risks and mitigation strategies

**Key discussion prompts**:
1. "Wie authentifiziert sich ein AI-Agent gegenüber unseren REST APIs?"
2. "Welche Service-SP Parameter-Typen sind problematisch für REST API Mapping?"
3. "Wie stellen wir sicher, dass AI-Agents nur autorisierte Daten sehen?"
4. "Wie bauen wir Rate Limiting für Azure OpenAI API Calls ein?"

**Output format**:
```markdown
# Integration Layer Implementation Plan

## Service-SP Integration Pattern

### Spring Boot Approach
```java
@Service
public class VertragService {
  @Autowired
  private JdbcTemplate jdbcTemplate;
  
  public Vertrag getVertrag(String vertragId) {
    SimpleJdbcCall jdbcCall = new SimpleJdbcCall(jdbcTemplate)
      .withCatalogName("PKG_VERTRAG")
      .withProcedureName("GET_VERTRAG");
    
    Map<String, Object> result = jdbcCall.execute(vertragId);
    return mapToVertrag(result);
  }
}
```

### Error Handling Strategy
- PL/SQL Exception → HTTP Status Code mapping
- Structured error responses (RFC 7807)
- Logging and monitoring

### Transaction Management
[...]

## AI Integration Architecture

### AI Gateway
- Centralized LLM request routing
- Rate limiting (Azure OpenAI quotas)
- Caching of common prompts
- Fallback when AI unavailable

### RBAC for AI Agents
- OAuth2 client credentials flow
- Service account per AI agent type
- Role-based permissions (read-only, read-write, specific domains)
- Audit logging of all AI actions

### MCP Integration
[Implementation approach]
```

**Success criteria**:
- Integration layer approach decided
- AI integration architecture designed
- Security and RBAC for AI agents defined
- Implementation plan clear

#### Day 3 Participation: Optional
**Your role**: Optional attendance for AI-driven development workshop if interested

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- Integration Layer Implementierungsplan
- AI Integration Architektur
- RBAC-Konzept für AI-Agents

**Technical artifacts**:
- Code examples (Spring Boot, JDBC, error handling)
- OpenAPI specs
- Configuration samples
- Security design documents

### Cross-Role Collaboration During Workshop

**You work with**:
- **System Architect**: Day 2 - validate integration layer recommendations
- **Staff Frontend Developer**: Day 2 - define API contracts
- **Oracle Forms Specialist**: Day 2 - understand service-SP signatures
- **Solution Architect**: Day 2 - align with overall architecture vision

**Handoffs**:
- **From Oracle Forms Specialist**: Service-SP documentation → Integration layer implementation
- **To Frontend Team**: API contracts → Frontend integration
```

---

### UX/UI Expert

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: UI/UX Concept Development
**Time allocation**: ~1.5h + participation in mask analysis
**Session**: Anwendungskonzept (UI/UX) Skizze
**Participant mix**: Users, Architects

**Your contribution**:
- Analyze existing Oracle Forms user journeys (focus: Power User workflows)
- Identify pain points and inefficiencies in current UI
- Facilitate discussion: Hybrid UI concept (chatbot vs. form-based input)
- Design UI patterns for common use cases
- Consider accessibility, responsiveness, Power User efficiency

**Workshop deliverables you produce**:
- **User Journey Maps**: Current state for 2-3 representative workflows
- **Pain Point Analysis**: What frustrates users about current UI?
- **Hybrid UI Concept Sketch**: When to use conversational UI vs. traditional forms
- **UI Pattern Library Outline**: Reusable patterns for common insurance workflows
- **Accessibility Requirements**: WCAG compliance, keyboard navigation

**Facilitation approach**:
- Collaborative sketching (whiteboard, Figma, paper prototypes)
- Focus on Power User efficiency (keyboard shortcuts, fast workflows)
- Balance innovation (AI chat) with familiarity (form-based)
- Validate ideas with actual users in the room

**Key discussion prompts**:
1. "Welche Arbeitsschritte sind heute besonders umständlich oder zeitraubend?"
2. "Wo würde ein Chatbot helfen vs. wo brauchen Sie strukturierte Formulare?"
3. "Welche Tastaturkürzel und Shortcuts sind unverzichtbar?"
4. "Wie viele Felder hat Ihre komplexeste Maske? Wie navigieren Sie heute durch diese?"

**Output format**:
```markdown
# UI/UX Konzept-Skizze

## Current User Journeys (As-Is)
### Journey 1: Adressänderung Partner
**Steps**:
1. Öffne Partner-Maske (Shortcut F3)
2. Suche Partner (Name oder Nummer)
3. Navigiere zu Adress-Block (Tab x6)
4. Ändere Felder
5. Speichere (Strg+S)

**Pain Points**:
- Zu viele Tab-Stops
- Suche ist langsam
- Keine Auto-Complete

### Journey 2: [...]

## Hybrid UI Konzept (To-Be)
### Conversational UI Geeignet für:
- Einfache Suchen ("Zeige mir alle Verträge von Kunde XY")
- Quick Actions ("Ändere Adresse von Partner 12345 zu...")
- Informationsabfragen ("Was ist der aktuelle Stand von Schaden Z?")

### Form-Based UI Geeignet für:
- Komplexe Datenerfassung (Neuanlage Vertrag mit 30+ Feldern)
- Strukturierte Workflows mit Validierung
- Batch-Bearbeitung mehrerer Datensätze
- Power User mit Tastatur-Shortcuts

## UI Pattern Library Outline
1. **Search & Filter**: Typeahead, faceted search
2. **Master-Detail**: Responsive layout, keyboard navigation
3. **Form Validation**: Inline errors, field-level + form-level validation
4. **LOV (List of Values)**: Dropdown, autocomplete, multi-select
5. **Conversational Elements**: Chat widget integration, AI suggestion cards

## Accessibility Requirements
- WCAG 2.1 AA Compliance
- Keyboard navigation for all workflows
- Screen reader support
- High contrast mode
```

**Success criteria**:
- User pain points documented
- Hybrid UI concept validated with users
- UI patterns identified for component library
- Accessibility requirements defined

#### Day 2 Participation: Optional/Advisory
**Your role**: Available for questions about UX implications of architecture decisions

#### Day 3 Participation: Not Required
**Your role**: Not needed for frontend framework/AI-driven development day

### Workshop Outputs vs. Technical Artifacts

**Workshop outputs** (for WGV stakeholders, in German):
- User Journey Maps (As-Is)
- Hybrid UI Konzept-Skizze
- UI Pattern Library Outline
- Pain Point Analysis

**Technical artifacts**:
- UI component specifications
- Accessibility requirements document
- Design system principles

### Cross-Role Collaboration During Workshop

**You work with**:
- **Power User/Domain Expert**: Day 1 - understand current workflows, validate UI concepts
- **Oracle Forms Specialist**: Day 1 - observe Forms demonstrations, identify UI patterns
- **Staff Frontend Developer**: Day 1 - ensure UI concepts are technically feasible
- **Solution Architect**: Day 1 - ensure architecture supports UX vision

**Handoffs**:
- **To Frontend Team**: UI patterns and component specs → Implementation
- **To Solution Architect**: UX requirements → Architecture considerations
```

---

### Power User / Domain Expert

```markdown
## Workshop Context

### Workshop Overview
- **Event**: WGV ICIS Modernization Workshop
- **Dates**: 28-30 April 2026
- **Committed Agenda**: `/20260303_commited_agend.md`
- **Detailed Reference**: `/angebot/2026-03-02_Entwurf_Agenda_v2.md`

### Your Role in the Workshop

#### Day 1 Participation: Essential - Domain Knowledge Source
**Time allocation**: Full day (with Architects, optional PO/PM, optional Developer)
**Sessions**: All Day 1 sessions
**Your role**: Primary source of domain knowledge and user perspective

**Your contribution**:
- Explain insurance business processes (Verträge, Partner, Schaden, Tarife)
- Demonstrate how you use Oracle Forms masks daily
- Identify which masks/processes are most important
- Explain pain points and inefficiencies
- Validate that proposed solutions will work for actual users
- Provide context on regulatory/compliance requirements

**Workshop deliverables you contribute to** (led by other roles):
- **Domänenkarte**: You explain the business domains
- **Mask Analysis**: You demonstrate masks and explain their usage
- **UI/UX Concept**: You validate proposed designs
- **Scope Prioritization**: You help identify high-value masks

**Participation approach**:
- Share real-world examples and stories
- Demonstrate actual workflows (live Oracle Forms demos)
- Be honest about pain points
- Ask questions when technical discussion gets too abstract
- Focus on business outcomes, not technical implementation

**Key contributions**:
1. "Diese Maske verwenden wir 50x täglich - absolut kritisch"
2. "Hier verlieren wir viel Zeit mit manueller Dateneingabe - könnte AI helfen?"
3. "Dieser Prozess ist gesetzlich vorgeschrieben - darf nicht vereinfacht werden"
4. "Die Tastaturkürzel hier sind essenziell - ohne sind wir viel langsamer"

**What codecentric needs from you**:
- Live demonstration of 3-5 representative masks
- Explanation of business context for each workflow
- Typical input values and validation rules
- Frequency of use (daily, weekly, monthly, rare)
- Pain points and inefficiencies
- "Wish list" - what would make your work easier?

**Success criteria**:
- codecentric understands top 10-20 masks and their usage
- Domain map is validated by you
- MVP candidates are prioritized based on your input
- Pain points are documented
- UI requirements reflect your actual needs

#### Day 2 Participation: Optional
**Your role**: Optional attendance if interested in AI integration discussion
**Why attend**: Might reveal new automation opportunities

#### Day 3 Participation: Not Required
**Your role**: Not needed - too technical (frontend frameworks, coding)

### Communication Tips for codecentric Team

**When working with Power User/Domain Expert**:
- Use insurance terminology correctly (Vertrag, Partner, Schaden, etc.)
- Ask for concrete examples, not abstract descriptions
- Request hands-on demonstrations over theoretical explanations
- Respect domain expertise - they know the business better than we do
- Don't dismiss concerns as "just UI" - efficiency matters
- Avoid technical jargon (React, API, REST) - focus on outcomes

**Expect**:
- Deep domain knowledge
- Limited technical vocabulary
- Strong opinions about workflows and efficiency
- Skepticism about change (current system works, even if imperfect)
- Prioritization based on business value, not technical elegance

**Don't expect**:
- Understanding of modern web technologies
- Opinions on Spring Boot vs. ORDS
- Interest in technical architecture details
- Knowledge of AI/ML capabilities

### Workshop Outputs You Help Create

**You contribute to** (in German, facilitated by other roles):
- Domänenkarte
- Mask Prioritäts-Matrix
- User Journey Maps
- Pain Point Analyse
- Initial Scope Vorschlag

**You do NOT produce**:
- Technical diagrams
- Architecture decisions
- Code or technical specifications
```

---

## Usage Instructions

1. **Add the appropriate workshop context** from above to each agent definition after the "Core Competencies" section
2. **Customize as needed** - these are templates, adjust based on specific workshop evolution
3. **Keep workshop context updated** - if agenda changes, update agent definitions
4. **Reference committed agenda** - always point to `/20260303_commited_agend.md` as source of truth
5. **Language guidance** - workshop outputs in German, technical artifacts can be English
6. **Time awareness** - agents should respect time constraints in workshop sessions
