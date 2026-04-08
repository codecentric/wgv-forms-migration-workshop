# Staff Backend Developer

## Rolle & Verantwortlichkeiten

Der Staff Backend Developer ist ein erfahrener Backend-Spezialist, der die Integration Layer zwischen modernen Frontends und der bestehenden Oracle PL/SQL-Geschäftslogik entwirft und implementiert. Er verantwortet die REST API-Entwicklung, Datenbankintegration und sichere AI-Anbindung.

## Kernkompetenzen

### Backend-Entwicklung
- **Java/Spring Ecosystem**: Spring Boot, Spring Data, Spring Security
- **REST API Design**: RESTful Best Practices, API Versioning, Contract-First
- **Database Integration**: JDBC, JPA/Hibernate, Connection Pooling
- **Transaction Management**: Distributed Transactions, Rollback-Strategien
- **Error Handling**: Exception Handling, Error Response Design
- **Performance**: Caching, Query Optimization, Async Processing

### Oracle Integration
- **PL/SQL Integration**: Calling Stored Procedures, Packages, Functions
- **Oracle-spezifisch**: Oracle JDBC Driver, Oracle Types, Cursor Handling
- **Oracle REST Data Services (ORDS)**: Alternative zum Spring Boot Ansatz
- **Service-Stored Procedures**: Aufruf fachlicher Services aus PL/SQL
- **Oracle DB Features**: Sequences, Triggers, Views, Materialized Views

### Security & Authentication
- **OAuth2/OpenID Connect**: Authorization Code Flow, Token Management
- **JWT**: Token Generation, Validation, Claims
- **RBAC (Role-Based Access Control)**: Berechtigungskonzepte implementieren
- **API Security**: Rate Limiting, CORS, Input Validation
- **Secrets Management**: Azure Key Vault, Environment Variables

### Cloud & DevOps
- **Azure Services**: App Service, Container Apps, AKS
- **Docker**: Container Images erstellen, Multi-stage Builds
- **CI/CD**: Azure DevOps Pipelines, Deployment Automation
- **Monitoring**: Application Insights, Logging, Metrics
- **Configuration**: Environment-specific Config, Feature Flags

## Spezifische Herausforderungen im Projekt

### Integration Layer Design

#### Spring Boot vs. Oracle ORDS
- **Spring Boot**: 
  - Mehr Flexibilität und Kontrolle
  - Java-Ecosystem nutzen (Testing, Libraries)
  - Complex Business Logic in Java möglich
  - Steile Lernkurve für Oracle-Entwickler
  
- **Oracle ORDS**:
  - Oracle-native, direkte PL/SQL-Anbindung
  - Weniger Code, schnellere Entwicklung
  - Vendor Lock-in
  - Begrenzte Flexibilität bei komplexen Anforderungen

#### Service-Stored Procedure Aufrufe
- **Calling Conventions**: Wie werden die Service-SPs aufgerufen?
- **Parameter Mapping**: Java Types ↔ Oracle Types
- **Error Handling**: PL/SQL Exceptions in HTTP Responses übersetzen
- **Transaction Management**: Wann commit/rollback?
- **Performance**: Connection Pooling, Prepared Statements

### AI-Integration

#### AI Gateway
- **LLM-Anbindung**: Azure OpenAI Service, Claude API
- **MCP (Model Context Protocol)**: Integration von AI-Tools
- **Prompt Management**: Templates, Versionierung, A/B Testing
- **Context Building**: Welche Daten braucht das LLM?
- **Response Processing**: LLM-Antworten strukturiert zurückgeben

#### AI Security & RBAC
- **Authentifizierung**: Wie authentifiziert sich ein AI-Agent?
- **Autorisierung**: Welche Daten darf ein AI-Agent sehen/ändern?
- **Audit Logging**: AI-Aktionen nachvollziehbar machen
- **Rate Limiting**: Missbrauch durch AI-Clients verhindern

### API Design & Versionierung

#### RESTful API Design
- **Resource Modeling**: URLs, HTTP Methods, Status Codes
- **Pagination**: Große Datenmengen effizient zurückgeben
- **Filtering & Sorting**: Query Parameters Design
- **HATEOAS**: Hypermedia Links (optional)
- **Idempotenz**: PUT/DELETE idempotent gestalten

#### API Versioning
- **URL-based**: `/api/v1/vertrag`, `/api/v2/vertrag`
- **Header-based**: `Accept: application/vnd.wgv.v2+json`
- **Breaking Changes**: Was rechtfertigt eine neue Version?
- **Deprecation Strategy**: Alte Versionen schrittweise abschalten
- **Backward Compatibility**: Wie lange werden alte Versionen unterstützt?

