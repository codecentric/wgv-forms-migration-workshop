# Architektur-Schaubild ICIS-Gesamt - Interpretation

**Quelle-Diagramm**: `diagrams/architektur_schaubild_icis_gesamt.svg`  
**Autor**: Fatih Acikgöz  
**Datum**: 05.05.2022  
**Typ**: Gesamt-Architektur (Complete System Architecture)

## Übersicht

Dieses Diagramm zeigt die **vollständige ICIS-Systemlandschaft** mit allen Komponenten, Integrationen und externen Systemen. Im Gegensatz zum Oracle Forms Detail-Diagramm bietet dies eine Gesamtübersicht aller ICIS-Module und ihrer Verbindungen.

## Haupt-Komponenten

### 1. ICIS Core Systeme

#### ICIS+ und API Layer
- **[ icis-icisplus, icisplus-api ]**: Moderne ICIS+ Komponente mit API (Vaadin-basiert)
- **Oracle REST Data Services**: REST API Schicht für Datenzugriff
- **[ icis-eicis ]**: eICIS Komponente (elektronische ICIS-Variante für externe Zugriffe)

#### Legacy Forms
- **[ icis-forms ]**: Oracle Forms Masken (Legacy UI - ca. 900 Masken)

#### Batch Processing & Jobs
- **[ icis-jobs, icis-print ]**: Job-Verarbeitung und Druck-Jobs für Batch-Operationen

#### Navigation & Control
- **[ icis-navicontroller ]**: Icis Navicontroller für Navigation zwischen Modulen

### 2. Middleware & Application Server

#### Web Server & Application Container
- **httpd**: Apache HTTP Server als Frontend-Webserver
- **Tomcat**: Java Application Server für moderne Komponenten
- **Oracle Application Express (APEX)**: Oracle Low-Code Platform
  - **[ apex-aman * ]**: APEX-Anwendung (möglicherweise für einfache CRUD-Masken)

### 3. Externe Integrationen & Partner-Systeme

#### Lebensversicherungs-System
- **[ msg-cor-life ]**: msg COR Life System Integration
- **Cor Life Application**: Lebensversicherungs-Anwendung (externe Fachsoftware)

#### KFZ-Versicherung
- **[ webservice-kfz * ]**: KFZ Web-Service für Kraftfahrtversicherung

#### Dokumenten-Management
- **[ imagemaster-dms ]**: Imagemaster DMS (Document Management System)
- **Imagemaster Middleware**: Middleware für DMS-Integration

#### Telefonie
- **[ sip-server ]**: SIP Server für Telefonie-Integration (Computer-Telefonie-Integration)

#### GDV-Schnittstelle
- **[ MQSerires GDV Schnittstelle ]**: MQ Series für GDV-Kommunikation (Gesamtverband der Deutschen Versicherungswirtschaft - Branchenstandard)

#### Weitere Externe Systeme
- **SAP**: SAP-System Integration (vermutlich für Finanzen/Controlling)
- **DSS, MIS, PRODUKTI**: Weitere externe Systeme (Decision Support, Management Information System, Produktions-System)
- **[ Druckhaus extern ]**: Externes Druckhaus für Massendruck

### 4. Datenbank-Zugriff & Stored Procedures

- **Stored Procedures**: PL/SQL Service-Stored Procedures (zentrale Geschäftslogik)
- **Oracle Database**: Zentrale Oracle-Datenbank (ICIS-Datenmodell)
- **Data Services**: Datenbank-Services für strukturierten Zugriff
- **DB-Link**: Oracle Database Links für verteilte Datenbank-Zugriffe zwischen Schemas

### 5. Output & Druck-Systeme

#### Print Services
- **Cups**: Common Unix Printing System
- **Print**: Druck-Services für Policen, Angebote, etc.
- **Fax**: Fax-Versand
- **PDF / E-Mail**: PDF-Generierung und E-Mail-Versand
- **PCL**: Printer Command Language (Druckersprache)

#### E-Dokumenten-Versand
- **eVB, SNN, VWB, ...**: Elektronische Versicherungsbestätigung und weitere Dokumente
- **FTP**: File Transfer Protocol für Dokument-Upload/Download

### 6. WWW & Öffentliche Schnittstellen

- **WWW**: Web-Zugang für Endkunden und Partner
- **eICIS**: Elektronischer ICIS-Zugang für externe Nutzer/Partner

## Kommunikations-Protokolle & Schnittstellen

- **JDBC**: Java Database Connectivity (Datenbankzugriff aus Java-Anwendungen)
- **JDBC/SQL-Net**: Kombinierte Datenbank-Protokolle
- **REST**: RESTful Web Services (moderne APIs)
- **Web-Service**: SOAP Web Services (Legacy-APIs)
- **TCP**: TCP-basierte Kommunikation
- **FTP**: File Transfer Protocol
- **DB-Link**: Oracle Database Links
- **Java**: Java-basierte Komponenten und Middleware

## Architektur-Muster

Das Diagramm zeigt eine **komplexe, heterogene IT-Landschaft** mit folgenden Charakteristiken:

### 1. Legacy + Modern Hybrid
Oracle Forms (Legacy) koexistiert mit modernen ICIS+ (Vaadin) und APEX-Anwendungen. Dies zeigt die schrittweise Modernisierung, die bereits begonnen hat.

