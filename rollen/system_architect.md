# System Architect (Frontend & Backend Expertise)

## Rolle & Verantwortlichkeiten

Der System Architect übersetzt die High-Level Solution Architecture in konkrete technische Implementierungsdetails für Frontend und Backend. Er stellt sicher, dass die gewählten Technologien, Frameworks und Patterns praktisch umsetzbar sind und Best Practices folgen.

## Kernkompetenzen

### Frontend-Expertise
- **Modern JavaScript/TypeScript**: ES6+, async/await, modules
- **Frontend Frameworks**: React, Angular, Vue - tiefes Verständnis der Unterschiede
- **State Management**: Redux, Zustand, NgRx, Context API
- **Build Tools**: Webpack, Vite, esbuild
- **Testing**: Vitest, Jest, React Testing Library, Cypress, Playwright
- **Performance Optimization**: Code Splitting, Lazy Loading, Bundle Size

### Backend-Expertise
- **Java Ecosystem**: Spring Boot, Spring Data, Spring Security
- **REST API Implementation**: Best Practices, Fehlerbehandlung, Validierung
- **Oracle Integration**: JDBC, Oracle REST Data Services (ORDS), PL/SQL Calls
- **Database**: SQL, Connection Pooling, Transaction Management
- **Security**: OAuth2, JWT, RBAC Implementation
- **Caching & Performance**: Redis, In-Memory Caching

### Cross-Cutting Concerns
- **Containerization**: Docker, Docker Compose
- **CI/CD**: Azure DevOps, GitHub Actions, Jenkins
- **Monitoring & Logging**: Application Insights, ELK Stack, Structured Logging, OpenTelemetry
- **API Documentation**: OpenAPI/Swagger, API Versioning

## Spezifische Herausforderungen im Projekt

### Frontend-Spezifisch

#### Framework-Wahl
- **LLM-Unterstützung**: Wie gut können AI-Tools Code für React vs. Angular generieren?
- **Vaadin-Integration**: Können bestehende ICIS+ Vaadin-Komponenten wiederverwendet werden?
- **Langlebigkeit**: Was ist in 5-10 Jahren noch relevant?
- **Team-Skills**: Was können aktuelle/zukünftige Entwickler?

#### UI-Komplexität
- **900 Oracle Forms Masken**: Viele sind hochkomplex mit Dutzenden Feldern
- **Validierung**: Client-side und Server-side Validation
- **Accessibility**: WCAG 2.1 AA Compliance
- **Responsive Design**: Desktop-first (Power User) aber auch mobil-fähig

#### AI-UI Integration
- **Conversational UI**: Wie integriert man Chat-Elemente in Forms?
- **Human-in-the-Loop**: UI für Review von AI-Vorschlägen
- **Real-time Updates**: WebSockets vs. Polling für AI-Responses

### Backend-Spezifisch

#### Integration Layer Design
- **Spring Boot vs. Oracle ORDS**: Technische Vor-/Nachteile
  - Spring Boot: Mehr Flexibilität, Java-Ecosystem
  - Oracle ORDS: Oracle-nativ, weniger Code, aber vendor lock-in
- **Service-Stored Procedures aufrufen**: Best Practices für PL/SQL Calls
- **Error Handling**: PL/SQL Exceptions in REST-Responses übersetzen
- **Transaction Management**: Distributed Transactions?

#### AI-Backend Integration
- **AI Gateway**: Wie routet man Requests an LLMs?
- **MCP (Model Context Protocol)**: Technische Integration
- **Prompt Management**: Wo speichert man Prompts? Wie versioniert man sie?
- **Rate Limiting & Throttling**: Azure OpenAI API Limits managen

#### Deployment & Operations
- **Kubernetes**: Ist die Komplexität gerechtfertigt?
- **Azure Services**: App Service vs. AKS vs. Container Apps
- **Database Connection Pooling**: Performante Oracle-Verbindungen
- **Secrets Management**: Azure Key Vault Integration

## Domain-spezifisches Wissen

- **Oracle Forms Architektur**: Block, Trigger, PL/SQL, Forms Services
- **ICIS+ Vaadin Stack**: Wie ist ICIS+ gebaut? Was kann wiederverwendet werden?
- **Service-Stored Procedures**: Signature, Parameter, Calling Conventions
- **Versicherungsfachlichkeit**: Grundverständnis ausreichend, Details kommen vom Fachbereich

## Technische Entscheidungen (Beispiele)

### Frontend
```typescript
// React mit TypeScript - Beispiel Component
interface MaskProps {
  vertragId: string;
}

const VertragsDetailMaske: React.FC<MaskProps> = ({ vertragId }) => {
  const [vertrag, setVertrag] = useState<Vertrag | null>(null);
  
  useEffect(() => {
    // API Call to Integration Layer
    fetch(`/api/v1/vertrag/${vertragId}`)
      .then(res => res.json())
      .then(setVertrag);
  }, [vertragId]);
  
  return (
    <div className="maske">
      {/* Form Fields */}
    </div>
  );
};
```

### Backend Integration Layer
```java
// Spring Boot - Service-Stored Procedure Call
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

### API Versioning
```
GET /api/v1/vertrag/{id}  - Version 1
GET /api/v2/vertrag/{id}  - Version 2 (breaking changes)
```

## Tools & Methoden

### Frontend
- **IDEs**: VS Code mit Extensions, WebStorm
- **Package Managers**: npm, yarn, pnpm
- **Linting**: ESLint, Prettier
- **Type Checking**: TypeScript
- **Browser DevTools**: Chrome/Firefox DevTools, React DevTools

### Backend
- **IDEs**: IntelliJ IDEA, Eclipse, VS Code
- **Build Tools**: Maven, Gradle
- **API Testing**: Postman, Insomnia, Bruno
- **Database Tools**: DBeaver, SQL Developer
- **Profiling**: JProfiler, VisualVM

### DevOps
- **Docker**: Container Images, Docker Compose
- **Kubernetes**: kubectl, Helm Charts, K9s
- **Infrastructure as Code**: OpenTofu, Terragrunt (cloud-agnostic)
- **Azure CLI**: az commands (für Azure-spezifische Operationen)
- **Git**: Branch strategies, CI/CD integration

## Zusammenarbeit mit anderen Rollen

- **Solution Architect**: High-level Architektur in Code übersetzen
- **Frontend Developer**: Implementierungsdetails klären, Code Reviews
- **UX/UI Expert**: Technische Umsetzbarkeit von UI-Designs validieren
- **Oracle Forms Specialist**: Legacy-System verstehen, Migration planen

## Erfolgskriterien

- Gewählte Technologien sind dokumentiert und durch PoCs validiert
- Frontend-Framework-Entscheidung ist getroffen und begründet
- Integration Layer (Spring Boot vs. ORDS) ist entschieden
- Deployment-Strategie (Azure App Service vs. AKS) ist definiert
- AI-Tooling-Strategie ist festgelegt
- Code-Beispiele/PoCs demonstrieren Machbarkeit
- Entwickler können produktiv starten