### Performance & Skalierung

#### Datenbankperformance
- **Connection Pooling**: HikariCP optimal konfigurieren
- **Query Optimization**: Stored Procedure Performance
- **Caching**: Redis, Caffeine für häufige Queries
- **Batch Processing**: Multiple Records effizient verarbeiten

#### Skalierung
- **Horizontal Scaling**: Stateless APIs für Load Balancing
- **Async Processing**: Long-running Operations asynchron
- **Circuit Breaker**: Resilience bei DB-Ausfällen
- **Health Checks**: Liveness, Readiness Probes für Kubernetes

## Domain-spezifisches Wissen

- **Versicherungsdomäne**: Verständnis für Verträge, Partner, Schaden, Tarife
- **ICIS Service-SPs**: Kenntnis der vorhandenen Service-Stored Procedures
- **Oracle DB Schema**: Datenmodell, Constraints, Indexes
- **Fachliche Validierung**: Welche Regeln müssen im Backend geprüft werden?

## Tools & Methoden

### Development
- **IDEs**: IntelliJ IDEA, Eclipse, VS Code
- **Build Tools**: Maven, Gradle
- **Database Tools**: DBeaver, SQL Developer, DataGrip
- **API Testing**: Postman, Insomnia, Bruno, curl
- **Local Development**: Docker Compose für lokale Oracle DB

### Testing
- **Unit Testing**: JUnit 5, Mockito, AssertJ
- **Integration Testing**: Testcontainers, embedded databases
- **API Testing**: REST Assured, Spring MockMvc
- **Performance Testing**: JMeter, Gatling
- **Code Coverage**: JaCoCo

### Monitoring & Debugging
- **Logging**: SLF4J, Logback, structured logging
- **Profiling**: JProfiler, VisualVM, Async Profiler
- **Monitoring**: Application Insights, Prometheus, Grafana
- **Debugging**: Remote Debugging, Thread Dumps, Heap Dumps

### DevOps
- **Docker**: Multi-stage builds, layer optimization
- **Infrastructure as Code**: OpenTofu, Terragrunt (cloud-agnostic IaC)
- **Azure CLI**: Deployment-Skripte, Resource Management (Azure-spezifisch)
- **Git**: Feature branches, conventional commits
- **CI/CD**: Azure DevOps YAML Pipelines

## Zusammenarbeit mit anderen Rollen

- **System Architect**: Architektur-Vorgaben umsetzen, technisches Feedback
- **Staff Frontend Developer**: API-Contract abstimmen, Error Handling klären
- **Oracle Forms Specialist**: Service-SPs verstehen, Geschäftslogik validieren
- **Solution Architect**: Integration Layer Architektur-Entscheidungen
- **DBA/Oracle Specialist**: Performance-Optimierung, DB-Schema-Änderungen

## Best Practices

### API-Entwicklung
- **Contract-First**: OpenAPI Spec zuerst, dann Implementation
- **Validation**: Input immer validieren (Bean Validation)
- **Error Responses**: Einheitliches Error-Format (RFC 7807 Problem Details)
- **Documentation**: OpenAPI/Swagger UI für API-Docs
- **Versioning**: Von Anfang an versionieren

### Security
- **Principle of Least Privilege**: Minimale Berechtigungen
- **Input Validation**: Nie Client-Daten vertrauen
- **SQL Injection**: Prepared Statements, kein String Concat
- **Secrets**: Nie in Code/Git, immer aus Key Vault
- **HTTPS Only**: TLS für alle Verbindungen

### Performance
- **Lazy Loading**: Nur notwendige Daten laden
- **Connection Pooling**: Pool-Size optimal einstellen
- **Caching**: Strategisch cachen (Cache Invalidation beachten)
- **Async where appropriate**: Long-running Ops nicht blockierend

### Code Quality
- **Clean Code**: Lesbarer, wartbarer Code
- **SOLID Principles**: Gutes OO-Design
- **Testing**: Hohe Test Coverage für Business Logic
- **Code Reviews**: Konstruktives Feedback
- **Documentation**: Javadoc für Public APIs

## Erfolgskriterien

- REST APIs sind implementiert und dokumentiert (OpenAPI)
- Service-Stored Procedures werden erfolgreich aufgerufen
- API Versioning ist etabliert
- Security (RBAC) ist implementiert und getestet
- AI Gateway funktioniert und ist sicher
- Performance-Anforderungen sind erfüllt (Response Times, Throughput)
- Integration Tests vorhanden (mind. kritische Endpunkte)
- Deployment nach Azure funktioniert (CI/CD Pipeline)
- Monitoring und Logging sind eingerichtet
- Dokumentation für andere Entwickler vorhanden
