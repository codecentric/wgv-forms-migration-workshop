# ICIS+ JEE-Architektur - Interpretation

**Quelle-Diagramm**: `diagrams/icis_plus_jee_architekture.svg`  
**Diagramm-Datum**: 30.02.2021 (Stand der Architektur zu diesem Zeitpunkt)  
**Interpretation erstellt**: 2026-04-16  
**Kontext**: WGV ICIS Modernisierung - Verständnis der ICIS+ Architektur

---

## ⚠️ Wichtiger Hinweis zur Aktualität

**Dieses Diagramm stammt vom Februar 2021** und zeigt den damaligen Stand der ICIS+ Architektur. Das Gesamt-Architektur-Diagramm (`architektur_schaubild_icis_gesamt.svg`) ist vom **Mai 2022** und damit **14 Monate jünger**. 

**Implikationen für den Workshop (April 2026)**:
- Dieses Diagramm ist **5 Jahre alt** und zeigt möglicherweise nicht die aktuelle ICIS+-Architektur
- Architektur-Entscheidungen können sich in der Zwischenzeit geändert haben
- **Validierung mit WGV erforderlich**: Welche Komponenten sind noch aktuell? Was hat sich geändert?
- Nutzen Sie dieses Diagramm als **historische Referenz** und **Ausgangspunkt für Diskussionen**, nicht als absolute Wahrheit

**Workshop-Empfehlung**: 
- Am Tag 1 ("Domäne erkennen & ICIS-System Verständnis") explizit nach Änderungen seit 2021 fragen
- Am Tag 1 (ICIS Deep Dive) fragen: "Ist diese Architektur noch aktuell oder gab es Weiterentwicklungen?"

---

## Überblick

Dieses Diagramm zeigt die **ICIS+ JEE-Architektur** (Stand Februar 2021), die moderne Java Enterprise Edition basierte Weiterentwicklung des Legacy ICIS-Systems (Oracle Forms). ICIS+ repräsentiert einen hybriden Ansatz: Es nutzt moderne Web-Technologien (Vaadin, Spring) für die Präsentationsschicht, greift aber weiterhin auf die bestehende Oracle-Datenbank und PL/SQL-Services zu.

Die Architektur folgt dem klassischen **3-Tier-Pattern** mit einer klaren Trennung zwischen Präsentation, Geschäftslogik und Datenhaltung.

---

## Architektur-Ebenen im Detail

### 1. Client-Ebene (Presentation Tier)

**Browser-basierte Anwendung**:
- **Technologie**: Vaadin Framework
- **Deployment**: Als WAR-File auf WebLogic Application Server
- **Zielgruppe**: Desktop-Nutzer (Sachbearbeiter, Power Users)
- **Charakteristik**: Rich Internet Application (RIA) mit server-seitigem Rendering

**Mobile Anwendung**:
- **Technologie**: JavaScript mit Sencha Framework
- **Deployment**: Separates mobile-app Deployment
- **Zielgruppe**: Mobile Nutzer (Außendienst, Field Service)
- **Charakteristik**: Client-seitige JavaScript-Anwendung

**Detail-Scheduler (Batch-Komponente)**:
- **Technologie**: Cronjob
- **Zweck**: Automatisierte, geplante Aufgaben (z.B. nächtliche Batch-Prozesse)
- **Integration**: Greift auf dieselben Services wie die Webanwendung zu

---

### 2. Application Server Tier (WebLogic-Server)

Diese Ebene ist das Herzstück von ICIS+ und enthält mehrere Sub-Layer:

#### 2.1 Presentation Layer

**Vaadin-UI (Browser)**:
- Server-seitige UI-Komponenten
- Automatisches Client-Server-Kommunikationsprotokoll
- Event-basiertes Programmiermodell

**Sencha-basierte Mobile UI**:
- Client-seitige JavaScript-Komponenten
- REST-API-Integration (Kommunikation mit Backend über REST)
- Touch-optimierte UI-Elemente

#### 2.2 Service Layer

**Spring Framework** (durchgängig):
- Dependency Injection Container
- Transaction Management
- Security (Spring Security)
- RESTful Web Services für Mobile-App

**csipjax-services**:
- Business Service-Schicht
- Orchestrierung von Geschäftsprozessen
- Koordination zwischen verschiedenen Backend-Adaptern

#### 2.3 Backend Adapter Layer

Diese Schicht abstrahiert verschiedene Backend-Systeme und Datenquellen:

**1. icis-anbindung (ICIS Legacy Integration)**:
- **Technologie**: Oracle JPublisher
- **Zweck**: Integration mit Legacy ICIS PL/SQL-Services
- **Pattern**: Wrapper für PL/SQL Stored Procedures
- **Funktion**: Übersetzt Java-Aufrufe in Oracle-Datenbankaufrufe (Stored Procedures, Packages)