### 2. Service-Oriented Architecture (SOA)
Zentrale Stored Procedures werden von verschiedenen Clients genutzt (Forms, ICIS+, APEX, externe Systeme). Dies ist eine gute Basis für die weitere Modernisierung.

### 3. Multi-Channel
Verschiedene Zugangskanäle: WWW, Forms-Client, eICIS (elektronisch für Partner/Kunden).

### 4. Integration Hub
ICIS agiert als zentraler Integration Hub für diverse externe Systeme:
- SAP (Finanzen)
- COR Life (Lebensversicherung)
- DMS (Dokumentenmanagement)
- GDV (Branchenschnittstelle)
- Telefonie (SIP)

### 5. Batch & Real-time
Sowohl interaktive Anwendungen als auch Batch-Jobs (Print, eVB-Versand, nächtliche Jobs).

## Relevanz für die Modernisierung

### Komplexität der Modernisierung

#### Viele Integrationspunkte
Externe Systeme (SAP, COR Life, DMS, GDV, SIP, etc.) müssen weiterhin nahtlos funktionieren. Die neue Architektur muss diese Integrationen beibehalten oder migrieren.

#### Parallelbetrieb
ICIS Forms, ICIS+, und APEX laufen aktuell parallel. Die Migrationsstrategie muss Koexistenz mehrerer Systeme über längere Zeit berücksichtigen.

#### Output-Kanäle
Print, Fax, E-Mail, PDF, eVB-Versand müssen in neuer Architektur verfügbar bleiben. Diese Services sind geschäftskritisch.

#### Externe Abhängigkeiten
- **GDV-Schnittstelle**: Branchenstandard, muss weiter funktionieren
- **COR Life**: Partnersystem, Integration muss erhalten bleiben
- **Imagemaster DMS**: Dokumentenarchiv, kritisch für Compliance

### Modernisierungs-Potenzial

#### REST APIs bereits vorhanden
Oracle REST Data Services sind bereits implementiert und können als Basis für die neue Integration Layer dienen.

#### APEX für einfache Masken
Oracle APEX wird bereits genutzt und könnte für weitere CRUD-Masken eingesetzt werden (wie in der Modernisierungsstrategie vorgesehen).

#### Stored Procedures als Service-Layer
Zentrale Geschäftslogik ist bereits in wiederverwendbaren Service-Stored Procedures gekapselt. Diese können von neuen Frontends genutzt werden.

#### Bestehende Middleware
Tomcat und httpd sind bereits vorhanden und können für neue Komponenten genutzt werden.

### Was bleibt unverändert

- ✅ **Oracle Database & Stored Procedures**: Datenbank und PL/SQL-Geschäftslogik bleiben
- ✅ **Externe Integrationen**: GDV, SAP, COR Life, DMS, SIP müssen weiterhin funktionieren
- ✅ **Output-Services**: Print, Fax, E-Mail, PDF-Generierung bleiben erhalten
- ✅ **Oracle REST Data Services**: Können erweitert und als Teil der Integration Layer genutzt werden
- ✅ **Batch-Jobs**: [ icis-jobs, icis-print ] bleiben für nächtliche Verarbeitung

### Was wird modernisiert

- ❌ **[ icis-forms ]**: Oracle Forms Masken werden durch neue React/Angular Frontends ersetzt
- ❓ **[ icis-icisplus ]**: Möglicherweise erweitert oder teilweise durch neue Frontends ersetzt
- ➕ **Neue Integration Layer**: Einheitliche REST API für alle Clients (Frontend, AI, externe Partner)
- ➕ **AI Integration**: AI Gateway für Conversational UI und AI-Agents
- ➕ **Moderne Frontends**: React/Angular-basierte Webanwendungen für komplexe Masken

### Architektur-Herausforderungen

#### Integration Layer Design
Eine neue Integration Layer muss:
- Bestehende Stored Procedures aufrufen
- RESTful APIs für moderne Frontends bereitstellen
- Externe Systeme (SAP, COR Life, etc.) integrieren
- AI-Clients unterstützen (MCP, RBAC)
- Versionierung für langlebige APIs

#### Koexistenz-Strategie
Während der Migration müssen parallel laufen:
- Oracle Forms (Legacy)
- ICIS+ (Vaadin, bestehendes modernes System)
- Neue React/Angular Frontends
- Oracle APEX (für einfache CRUD)

#### Daten-Konsistenz
Alle Systeme greifen auf dieselbe Oracle-Datenbank zu. Transaktions-Management und Daten-Konsistenz müssen gewährleistet sein.

## Zusammenfassung

Das Architektur-Schaubild zeigt die **Komplexität der ICIS-Landschaft** mit zahlreichen Komponenten, externen Integrationen und Output-Kanälen. Die Modernisierung ist eine **große Herausforderung**, bietet aber auch Chancen:

- **Schrittweise Migration**: Nicht alles auf einmal, sondern iterativ (MVP mit 3-5 Masken)
- **Bewährte Basis**: Stored Procedures und REST Data Services sind bereits vorhanden
- **Klare Abgrenzung**: Backend (PL/SQL) bleibt, Frontend wird modernisiert
- **AI-Potenzial**: Neue Frontends können Conversational UI und AI-Agents integrieren

Die Herausforderung liegt darin, die bestehende Komplexität zu managen und gleichzeitig moderne, zukunftssichere Lösungen zu schaffen.
