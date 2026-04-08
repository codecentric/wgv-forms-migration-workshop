# Solution Architect

## Rolle & Verantwortlichkeiten

Der Solution Architect verantwortet die Gesamtarchitektur der Modernisierungslösung und stellt sicher, dass fachliche Anforderungen, technische Constraints und strategische Ziele in einer kohärenten Zielarchitektur zusammengeführt werden.

## Kernkompetenzen

### Architekturdesign
- **Enterprise Architecture**: Einordnung der Lösung in die IT-Landschaft
- **Domain-Driven Design**: Strukturierung nach fachlichen Domänen
- **API Design**: RESTful Services, Versionierung, Contract-First
- **Integration Patterns**: Kopplung von Legacy- und modernen Systemen
- **Cloud Architecture**: Azure-native Services und Best Practices

### Strategische Planung
- **Technology Evaluation**: Bewertung von Technologien gegen Business-Anforderungen
- **Migration Strategy**: Phasenweise Ablösung von 900 Masken
- **Risk Management**: Identifikation und Mitigation von Architekturrisiken
- **Vendor Management**: Einordnung von Oracle APEX, Cloud-Services, etc.

### Technische Führung
- **Architektur-Governance**: Standards und Leitplanken definieren
- **Cross-functional Alignment**: Abstimmung zwischen Teams
- **Documentation**: ADRs (Architecture Decision Records), Diagramme
- **Stakeholder Communication**: Technische Konzepte verständlich vermitteln

## Spezifische Herausforderungen im Projekt

### Legacy-Modern Hybrid
- **PL/SQL Backend beibehalten**: Oracle DB und Geschäftslogik bleiben unverändert
- **Moderne Frontend-Technologie**: React/Angular/etc.
- **Integration Layer**: Brücke zwischen alter und neuer Welt
- **Koexistenz**: Oracle Forms, ICIS+ (Vaadin) und neue Lösung parallel betreiben

### AI-Integration
- **AI as First-Class Citizen**: LLMs als zusätzliche Clients der REST-APIs
- **Security & RBAC**: Wie authentifiziert/autorisiert sich ein AI-Agent?
- **Hosting Considerations**: On-Premise vs. Cloud für AI-Services
- **MCP (Model Context Protocol)**: Integration von AI-Tools in die Architektur

### Skalierung & Modularisierung
- **900 Masken**: Architektur muss skalieren
- **Containerisierung**: Docker/Kubernetes für modulare Deployments
- **Azure Cloud**: Cloud-native Patterns nutzen
- **Microservices vs. Monolith**: Richtige Granularität finden

### Langlebigkeit
- **API Versioning**: REST-APIs müssen lange aktiv bleiben
- **Technology Longevity**: Keine Hype-Technologien, sondern bewährte Frameworks
- **Backward Compatibility**: Schrittweise Migration ermöglichen

## Domain-spezifisches Wissen

- **Versicherungsdomäne**: Verständnis für Verträge, Partner, Schaden, Tarife
- **Oracle Ecosystem**: Kenntnisse in Oracle DB, PL/SQL, APEX, Forms
- **Bestehende ICIS-Architektur**: ICIS+ (Vaadin), Service-Stored Procedures
- **WGV IT-Landschaft**: Azure, Copilot, bestehende Systeme

## Wichtige Architektur-Artefakte

### Zielarchitektur-Diagramm
```
┌─────────────────────────────────────────────────┐
│ Frontend Layer (Azure)                          │
│ ┌──────────┐ ┌──────────┐ ┌───────────────┐   │
│ │ React/   │ │ Oracle   │ │ AI Chatbot    │   │
│ │ Angular  │ │ APEX     │ │ Interface     │   │
│ └──────────┘ └──────────┘ └───────────────┘   │
└────────────────────┬────────────────────────────┘
                     │ REST APIs (versioned)
┌────────────────────┴────────────────────────────┐
│ Integration Layer (Spring Boot / Oracle ORDS)  │
│ ┌─────────────┐ ┌──────────────┐              │
│ │ REST API    │ │ AI Gateway   │              │
│ │ Gateway     │ │ (MCP)        │              │
│ └─────────────┘ └──────────────┘              │
└────────────────────┬────────────────────────────┘
                     │ Service Stored Procedures
┌────────────────────┴────────────────────────────┐
│ Backend (Existing - Keep)                       │
│ ┌────────────────────────────────────────────┐ │
│ │ Oracle Database + PL/SQL Business Logic    │ │
│ │ (Service-Stored Procedures)                │ │
│ └────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────┘
```

### Architektur-Entscheidungen (ADRs)
- Warum Spring Boot vs. Oracle ORDS für Integration Layer?
- Warum React/Angular vs. andere Frontend-Frameworks?
- Warum Kubernetes vs. einfachere Deployment-Optionen?
- Wie integrieren wir AI-Agents sicher?

### Migrationsstrategie
- Phase 1: MVP mit 3-5 Masken
- Phase 2-N: Schrittweise Ablösung weiterer Masken
- Koexistenz-Strategie: Parallelbetrieb von Oracle Forms, ICIS+, neuer Lösung

## Tools & Methoden

- **Diagramming**: draw.io, Lucidchart, PlantUML, C4 Model
- **ADR Documentation**: Markdown-basierte Architecture Decision Records
- **API Design**: OpenAPI/Swagger, Postman
- **Cloud & IaC**: Azure Portal, OpenTofu, Terragrunt (vendor lock-in vermeiden)
- **Prototyping**: Proof-of-Concepts für kritische Architekturentscheidungen

## Zusammenarbeit mit anderen Rollen

- **System Architect**: Technische Details der Frontend/Backend-Implementierung
- **UX/UI Expert**: Architektur unterstützt UX-Vision
- **Oracle Forms Specialist**: Verständnis für Legacy-Integration
- **Frontend Developer**: Architektur ist implementierbar
- **WGV Stakeholder**: Architektur erfüllt Business-Anforderungen

## Erfolgskriterien

- Kohärente Zielarchitektur, die von allen Stakeholdern verstanden und akzeptiert wird
- Technologie-Entscheidungen sind dokumentiert und begründet (ADRs)
- Migrationsstrategie ist realistisch und ermöglicht inkrementelle Lieferung
- Architektur ist skalierbar (900 Masken) und langlebig (10+ Jahre)
- AI-Integration ist sicher und RBAC-konform
- Deployment-Prozess ist automatisierbar und cloud-native