**2. odsp-anbindung (ODSP Integration)**:
- **Technologie**: Spring
- **Zweck**: Integration mit ODSP-System (Oracle Data Service Provider oder ähnlich)
- **Pattern**: Service-Adapter
- **Funktion**: Anbindung an spezialisierte Oracle-Services

**3. fe-generierungs-anbindung (Frontend-Generierung)**:
- **Technologie**: WebV1
- **Zweck**: Dynamische UI-Generierung (möglicherweise Formular-Generator)
- **Pattern**: Template-basierte Generierung
- **Funktion**: Automatisches Erzeugen von UI-Komponenten aus Metadaten oder Geschäftslogik

**4. csipjax-persistent (Persistenz-Layer)**:
- **Technologie**: JPA 2.0 (Java Persistence API)
- **Zweck**: Objekt-relationale Abbildung (ORM)
- **Pattern**: Repository Pattern
- **Funktion**: CRUD-Operationen auf ICIS+ Datenbank

---

### 3. Data Tier (Datenbank-Ebene)

ICIS+ nutzt eine **Dual-Datenbank-Architektur**:

#### Datenbank ICIS (Legacy)

**WDP Wrapper-Schicht (ICIS)**:
- **Zweck**: Service-Fassade für PL/SQL-Logik
- **Komponenten**:
  - **JOBs**: Batch-Job-Definitionen
  - **SRV**: Service Stored Procedures (Business Logic)
  - **PKG**: PL/SQL Packages (gebündelte Funktionen und Prozeduren)

**Datenbank-Tabellen (Legacy)**:
- Ursprüngliche ICIS-Datenstrukturen
- Historisch gewachsenes Schema
- Weiterhin in Nutzung für Legacy-Funktionen

#### Datenbank ICIS+ (Modern)

**Datenbank-Tabellen**:
- **CSIPJAX**: Neue Geschäftsobjekte (z.B. erweiterte Vertragsverwaltung)
- **CRM**: Customer Relationship Management Daten
- Modernes, normalisiertes Schema
- JPA-optimierte Struktur

---

## Deployment-Struktur

### WAR Deployment (Browser-Anwendung)
```
[war]
├── Vaadin UI Components
├── Spring Configuration
├── csipjax-services
└── Backend Adapters (icis-anbindung, odsp-anbindung, etc.)
```

### Mobile App Deployment
```
[mobile-app]
├── JavaScript/Sencha Frontend
└── REST API Endpoints (Spring)
```

---

## Technologie-Stack Zusammenfassung

| Layer | Technologie | Zweck |
|-------|-------------|-------|
| **Web UI** | Vaadin | Rich Web Application Framework (Java-basiert) |
| **Mobile UI** | JavaScript + Sencha | Mobile-optimierte Touch-UI |
| **Application Framework** | Spring Framework | Dependency Injection, Transaction Management, Security |
| **Persistenz (Modern)** | JPA 2.0 | ORM für ICIS+ Datenbank |
| **Legacy Integration** | Oracle JPublisher | PL/SQL-Wrapper-Generierung |
| **Application Server** | WebLogic | JEE Container |
| **Datenbank** | Oracle Database | ICIS (Legacy) + ICIS+ (Modern) |

---

## Architektur-Patterns

### 1. **Adapter Pattern** (Backend Adapters)
Verschiedene Backend-Systeme (ICIS Legacy, ODSP, Persistenz) werden über einheitliche Adapter-Interfaces angesprochen. Dies ermöglicht:
- Austauschbarkeit von Backend-Implementierungen
- Klare Separation of Concerns
- Testbarkeit (Mock-Adapter)

### 2. **Dual-Schreiben (Dual-Write) / Hybrid Data Architecture**
ICIS+ schreibt parallel in zwei Datenbanken:
- **ICIS Legacy DB**: Für Kompatibilität mit bestehenden Systemen
- **ICIS+ DB**: Für neue Features und optimierte Datenstrukturen

**Risiko**: Konsistenz-Probleme bei Dual-Write (potenzielle Race Conditions)

### 3. **Strangler Fig Pattern** (implizit)
ICIS+ ersetzt schrittweise ICIS-Klassik:
- Neue Features in ICIS+
- Legacy-Features weiterhin über ICIS-Anbindung verfügbar
- Schrittweise Migration von Masken

---

## Kritische Integrationspunkte

### Integration mit ICIS Legacy (icis-anbindung)

**Kommunikationsfluss**:
```
Vaadin UI 
  → Spring Service (csipjax-services) 
    → icis-anbindung (JPublisher Wrapper)
      → WDP Wrapper-Schicht 
        → PL/SQL Service Stored Procedures (SRV)
          → ICIS Datenbank-Tabellen
```

