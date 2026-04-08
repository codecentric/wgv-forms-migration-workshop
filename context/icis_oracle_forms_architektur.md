# ICIS Oracle Forms Architektur - Interpretation

**Quelle-Diagramm**: `diagrams/icis_oracle_forms_architektur.svg`  
**Autor**: Fatih Acikgöz  
**Datum**: 05.05.2022  
**Typ**: Detail-Schaubild (Detaillierte Architekturdarstellung)

## Übersicht

Das Diagramm zeigt die **aktuelle Oracle Forms Architektur** des ICIS-Systems. Diese Architektur repräsentiert den Legacy-Zustand, der im Rahmen der WGV-Modernisierung teilweise abgelöst werden soll.

## Architektur-Komponenten

### 1. Client Layer
- **Forms Java Client**: Oracle Forms Client-Anwendung, die in Java läuft

### 2. Application Server Layer
Die mittlere Schicht besteht aus mehreren Komponenten:
- **[ weblogic-server ]**: WebLogic Server als Application Server
- **[ forms-runtime ]**: Oracle Forms Runtime-Umgebung
- **[ icis-forms ]**: ICIS-spezifische Forms-Anwendung
- **[ Oracle-FSAL ]**: Oracle Forms Server Application Layer

### 3. Oracle Forms Architektur (Java VM)
Die klassische Oracle Forms 3-Schichten-Architektur:
- **UI Presentation**: Darstellungsschicht für Benutzeroberflächen
- **Application Logic**: Ausführung der Geschäftslogik
- **Data Manager**: Datenzugriff und -verwaltung

### 4. Database Layer
- **PL/SQL Engine**: Datenbank-seitige PL/SQL-Ausführung
- **Datenbank ICIS**: Die zentrale ICIS-Datenbank

### 5. Datenbank-Komponenten
Die Datenbank enthält:
- **Datenbank-Tabellen**: Persistente Datenspeicherung
- **Packages**: PL/SQL-Packages mit Geschäftslogik
- **Views**: Datenbank-Views
- **FMX-Dateien**: Kompilierte Forms-Module

### 6. Service Procedures
Das Diagramm zeigt verschiedene Service-Procedure-Abkürzungen:
- **BSP, BSV**: Wahrscheinlich Business Service Procedures/Views
- **DSP, DSV**: Wahrscheinlich Data Service Procedures/Views
- **GSP**: Wahrscheinlich General Service Procedures
- **TSP**: Wahrscheinlich Transaction Service Procedures

## Kommunikation

- **Http Request**: Kommunikationsprotokoll zwischen Client und Application Server
- **SQL Net**: Oracle Datenbank-Netzwerkprotokoll zwischen Application Server und Datenbank

## Relevanz für die Modernisierung

Diese Architektur zeigt den **aktuellen Zustand (Legacy)**, der modernisiert werden soll:

### Was bleibt unverändert:
- ✅ **PL/SQL Engine**: Die Geschäftslogik in PL/SQL bleibt erhalten
- ✅ **Datenbank ICIS**: Oracle DB und Datenmodell bleiben unverändert
- ✅ **Packages/Service-SPs**: Die Service-Stored Procedures werden weiterhin genutzt

### Was wird ersetzt:
- ❌ **Forms Java Client**: Wird durch moderne Web-Frontends (React/Angular) ersetzt
- ❌ **UI Presentation & Application Logic**: Werden durch neue Frontend- und Integration-Layer ersetzt
- ❌ **Forms Runtime & ICIS-Forms**: Oracle Forms wird schrittweise abgelöst

### Neue Komponenten (geplant):
- **Integration Layer**: REST API-Schicht (Spring Boot oder Oracle ORDS) zwischen Frontend und PL/SQL
- **Modern Frontend**: React/Angular-basierte Webanwendungen
- **AI Integration**: AI Gateway für Conversational UI und AI-Agents

## Architektur-Muster

Das Diagramm zeigt eine klassische **3-Tier Oracle Forms Architektur**:
1. **Client Tier**: Forms Java Client
2. **Application Tier**: WebLogic + Forms Runtime + Application Logic
3. **Database Tier**: Oracle DB + PL/SQL Engine

Diese Architektur ist typisch für Oracle Forms Anwendungen aus den 2000er Jahren und repräsentiert eine bewährte, aber veraltete Technologie, die nun modernisiert werden soll.