**Technische Details**:
- **JPublisher**: Oracle-Tool zur Generierung von Java-Klassen aus PL/SQL-Signaturen
- **WDP-Wrapper**: Zusätzliche Abstraktionsschicht (möglicherweise für vereinfachte Service-Signaturen)
- **Aufrufe**: Synchron (blocking) - Performance-Implikation bei langsamen PL/SQL-Calls

### Integration mit ICIS+ Persistenz (csipjax-persistent)

**Kommunikationsfluss**:
```
Vaadin UI 
  → Spring Service 
    → csipjax-persistent (JPA Repository)
      → ICIS+ Datenbank-Tabellen (CSIPJAX, CRM)
```

**Technische Details**:
- **JPA 2.0**: Standard Java-Persistenz-API
- **ORM**: Automatisches Mapping zwischen Java-Objekten und DB-Tabellen
- **Transaktionsmanagement**: Über Spring deklarativ gesteuert

---

## Modernisierungs-Implikationen

### Wiederverwendbarkeit für neue Modernisierung

**✅ Was kann wiederverwendet werden?**

1. **Spring-basierte Service-Schicht**:
   - Geschäftslogik in `csipjax-services` ist Framework-agnostic
   - Kann über REST-APIs exponiert werden
   - Transaktionslogik bleibt erhalten

2. **Backend-Adapter-Pattern**:
   - `icis-anbindung` zeigt bewährte Integration mit PL/SQL
   - Kann als Vorlage für neue REST-basierte Integration Layer dienen

3. **JPA-Persistenz-Layer**:
   - Datenbank-Zugriff über JPA ist portierbar
   - Kann in neue Microservices übernommen werden

4. **Mobile App REST-APIs**:
   - Bereits existierende REST-Schnittstellen
   - Können für neue Frontend-Frameworks (React/Angular) genutzt werden

**❌ Was sollte NICHT wiederverwendet werden?**

1. **Vaadin UI-Komponenten**:
   - Tightly coupled mit Server-seitigem State
   - Nicht kompatibel mit modernen SPA-Frameworks (React, Angular, Vue)
   - Migration erfordert UI-Neuentwicklung

2. **WebLogic Application Server**:
   - Heavy-weight, proprietär
   - Modernisierung sollte auf Kubernetes/Cloud-native setzen
   - Ersatz durch Spring Boot + Embedded Tomcat/Netty empfehlenswert

3. **Dual-Datenbank-Architektur**:
   - Konsistenz-Risiken
   - Modernisierung sollte Single Source of Truth anstreben
   - Entweder ICIS Legacy über API-Gateway oder vollständige Datenmigration

### Empfohlene Migrations-Strategie

**Phase 1: API-Schicht extrahieren**
- Spring Services als REST-APIs exponieren
- Frontend (React/Angular) konsumiert diese APIs
- Backend (ICIS+ Services + icis-anbindung) bleibt zunächst unverändert

**Phase 2: Frontend-Migration**
- Vaadin-Masken schrittweise durch React/Angular ersetzen
- Wiederverwendung der REST-APIs aus Phase 1
- Hybrid-Betrieb: ICIS+ Vaadin + neue React-Masken parallel

**Phase 3: Backend-Konsolidierung**
- Dual-Database-Architektur auflösen
- PL/SQL-Services schrittweise in Java-Services migrieren (falls Business Value)
- Event-Driven Architecture einführen (asynchrone Kommunikation)

---

## Vergleich: ICIS-Klassik vs. ICIS+

| Aspekt | ICIS-Klassik | ICIS+ |
|--------|--------------|-------|
| **UI-Technologie** | Oracle Forms (Client-Server) | Vaadin (Web) + Sencha (Mobile) |
| **Application Tier** | Oracle Forms Runtime + PL/SQL | Spring Framework + JEE |
| **Persistenz** | Direkt in PL/SQL (Stored Procedures) | JPA 2.0 + PL/SQL-Wrapper |
| **Datenbank** | Oracle DB (Monolith) | Oracle DB (Dual: Legacy + Modern) |
| **Deployment** | Fat Client Installation | Web Application (Browser) |
| **Integration** | Direct Database Calls | Service-orientierte Architektur (SOA) |
| **Skalierbarkeit** | Vertikal (DB-Server) | Horizontal (Application Server Cluster) |

---

## Architektur-Risiken und Pain Points

### 1. **Dual-Database-Synchronisation**
- **Problem**: Daten in ICIS und ICIS+ können divergieren
- **Mitigation**: Transaktionale Konsistenz über 2-Phase-Commit oder Event Sourcing

### 2. **Synchrone PL/SQL-Aufrufe**
- **Problem**: Blocking Calls zu PL/SQL reduzieren Skalierbarkeit
- **Mitigation**: Asynchrone Verarbeitung, Message Queues (z.B. Oracle AQ, Kafka)

### 3. **Vaadin Server-Side State**
- **Problem**: Session-State auf Application Server → Horizontal Scaling schwierig
- **Mitigation**: Sticky Sessions oder Session Replication (WebLogic-Feature)

### 4. **WebLogic Vendor Lock-in**
- **Problem**: Proprietäre Features, hohe Lizenzkosten, Cloud-Migration erschwert
- **Mitigation**: Standardisierung auf Spring Boot, Containerisierung (Docker/Kubernetes)

### 5. **Monolithische Architektur**
- **Problem**: Alle Komponenten in einem WAR-Deployment → schwer wartbar
- **Mitigation**: Microservices-Extraktion (z.B. Customer Service, Policy Service)

---

## Erfolgskriterien für Modernisierung basierend auf ICIS+

Aus der ICIS+-Architektur lassen sich folgende Erfolgskriterien ableiten:

✅ **Behalten (Keep)**:
- Spring Framework als Backend-Basis (bewährt, stabil, Cloud-ready)
- Service-Layer-Pattern (csipjax-services)
- Adapter-Pattern für Backend-Integration
- JPA für neue Datenbank-Zugriffe

✅ **Weiterentwickeln (Evolve)**:
- REST-APIs für Frontend-Entkopplung (bereits vorhanden für Mobile, erweitern)
- Cloud-native Deployment (WebLogic → Kubernetes)
- Asynchrone Kommunikation (Message Queues einführen)
- Event-Driven Architecture für Konsistenz

❌ **Ersetzen (Replace)**:
- Vaadin → React/Angular/Vue
- Dual-Database → Single Source of Truth mit Event Sourcing
- Synchrone PL/SQL-Calls → Service-basierte Abstraktion

---

## Zeitliche Einordnung der Architektur-Diagramme

**Chronologische Reihenfolge**:
1. **Februar 2021**: ICIS+ JEE-Architektur-Diagramm (dieses Dokument) - Detailansicht der ICIS+ Komponente
2. **Mai 2022**: Gesamt-Architektur-Diagramm (`architektur_schaubild_icis_gesamt.md`) - Gesamtsystem inkl. ICIS+

**Mögliche Änderungen zwischen 2021 und 2022** (Hypothesen, zu validieren):
- Weitere ICIS+-Komponenten entwickelt
- Zusätzliche externe Integrationen (siehe Gesamt-Diagramm: SAP, COR Life, etc.)
- Deployment-Änderungen (WebLogic-Version, Container-Strategien)
- Neue Backend-Adapter oder Services

**Weitere Weiterentwicklungen seit 2022** (zu erfragen am Workshop):
- Welche Masken wurden von Forms zu ICIS+ migriert?
- Welche neuen ICIS+-Features wurden entwickelt?
- Gibt es neue Technologien (z.B. Ersetzen von Vaadin durch React/Angular bereits begonnen)?
- Wurde die Dual-Database-Architektur weiterentwickelt oder konsolidiert?

---

## Verbindung zu anderen Dokumenten

**Verwandte Architektur-Dokumentationen** (chronologisch):
- `context/icis_oracle_forms_architektur.md`: ICIS-Klassik 3-Tier-Architektur (Legacy)
- `context/icis_plus_jee_architekture.md`: ICIS+ JEE-Architektur (Feb 2021, dieses Dokument)
- `context/architektur_schaubild_icis_gesamt.md`: Gesamtsystem mit ICIS, ICIS+, APEX und externen Systemen (Mai 2022, **aktueller**)

**Facilitation Guides**:
- `facilitation/tag1_icis_deep_dive_guide.md`: Strukturierte Fragen zu ICIS+ (Part B) - **Validierung der Architektur seit 2021 erforderlich!**
- `facilitation/tag1_domain_mapping_guide.md`: Domain-Grenzen zwischen ICIS und ICIS+

**Workshop-Relevanz**:
- **Tag 1**: ICIS+-Architektur-Verständnis im Kontext "Domäne erkennen & ICIS-System Verständnis"
  - **Kritische Frage**: "Welche Änderungen gab es seit 2021 an der ICIS+-Architektur?"
- **Tag 2**: Wiederverwendbarkeit von ICIS+-Komponenten für Integrationsschicht-Diskussion
  - **Kritische Frage**: "Sind die Backend-Adapter (icis-anbindung, etc.) noch aktuell?"
- **Tag 2**: Deployment-Ansätze (WebLogic → Kubernetes Migration)
  - **Kritische Frage**: "Läuft ICIS+ 2026 noch auf WebLogic oder gab es bereits Modernisierung?"

---

**Erstellt**: 2026-04-16  
**Autor**: Sócrates Ponce (codecentric)  
**Zweck**: Architektur-Verständnis für WGV ICIS Modernisierungs-Workshop  
**Version**: 1.0
