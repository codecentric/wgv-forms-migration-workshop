# Tag 1: ICIS Deep Dive (ICIS-Klassik & ICIS+) - Facilitator Guide

**Workshop**: WGV ICIS Modernisierung  
**Zielgruppe**: Nutzer, Architekten, (optional: PO/Projektleiter, Developer)  
**Dauer**: ~90-120 Minuten  
**Ansatz**: Strukturierte Informationssammlung durch WGV-Präsentation mit Facilitator-Fragenführung

---

## Zielsetzung

Am Ende der ICIS Deep Dive Session haben wir:

✅ **Architektur-Verständnis**: Dokumentation von ICIS-Klassik (Oracle Forms) und ICIS+ (Vaadin) Architekturen  
✅ **Service-Inventar**: Liste der Stored Procedures mit Signaturen und Geschäftsfunktionen  
✅ **Wiederverwendbarkeits-Assessment**: Welche ICIS+ Komponenten/Services können wiederverwendet werden?  
✅ **Pain Points Katalog**: Bekannte Probleme mit aktuellen Systemen  
✅ **Migrations-Constraints**: Was muss unverändert bleiben  
✅ **Vergleichsmatrix**: Klare Sicht auf Unterschiede ICIS-Klassik vs. ICIS+  
✅ **Migrations-Strategie Canvas**: Initiale Sicht auf Keep/Reuse/Build-New  

**Output für weitere Tag 1 Aktivitäten**: Basis für Maskenanalyse, Scope-Diskussion, AI-Features-Identifikation

---

## Kontext & Facilitator-Mindset

### Wichtig: Rollenverteilung

**WGV-Team**:
- ✅ **Experten** für ihre Systeme (ICIS-Klassik, ICIS+)
- ✅ **Präsentatoren** der Architektur, Masken, Services
- ✅ **Wissensträger** für Business-Logik und Prozesse

**codecentric-Team (wir)**:
- ✅ **Facilitators**: Strukturierte Fragen stellen
- ✅ **Dokumentatoren**: Antworten in Templates festhalten
- ✅ **Synthesizer**: Erkenntnisse in Migrations-Implikationen übersetzen

### Was wir NICHT tun

- ❌ WGV erklären, wie ihr System funktioniert
- ❌ Architektur-Entscheidungen kritisieren (es sei denn, sie fragen)
- ❌ Antworten über ICIS/ICIS+ Interna geben, die wir nicht haben

### Kontext aus vorherigen Aktivitäten

**Input aus Domain Mapping**:
- Identifizierte Bounded Contexts (Schaden, Vertrag, Kunde, etc.)
- Context Map mit externen Systemen
- Core Domain Chart (Priorisierung)

**Nutzung für ICIS Deep Dive**:
- Masken nach Bounded Context kategorisieren
- Stored Procedures nach Domäne gruppieren
- Wiederverwendbarkeit im Kontext der Modernisierung bewerten

---

## Aktivitätsstruktur

### Dreiteilige Struktur

| Phase | Dauer | Format | Fokus |
|-------|-------|--------|-------|
| **Part A: ICIS-Klassik Deep Dive** | 40-50min | WGV präsentiert, wir fragen strukturiert | Oracle Forms + Stored Procedures |
| **Part B: ICIS+ Deep Dive** | 30-40min | WGV präsentiert, wir fragen strukturiert | Vaadin + Spring/Hibernate + Wrapper Services |
| **Part C: Vergleichende Analyse** | 20-30min | Gemeinsames Template-Ausfüllen | ICIS vs. ICIS+ Vergleich, Migrations-Implikationen |

**Gesamtdauer**: ~90-120 Minuten

### Empfohlene Platzierung in Tag 1

**Option A** (Vormittag Ende):
- 10:25-12:00 (nach 15min Pause, ~95min verfügbar)
- **Vorteil**: Frische Köpfe, konzentrierte technische Diskussion
- **Nachteil**: Möglicherweise zu technisch für nicht-Entwickler

**Option B** (Nachmittag Start):
- 13:00-14:30 (90min vor erster Pause)
- **Vorteil**: Nach Mittagspause, passt gut in ersten Nachmittags-Block
- **Nachteil**: Post-Lunch-Tief

**Empfehlung**: Option A (Vormittag Ende), wenn Architekten/Developer anwesend

---

## Part A: ICIS-Klassik (Oracle Forms) Deep Dive

**Dauer**: 40-50 Minuten  
**Ziel**: Bestehende Oracle Forms Architektur, Stored Procedure Services und Datenfluss-Patterns verstehen

### Ablauf

**Einführung (5min)**:
- Erklärung des Ziels: "Wir möchten verstehen, wie ICIS-Klassik aufgebaut ist, um die Modernisierung zu planen"
- Erwartung an WGV: "Bitte zeigen Sie uns Ihre Architektur, Masken-Beispiele und Stored Procedures"
- Unsere Rolle: "Wir werden strukturierte Fragen stellen und dokumentieren"

**WGV-Präsentation + Strukturierte Fragen (35-45min)**:

---

### Fragenkategorie 1: Architektur & Technologie-Stack (~10min, 8 Fragen)

**Ziel**: Verstehen der technischen Basis und Deployment-Architektur

#### Frage 1.1: Oracle Forms Version
> "Welche **Oracle Forms Version** setzen Sie ein? (z.B. 10g, 11g, 12c)"

**Notieren**:
- Forms Version: _______
- Oracle Database Version: _______
- Compatibility Matrix beachten (für spätere Referenz)

#### Frage 1.2: Deployment-Modell
> "Wie ist Oracle Forms **deployed**?"
> - Forms Server (Application Server, welcher?)
> - Runtime Environment (welche Java-Version?)
> - Client-Zugriff: Java Web Start? Browser Plugin? Thick Client?

**Notieren**:
- Deployment-Typ: _______
- Application Server: _______
- Client-Technologie: _______

#### Frage 1.3: Netzwerk-Topologie
> "Wie ist die **Netzwerk-Architektur** aufgebaut?"
> - Wo läuft Forms Server? (On-Premise, Datacenter?)
> - Wo liegt die Oracle-Datenbank?
> - Wie greifen Benutzer zu? (VPN, Citrix, direkter Zugriff?)

**Notieren**:
- Forms Server Location: _______
- DB Location: _______
- User Access Method: _______
- **Performance-Hinweise**: Latenz-Probleme? Bandbreite-Limits?

#### Frage 1.4: Authentifizierung & Autorisierung
> "Wie werden **Benutzer authentifiziert**?"
> - LDAP/Active Directory?
> - Oracle Database Benutzer?
> - SSO (Single Sign-On)?
> 
> "Wie wird **Autorisierung** gehandhabt?"
> - Rollen-Modell in Oracle Forms?
> - Datenbank-Rollen?
> - Application-Level Security?

**Notieren**:
- Authentifizierungs-Mechanismus: _______
- Autorisierungs-Modell: _______
- **Wichtig für Migration**: Muss neues Frontend dasselbe Auth-Modell nutzen?

#### Frage 1.5: Session-Management
> "Wie wird **Session-Management** gehandhabt?"
> - Forms Session vs. Database Session?
> - Connection Pooling?
> - Session-Timeout? Idle-Timeout?

**Notieren**:
- Session-Verwaltung: _______
- Connection Pool Konfiguration: _______
- Timeouts: _______

#### Frage 1.6: High Availability & Disaster Recovery
> "Gibt es **High Availability** Setup?"
> - Redundante Forms Server?
> - Failover-Mechanismen?
> - Backup & Recovery Strategie?

**Notieren**:
- HA-Setup: Ja/Nein, Details: _______
- DR-Strategie: _______

#### Frage 1.7: Monitoring & Logging
> "Wie wird ICIS-Klassik **überwacht**?"
> - Monitoring-Tools? (z.B. Oracle Enterprise Manager)
> - Logging-Strategie? (Application Logs, Database Logs)
> - Performance-Metriken? (Response-Times, Throughput)

**Notieren**:
- Monitoring-Lösung: _______
- Logging-Infrastruktur: _______
- **Pain Points**: Was ist schwer zu monitoren?

#### Frage 1.8: Deployment-Prozess
> "Wie werden **Änderungen deployed**?"
> - Manuelle Deployments?
> - Automatisierung vorhanden?
> - Downtime erforderlich?
> - Rollback-Strategie?

**Notieren**:
- Deployment-Prozess: _______
- **Pain Point**: Ist Deployment komplex/fehleranfällig?

**Template**: **Architecture Overview Canvas** (Miro/Whiteboard)
```
┌─────────────────────────────────────────────┐
│  ICIS-Klassik Architektur-Übersicht         │
├─────────────────────────────────────────────┤
│ Forms Version: ___________________________  │
│ Oracle DB Version: _______________________  │
│ Deployment: _______________________________  │
│ Client Access: ____________________________  │
│ Authentication: ___________________________  │
│ Session Management: _______________________  │
│ HA/DR: ____________________________________  │
│ Monitoring: _______________________________  │
└─────────────────────────────────────────────┘
```

---

### Fragenkategorie 2: Forms-Masken Struktur & Patterns (~10min, 10 Fragen)

**Ziel**: Verstehen der UI-Patterns, Komplexität und Nutzungsmuster

#### Frage 2.1: Masken-Kategorisierung
> "Wie viele **verschiedene Masken-Typen** gibt es in ICIS-Klassik?"
> - CRUD-Masken (Create, Read, Update, Delete)?
> - Wizards/Assistenten?
> - Dashboards/Übersichten?
> - Report-Masken?
> - Andere?

**Notieren**:
- CRUD-Masken: ~___ Masken
- Wizards: ~___ Masken
- Dashboards: ~___ Masken
- Reports: ~___ Masken
- Andere: _______

#### Frage 2.2: Häufigste Masken
> "Welche Masken werden **am häufigsten** genutzt?"
> - Können Sie die Top 20% identifizieren? (Pareto-Prinzip)
> - Welche Masken nutzen Power User täglich?

**Notieren**:
- Top 10-20 Masken (Name + Geschäftsfunktion): _______
- **Wichtig**: Diese könnten MVP-Kandidaten sein

#### Frage 2.3: Komplexeste Masken
> "Welche Masken sind **am komplexesten**?"
> - Viele Felder? (>50 Felder?)
> - Viele Geschäftsregeln?
> - Komplexe Validierung?
> - Viele Stored Procedure Aufrufe?

**Notieren**:
- Komplexe Masken (Name + Komplexitäts-Gründe): _______
- **Achtung**: Diese sollten NICHT im MVP sein

#### Frage 2.4: Masken-Organisation
> "Wie sind Masken **organisiert**?"
> - Nach Modul? (z.B. Schaden, Vertrag, Kunde)
> - Nach Geschäftsprozess?
> - Nach Abteilung?
> - Andere Struktur?

**Notieren**:
- Organisationsstruktur: _______
- **Mapping**: Passt das zu Bounded Contexts aus Domain Mapping?

#### Frage 2.5: Navigations-Patterns
> "Wie **navigieren** Benutzer zwischen Masken?"
> - Menü-Navigation?
> - Tastaturkürzel?
> - Direkte Aufrufe (z.B. Vertragsnummer → Vertrag öffnen)?
> - Workflow-gesteuert?

**Notieren**:
- Navigations-Typen: _______
- **Power User Requirement**: Welche Shortcuts sind kritisch?

#### Frage 2.6: Master-Detail Beziehungen
> "Wie werden **Master-Detail Beziehungen** dargestellt?"
> - Beispiel: Vertrag (Master) mit Positionen (Detail)
> - Wie sind Detail-Ansichten aufgebaut?
> - Inline-Editing möglich?

**Notieren**:
- Master-Detail Pattern: _______
- **UI-Implikation**: Muss neues Frontend ähnlich sein?

#### Frage 2.7: Datenvalidierung
> "Wo findet **Datenvalidierung** statt?"
> - Client-seitig (in Forms-Maske)?
> - Server-seitig (in Stored Procedures)?
> - Beides?
> 
> "Wann wird validiert?"
> - Bei jedem Feldwechsel?
> - Beim Speichern?

**Notieren**:
- Validierungs-Strategie: _______
- **Wichtig**: Muss dieselbe Validierung im neuen Frontend sein

#### Frage 2.8: Lookups & Dropdowns
> "Wie werden **Lookups/Dropdowns** befüllt?"
> - Record Groups (Forms-intern)?
> - Stored Procedure Aufrufe?
> - Statische Listen?
> 
> "Wie viele Einträge haben typische Dropdowns?"
> - <10, 10-100, 100-1000, >1000?

**Notieren**:
- Lookup-Mechanismus: _______
- Typische Größen: _______
- **Performance**: Gibt es langsame Lookups?

#### Frage 2.9: Fehlerbehandlung & Messaging
> "Wie wird **Fehlerbehandlung** implementiert?"
> - Oracle Forms Alerts/Messages?
> - Custom Error Dialogs?
> 
> "Welche Arten von Fehlern gibt es?"
> - Validierungs-Fehler?
> - DB-Constraint-Fehler?
> - Business-Rule-Fehler?
> 
> "Sind Fehlermeldungen **benutzerfreundlich**?"

**Notieren**:
- Error-Handling-Strategie: _______
- **Pain Point**: Sind Fehlermeldungen kryptisch?

#### Frage 2.10: UI-Patterns & Widgets
> "Welche **Standard-UI-Patterns** werden am häufigsten genutzt?"
> - Text-Felder, Checkboxen, Radio Buttons?
> - Grids/Tabellen?
> - Tabs?
> - Trees?
> - Custom Widgets?

**Notieren**:
- Häufige Widgets: _______
- Custom Widgets: _______ (Achtung: Migration-Challenge!)

**Template**: **Forms Mask Catalog** (Excel/Miro-Tabelle)

| Masken-Name | Typ (CRUD/Wizard/Dashboard) | Bounded Context | Nutzungshäufigkeit (H/M/L) | Komplexität (1-5) | Migration-Priorität | Notizen |
|-------------|----------------------------|-----------------|---------------------------|-------------------|---------------------|---------|
| Schaden anlegen | Wizard | Schaden | H | 4 | Hoch | Viele Validierungen |
| Kundensuche | CRUD | Kunde | H | 2 | Mittel | Einfach, guter MVP-Kandidat |
| ... | ... | ... | ... | ... | ... | ... |

---

### Fragenkategorie 3: Stored Procedures & Service Layer (~15min, 10 Fragen)

**Ziel**: Service-Inventar erstellen und Schnittstellen verstehen

#### Frage 3.1: Stored Procedure Organisation
> "Wie sind **Stored Procedures organisiert**?"
> - In Packages?
> - Einzelne Procedures?
> - Nach welchem Schema? (Naming Conventions?)
> 
> "Gibt es eine klare **Trennung** zwischen:"
> - Service-Procedures (wiederverwendbar, API-artig)?
> - Helper-Procedures (intern)?
> - Trigger-Procedures?

**Notieren**:
- Organisationsstruktur: _______
- Naming Conventions: _______
- **Wichtig**: Service-Procedures sind Kandidaten für REST API

#### Frage 3.2: Typische Procedure-Signatur
> "Können Sie uns eine **typische Service-Procedure** zeigen?"
> - Procedure-Name?
> - Input-Parameter (Typen, Strukturen)?
> - Output-Parameter (RETURN, OUT, REF CURSOR)?
> 
> **Live-Beispiel zeigen lassen!**

**Notieren**:
- Beispiel-Procedure: _______
- Signatur dokumentieren (Screenshot oder Code-Snippet)
- **Template**: Service Signature Beispiel

**Beispiel-Template**:
```sql
PROCEDURE get_customer_details (
    p_customer_id IN NUMBER,
    p_customer_info OUT SYS_REFCURSOR,
    p_error_code OUT VARCHAR2,
    p_error_message OUT VARCHAR2
);
```

#### Frage 3.3: Input-Parameter Typen
> "Welche **Oracle-Typen** werden für Input-Parameter genutzt?"
> - Einfache Typen (NUMBER, VARCHAR2, DATE)?
> - RECORD Types?
> - TABLE Types (Collections)?
> - VARRAY?
> 
> "Wenn RECORD/TABLE Types: Wie sind diese definiert?"
> - In Packages?
> - Als separate Types?

**Notieren**:
- Verwendete Typen: _______
- Beispiel für komplexe Typen: _______
- **Migration-Challenge**: Wie mappen wir diese auf JSON/REST?

#### Frage 3.4: Output-Parameter Typen
> "Wie werden **Ergebnisse zurückgegeben**?"
> - RETURN-Wert (bei Functions)?
> - OUT-Parameter?
> - REF CURSOR (für Datensätze)?
> - Kombination?
> 
> "Gibt es Standard-Output-Parameter für Fehlerbehandlung?"
> - Error-Code, Error-Message OUT-Parameter?

**Notieren**:
- Return-Strategie: _______
- Fehlerbehandlungs-Pattern: _______
- **Wichtig**: Standardisierte Fehlerbehandlung erleichtert REST API Mapping

#### Frage 3.5: Aufruf aus Forms
> "Wie rufen Forms-Masken **Stored Procedures** auf?"
> - Direkt über PL/SQL-Block?
> - Forms Built-in EXECUTE_QUERY, etc.?
> - Über spezielle API-Packages?

**Notieren**:
- Aufruf-Mechanismus: _______
- **Unterschied zu REST**: Forms kann direkt PL/SQL ausführen, REST braucht Mapping

#### Frage 3.6: Business-Logik Lokation
> "Wo liegt die **Business-Logik**?"
> - Primär in Stored Procedures?
> - Teilweise in Forms-Masken (Triggers, Program Units)?
> - Beide?
> 
> **Wie viel % würden Sie schätzen?**
> - 80% DB, 20% Forms?
> - 50/50?

**Notieren**:
- Business-Logik-Verteilung: ___% DB, ___% Forms
- **Migrations-Implikation**: Forms-Logik muss ins neue Frontend portiert werden

#### Frage 3.7: Transaktions-Management
> "Wie werden **Transaktionen** gehandhabt?"
> - COMMIT/ROLLBACK in Forms?
> - COMMIT/ROLLBACK in Stored Procedures?
> - Wer ist verantwortlich?
> 
> "Gibt es **lange Transaktionen**?"
> - Multi-Step Wizards mit einer Transaction?
> - Pessimistisches Locking?

**Notieren**:
- Transaktions-Strategie: _______
- **Wichtig**: REST APIs sollten kurze Transaktionen haben (Stateless!)

#### Frage 3.8: Dokumentation
> "Wie sind Stored Procedures **dokumentiert**?"
> - Code-Kommentare?
> - Externe Dokumentation?
> - Gar nicht?
> 
> "Gibt es Beispiele für Procedure-Aufrufe?"
> - Test-Scripts?
> - Integration-Tests?

**Notieren**:
- Dokumentations-Level: _______
- **Pain Point**: Fehlende Dokumentation erschwert Migration

#### Frage 3.9: Versionierung
> "Können Stored Procedures **versioniert** deployed werden?"
> - Können alte und neue Version parallel laufen?
> - Wie wird Rückwärts-Kompatibilität sichergestellt?
> 
> "Gibt es Breaking Changes Prozess?"

**Notieren**:
- Versionierungs-Strategie: _______
- **Wichtig für REST API**: Wie versionieren wir APIs?

#### Frage 3.10: Performance
> "Welche Stored Procedures sind **langsam**?"
> - Performance-Probleme bekannt?
> - Warum? (Komplexe Queries, große Datenmengen, fehlende Indizes?)
> 
> "Gibt es Caching-Strategien?"

**Notieren**:
- Performance-Probleme: _______
- **Optimierungs-Potenzial**: Kann neue Architektur helfen?

**Template**: **Stored Procedure Service Catalog** (Excel/Miro-Tabelle)

| Package | Procedure Name | Geschäftsfunktion | Input (Zusammenfassung) | Output (Zusammenfassung) | Genutzt von Masken | Performance | REST-API-Kandidat? | Notizen |
|---------|---------------|-------------------|-------------------------|--------------------------|-------------------|-------------|-------------------|---------|
| PKG_CUSTOMER | get_customer_details | Kundendaten laden | customer_id (NUMBER) | REF CURSOR (customer_info) | Kundensuche, Vertrag anlegen | OK | Ja | Gut dokumentiert |
| PKG_CLAIM | create_claim | Schaden anlegen | claim_record (RECORD) | claim_id (OUT NUMBER), error (OUT) | Schaden anlegen | Langsam (~2s) | Ja, optimieren | Komplexe Validierung |
| ... | ... | ... | ... | ... | ... | ... | ... | ... |

---

### Fragenkategorie 4: Datenstrukturen & Integrationspunkte (~8min, 5 Fragen)

**Ziel**: Datenmodell und externe Systeme verstehen

#### Frage 4.1: Kern-Daten-Entitäten
> "Was sind die **Kern-Entitäten** im ICIS-Datenmodell?"
> - Kunde, Vertrag, Police, Schaden, Position, ...?
> 
> "Welche Beziehungen gibt es?"
> - Kunde → Vertrag (1:n)?
> - Vertrag → Schaden (1:n)?

**Notieren**:
- Haupt-Entitäten: _______
- Beziehungen: _______
- **Mapping**: Zu Bounded Contexts aus Domain Mapping

#### Frage 4.2: Datenmodell-Enforcement
> "Wie werden **Beziehungen erzwungen**?"
> - Foreign Keys?
> - Triggers?
> - Application-Level (nur in Code)?
> 
> "Gibt es **referentielle Integrität** in der DB?"

**Notieren**:
- Integritäts-Strategie: _______
- **Wichtig**: Wenn nur Application-Level, muss neues Frontend dieselben Regeln haben

#### Frage 4.3: Externe Systeme
> "Mit welchen **externen Systemen** integriert ICIS-Klassik?"
> - GDV (Gesamtverband der Deutschen Versicherungswirtschaft)?
> - SAP?
> - COR Life?
> - DMS (Dokumentenmanagement)?
> - Andere?

**Notieren**:
- Externe Systeme: _______
- **Siehe**: Architektur-Diagramm `architektur_schaubild_icis_gesamt.svg`

#### Frage 4.4: Integrations-Mechanismen
> "**Wie** integriert ICIS-Klassik mit externen Systemen?"
> - Database Links?
> - File Exchange (FTP, etc.)?
> - Web Services (SOAP)?
> - Message Queues (z.B. MQ Series)?
> 
> "Welche **Stored Procedures** sind für Integration zuständig?"

**Notieren**:
- Integration-Typ pro System: _______
- Procedures für Integration: _______
- **Wichtig**: Bleiben diese Integrationen oder müssen sie modernisiert werden?

#### Frage 4.5: Batch-Prozesse
> "Welche **Batch-Prozesse** gibt es?"
> - Nächtliche Jobs?
> - Daten-Synchronisation?
> - Reports?
> - EDI-Versand (z.B. eVB)?
> 
> "Wie werden diese getriggert?"
> - Cron/Scheduler?
> - Oracle Scheduler?

**Notieren**:
- Batch-Prozesse: _______
- **Wichtig**: Bleiben diese oder werden sie modernisiert?

**Template**: **Data Model Overview + Integration Map** (Whiteboard-Skizze)

```
┌─────────────┐         ┌─────────────┐
│   Kunde     │────1:n──│   Vertrag   │
└─────────────┘         └─────────────┘
                             │
                           1:n
                             │
                        ┌─────────────┐
                        │   Schaden   │
                        └─────────────┘

Externe Systeme:
- GDV: MQ Series (Stored Proc: PKG_GDV.send_message)
- SAP: DB Link (Stored Proc: PKG_SAP.sync_financials)
- DMS: Web Service (Stored Proc: PKG_DMS.archive_document)
```

---

### Fragenkategorie 5: Pain Points & Migrations-Readiness (~7min, 2 Fragen)

**Ziel**: Probleme und Constraints identifizieren

#### Frage 5.1: Größte Pain Points
> "Was sind die **größten Probleme** mit ICIS-Klassik?"
> 
> **Performance**:
> - Welche Masken sind langsam?
> - Welche Procedures sind langsam?
> 
> **Usability**:
> - Was beklagen Nutzer am meisten?
> - Wo sind Workflows umständlich?
> 
> **Wartbarkeit**:
> - Was ist schwer zu ändern?
> - Wo ist technische Schuld?
> 
> **Deployment**:
> - Ist Deployment komplex/risikoreich?

**Notieren** (Pain Points Catalog):
- Performance: _______
- Usability: _______
- Wartbarkeit: _______
- Deployment: _______
- Andere: _______

**Priorisierung**: Welche Pain Points sind kritisch zu lösen?

#### Frage 5.2: Was MUSS unverändert bleiben?
> "Welche Aspekte von ICIS-Klassik **dürfen sich nicht ändern** bei der Modernisierung?"
> 
> **Technisch**:
> - Stored Procedures Business-Logik?
> - Datenbank-Schema?
> - Integrations-Protokolle?
> 
> **Fachlich**:
> - Bestimmte Workflows?
> - Compliance-Anforderungen?
> - Nutzer-Erwartungen?

**Notieren** (Constraints):
- Technische Constraints: _______
- Fachliche Constraints: _______
- **Wichtig**: Diese Constraints definieren Modernisierungs-Boundaries

**Template**: **Pain Points & Constraints Canvas** (2-Spalten)

| 🔴 Pain Points | ✅ Muss bleiben (Constraints) |
|---------------|------------------------------|
| Langsame Maske X (~5s Ladezeit) | Stored Procedures unverändert |
| Deployment dauert 4h + Downtime | Datenbank-Schema unverändert |
| Fehlerhafte Fehlermeldungen | GDV-Integration (MQ Series) |
| Keine Mobile-Unterstützung | Validierungs-Regeln (identisch) |
| Schwer zu testen | Batch-Jobs (unverändert) |

---

## Part B: ICIS+ (Vaadin) Deep Dive

**Dauer**: 30-40 Minuten  
**Ziel**: ICIS+ Architektur verstehen, wiederverwendbare Komponenten identifizieren, Wrapper Services analysieren

### Ablauf

**Einführung (3min)**:
- Kontext: "ICIS+ ist bereits eine Modernisierung von ICIS-Klassik. Wir möchten verstehen, was wiederverwendbar ist."
- Ziel: "Vaadin-Komponenten, Wrapper-Services und Best Practices identifizieren"

**WGV-Präsentation + Strukturierte Fragen (27-37min)**:

---

### Fragenkategorie 6: ICIS+ Architektur & Technologie-Stack (~10min, 8 Fragen)

**Ziel**: Technische Basis von ICIS+ verstehen

#### Frage 6.1: Vaadin Version & Setup
> "Welche **Vaadin-Version** nutzen Sie?"
> - Vaadin 8, 14, 23, 24?
> - Flow oder Framework 8?
> 
> "Deployment-Modus?"
> - Server-side rendering?
> - Client-side (Hilla)?

**Notieren**:
- Vaadin Version: _______
- Deployment-Modus: _______
- **Wichtig**: Vaadin 8 (legacy) vs. Vaadin 23+ (modern)

#### Frage 6.2: Java Framework Stack
> "Welche **Java-Frameworks** nutzen Sie?"
> - Spring Boot? Welche Version?
> - Spring MVC?
> - Andere?
> 
> "Build-Tool?"
> - Maven oder Gradle?

**Notieren**:
- Java Version: _______
- Spring Boot Version: _______
- Build-Tool: _______

#### Frage 6.3: Hibernate & ORM
> "Wie wird **Hibernate** genutzt?"
> - JPA-Entities für Datenbank-Zugriff?
> - Oder nur für spezifische Bereiche?
> 
> "Oder wird direkt JDBC/Stored Procedures aufgerufen?"

**Notieren**:
- Hibernate-Nutzung: _______
- **Wichtig**: Wenn Hibernate, dann ORM-Mapping vorhanden (wiederverwendbar?)

#### Frage 6.4: Application Server
> "Auf welchem **Application Server** läuft ICIS+?"
> - Tomcat?
> - Embedded Tomcat (Spring Boot)?
> - Andere?

**Notieren**:
- Application Server: _______

#### Frage 6.5: Frontend Build
> "Wie wird das **Frontend gebaut**?"
> - Maven Frontend Plugin?
> - npm/webpack direkt?
> - Vaadin-eigener Build-Prozess?
> 
> "Gibt es **Custom Frontend-Code** (TypeScript/JavaScript)?"

**Notieren**:
- Build-Prozess: _______
- Custom Frontend-Code: Ja/Nein, Details: _______

#### Frage 6.6: State Management
> "Wie wird **State** gehandhabt?"
> - Vaadin Session?
> - Spring Beans (Singleton, Session-Scope, Request-Scope)?
> 
> "Gibt es **Stateful Components**?"

**Notieren**:
- State-Management: _______
- **Wichtig**: Stateless REST API vs. Stateful Vaadin

#### Frage 6.7: Authentifizierung & Autorisierung
> "Wie funktioniert **Auth** in ICIS+?"
> - Dieselbe wie ICIS-Klassik?
> - Spring Security?
> - Custom?
> 
> "Wie wird Autorisierung geprüft?"
> - Annotations (@Secured, @PreAuthorize)?
> - Programmatisch?

**Notieren**:
- Auth-Mechanismus: _______
- **Mapping**: Kann neues Frontend dasselbe nutzen?

#### Frage 6.8: Deployment & Hosting
> "Wie wird ICIS+ **deployed**?"
> - On-Premise VMs?
> - Containerisiert (Docker)?
> - Cloud (Azure)?
> 
> "Wie oft wird deployed?"
> - Continuous Deployment?
> - Release-Zyklen?

**Notieren**:
- Deployment: _______
- **Vorteil**: Wenn schon containerisiert, Erfahrung vorhanden

**Template**: **ICIS+ Technology Stack Canvas**

```
┌─────────────────────────────────────────────┐
│  ICIS+ Technologie-Stack                    │
├─────────────────────────────────────────────┤
│ Vaadin: ________________________________    │
│ Java: __________________________________    │
│ Spring Boot: ___________________________    │
│ Hibernate: _____________________________    │
│ Application Server: ____________________    │
│ Build: _________________________________    │
│ State Management: ______________________    │
│ Auth: __________________________________    │
│ Deployment: ____________________________    │
└─────────────────────────────────────────────┘
```

---

### Fragenkategorie 7: Vaadin-Komponenten & UI-Patterns (~8min, 7 Fragen)

**Ziel**: Wiederverwendbare UI-Patterns identifizieren

#### Frage 7.1: Häufigste Vaadin-Komponenten
> "Welche **Vaadin-Komponenten** nutzen Sie am meisten?"
> - TextField, ComboBox, Grid, DatePicker?
> - Layouts (VerticalLayout, HorizontalLayout)?
> - Dialog, Notification?

**Notieren**:
- Top-Components: _______

#### Frage 7.2: Custom Vaadin Components
> "Haben Sie **eigene Vaadin-Komponenten** entwickelt?"
> - Welche?
> - Warum custom? (fehlende Standard-Komponente?)
> 
> "Sind diese **wiederverwendbar** für das neue Frontend?"
> - Könnten Patterns in React/Angular portiert werden?

**Notieren**:
- Custom Components: _______
- Wiederverwendbarkeits-Assessment: _______
- **Wichtig**: UI-Patterns extrahieren, nicht Code 1:1 portieren

#### Frage 7.3: Formular-Struktur
> "Wie sind **Formulare** in Vaadin strukturiert?"
> - Binder-Pattern genutzt?
> - Validatoren?
> 
> **Live-Beispiel zeigen lassen!**

**Notieren**:
- Form-Pattern: _______
- **Übertragbarkeit**: Ähnliches Pattern in React (React Hook Form, Formik)?

#### Frage 7.4: Navigation
> "Wie funktioniert **Navigation** in ICIS+?"
> - Vaadin Router?
> - Custom Navigation?
> - URL-basiert oder programmatisch?

**Notieren**:
- Navigation-Mechanismus: _______
- **Wichtig**: REST-basiertes Frontend braucht client-side Routing

#### Frage 7.5: Master-Detail Views
> "Wie sind **Master-Detail-Ansichten** umgesetzt?"
> - Beispiel: Vertrag (Master) mit Positionen (Detail)
> - Grid mit Detail-Panel?
> - Separate Views?

**Notieren**:
- Master-Detail-Pattern: _______

#### Frage 7.6: Responsive & Mobile
> "Ist ICIS+ **responsive**?"
> - Funktioniert es auf Tablets/Smartphones?
> - Vaadin Responsive Layouts genutzt?
> 
> "Ist Mobile-Support gewünscht für neues Frontend?"

**Notieren**:
- Responsive: Ja/Nein
- Mobile-Anforderung für neues Frontend: _______

#### Frage 7.7: UI-Pattern-Extraktion
> "Welche **UI-Patterns** aus Vaadin funktionieren gut und sollten beibehalten werden?"
> - Bestimmte Layouts?
> - Interaktionsmuster?
> - Farbschema, Styling?

**Notieren**:
- Bewährte Patterns: _______
- **Übertragung**: Diese Patterns als Inspiration für neues Frontend

**Template**: **Vaadin Component Inventory** (Tabelle)

| Component Name | Typ (Standard/Custom) | Verwendung | Wiederverwendbarkeit | Migrations-Strategie | Notizen |
|----------------|----------------------|------------|---------------------|---------------------|---------|
| TextField | Standard | Hoch | N/A (Standard in allen Frameworks) | Standard-Component in React/Angular | - |
| CustomerSearchCombo | Custom | Hoch | Mittel | Pattern portieren, nicht Code | Gute Typeahead-Logik |
| ClaimWizardStepper | Custom | Mittel | Hoch | Pattern portieren | Mehrstufiger Prozess, gutes UX |
| ... | ... | ... | ... | ... | ... |

---

### Fragenkategorie 8: Wrapper Services & Business Logic Layer (~10min, 8 Fragen)

**Ziel**: Wrapper Services verstehen und Wiederverwendbarkeit bewerten

#### Frage 8.1: Was sind Wrapper Services?
> "Können Sie **Wrapper Services** erklären?"
> - Java-Services, die Stored Procedures aufrufen?
> - Wo liegen sie? (Package-Struktur?)
> - Wer hat sie entwickelt? (Standard-Ansatz oder custom?)

**Notieren**:
- Definition: _______
- Package: _______

#### Frage 8.2: Aufruf von Stored Procedures
> "**Wie** rufen Wrapper Services Stored Procedures auf?"
> - JDBC direkt?
> - Spring JdbcTemplate?
> - MyBatis?
> - Hibernate Stored Procedure Calls?
> 
> **Live-Code-Beispiel zeigen lassen!**

**Notieren**:
- Technologie: _______
- Code-Beispiel (Screenshot): _______

#### Frage 8.3: Typ-Mapping (Java ↔ Oracle)
> "Wie werden **Oracle-Typen** auf **Java-Typen** gemappt?"
> - NUMBER → Long/BigDecimal?
> - VARCHAR2 → String?
> - DATE → java.util.Date / LocalDate?
> 
> "Wie werden **komplexe Oracle-Typen** gehandhabt?"
> - RECORD Types → Java Objects?
> - TABLE Types → List<>?
> - REF CURSOR → ResultSet / Stream?

**Notieren**:
- Mapping-Strategie: _______
- Beispiel für komplexe Typen: _______
- **Wichtig**: Dieses Mapping ist wiederverwendbar für REST API!

#### Frage 8.4: Business-Logik in Wrapper Services
> "Enthalten Wrapper Services **zusätzliche Business-Logik**?"
> - Nur Mapping (dünner Wrapper)?
> - Oder auch Validierung, Transformation, etc.?
> 
> "Falls ja: Welche Art von Logik?"

**Notieren**:
- Logik-Anteil: _______
- **Wichtig**: Wenn nur Mapping → gut wiederverwendbar

#### Frage 8.5: Transaktions-Management
> "Wie wird **Transaktions-Management** gehandhabt?"
> - Spring @Transactional?
> - Programmatisch?
> 
> "Wer macht COMMIT/ROLLBACK?"
> - Wrapper Service?
> - Stored Procedure?

**Notieren**:
- Transaction-Strategie: _______
- **Wichtig**: REST API sollte dasselbe Modell nutzen

#### Frage 8.6: Wiederverwendbarkeit für REST API
> "Können Wrapper Services **als Backend für REST API** dienen?"
> - Müssten sie refactored werden?
> - Oder sind sie schon stateless und wiederverwendbar?
> 
> "Was müsste geändert werden?"

**Notieren**:
- Wiederverwendbarkeit: Hoch/Mittel/Niedrig
- Änderungen nötig: _______
- **Entscheidend**: Können wir Zeit sparen durch Wiederverwendung?

#### Frage 8.7: Testing
> "Wie werden Wrapper Services **getestet**?"
> - Unit-Tests?
> - Integration-Tests (mit echter DB)?
> - Mocking?
> 
> "Test-Coverage?"

**Notieren**:
- Test-Strategie: _______
- Coverage: ____%
- **Vorteil**: Wenn gut getestet, vertrauenswürdige Basis

#### Frage 8.8: Dokumentation
> "Wie sind Wrapper Services **dokumentiert**?"
> - JavaDoc?
> - Externe Dokumentation?
> 
> "Gibt es **API-Spezifikationen**?"
> - Swagger/OpenAPI (wenn REST-ähnlich)?

**Notieren**:
- Dokumentation: _______
- **Gap**: Wenn keine Doku, muss für REST API erstellt werden

**Template**: **Wrapper Service Catalog** (Tabelle)

| Service Name | Package | Wrapped Stored Procedure | Input (Java) | Output (Java) | Business-Logik? | Wiederverwendbar für REST? | Änderungen nötig | Notizen |
|--------------|---------|--------------------------|--------------|---------------|----------------|---------------------------|-----------------|---------|
| CustomerService | com.wgv.customer | PKG_CUSTOMER.get_details | Long customerId | CustomerDTO | Nein, nur Mapping | Ja | @RestController hinzufügen | Gut dokumentiert |
| ClaimService | com.wgv.claim | PKG_CLAIM.create_claim | ClaimDTO | Long claimId | Ja, Validierung | Mittel | Validierung refactoren | Komplexe Logik |
| ... | ... | ... | ... | ... | ... | ... | ... | ... |

---

### Fragenkategorie 9: ICIS+ vs. ICIS-Klassik Vergleich (~7min, 2 Fragen)

**Ziel**: Unterschiede und Lessons Learned extrahieren

#### Frage 9.1: Implementierungs-Unterschiede
> "Für **denselben Geschäftsprozess**: Wie unterscheidet sich die Implementierung?"
> 
> **Beispiel**: "Kunde anlegen" in ICIS-Klassik vs. ICIS+
> 
> **Stored Procedures**:
> - Dieselben Stored Procedures genutzt?
> - Oder neue/angepasste Procedures?
> 
> **Datenmodell**:
> - Dasselbe Schema?
> - Erweitert?
> 
> **Business Rules**:
> - Identisch?
> - Weiterentwickelt?

**Notieren**:
- Stored Procedures: Gleich/Unterschiedlich: _______
- Datenmodell: Gleich/Erweitert: _______
- Business Rules: Identisch/Weiterentwickelt: _______
- **Wichtig**: Wenn Procedures gleich → guter Sign für Wiederverwendung

#### Frage 9.2: Lessons Learned
> "Was haben Sie bei der **ICIS+ Migration gelernt**?"
> 
> **Was lief gut?**
> - Technologie-Entscheidungen?
> - Prozess?
> - Team-Struktur?
> 
> **Was würden Sie anders machen?**
> - Technische Entscheidungen überdenken?
> - Scope-Management?
> - Testing-Strategie?

**Notieren**:
- ✅ Was lief gut: _______
- ❌ Was würden wir anders machen: _______
- **Anwenden**: Diese Lessons auf neue Modernisierung anwenden!

**Template**: **ICIS vs. ICIS+ Comparison Matrix** (siehe Part C)

---

## Part C: Vergleichende Analyse & Migrations-Implikationen

**Dauer**: 20-30 Minuten  
**Ziel**: Erkenntnisse synthetisieren und Migrations-Strategie skizzieren

### Aktivität 1: ICIS vs. ICIS+ Comparison Matrix (~15min)

**Format**: Gemeinsames Ausfüllen eines großen Canvas (Miro/Whiteboard)

**Struktur**: 3-Spalten-Matrix

| Dimension | ICIS-Klassik (Forms) | ICIS+ (Vaadin) | Implikationen für Neues Frontend |
|-----------|---------------------|----------------|----------------------------------|
| **Technology Stack** | | | |
| **UI Patterns** | | | |
| **Service Layer** | | | |
| **Data Mapping** | | | |
| **Transaction Mgmt** | | | |
| **User Base** | | | |
| **Deployment** | | | |
| **Maintenance** | | | |

**Ausfüllen während Session**:

#### Zeile: Technology Stack
- **ICIS-Klassik**: Forms 11g + Oracle DB 19c
- **ICIS+**: Vaadin 14 + Spring Boot 2.7 + Hibernate + Oracle DB 19c
- **Implikationen**: Neues Frontend: React/Angular + Spring Boot (wiederverwendbar!) + Oracle DB

#### Zeile: UI Patterns
- **ICIS-Klassik**: Forms-basiert, tastaturgesteuert, Desktop-only
- **ICIS+**: Web-basiert, Vaadin-Komponenten, Server-side Rendering
- **Implikationen**: Neues Frontend: Client-side Rendering (React/Angular), Responsive, Keyboard-Shortcuts beibehalten

#### Zeile: Service Layer
- **ICIS-Klassik**: Direkter Aufruf von Stored Procedures aus Forms
- **ICIS+**: Java Wrapper Services rufen Stored Procedures auf
- **Implikationen**: Wrapper Services als Basis für REST API nutzen → Zeit sparen!

#### Zeile: Data Mapping
- **ICIS-Klassik**: Forms Built-in Mapping (Oracle Typen ↔ Forms)
- **ICIS+**: Java/Hibernate ORM Mapping (Oracle Typen ↔ Java Objects)
- **Implikationen**: Java-Mapping wiederverwendbar, JSON-Serialisierung hinzufügen

#### Zeile: Transaction Management
- **ICIS-Klassik**: Forms-gesteuert (COMMIT in Forms Trigger)
- **ICIS+**: Spring @Transactional (deklarativ)
- **Implikationen**: REST API nutzt Spring @Transactional (bewährt in ICIS+)

#### Zeile: User Base
- **ICIS-Klassik**: Power User, hohe Frequenz, Experten-Workflows
- **ICIS+**: Gemischt (Power User + Gelegenheitsnutzer)
- **Implikationen**: Neues Frontend muss beide bedienen: Forms für Power User, Conversational UI für Gelegenheitsnutzer

#### Zeile: Deployment
- **ICIS-Klassik**: Client-Server, Thick Client, komplexe Installation
- **ICIS+**: Web App, Server-side Rendering, einfacher (Browser-basiert)
- **Implikationen**: Neues Frontend: Cloud-native (Azure), containerisiert (Docker/K8s)

#### Zeile: Maintenance
- **ICIS-Klassik**: Hoch (Legacy, schwer zu ändern)
- **ICIS+**: Mittel (modern, aber noch DB-gekoppelt)
- **Implikationen**: Neues Frontend: REST API entkoppelt Frontend von DB → bessere Wartbarkeit

**Facilitator-Fragen während Ausfüllen**:
- "Sehen Sie Muster, die wir wiederholen sollten?"
- "Was sollten wir aus ICIS+ übernehmen?"
- "Was sollten wir aus ICIS-Klassik bewahren?"

---

### Aktivität 2: Migration Strategy Canvas (~10-15min)

**Format**: 3-Spalten Canvas

**Struktur**:

| ✅ Unverändert lassen (Keep) | 🔄 Wiederverwenden/Anpassen (Reuse/Adapt) | 🆕 Neu bauen (Build New) |
|------------------------------|-------------------------------------------|-------------------------|
| | | |

**Gemeinsam ausfüllen**:

#### Spalte 1: ✅ Unverändert lassen (Keep)

**Frage**: "Was MUSS unverändert bleiben?"

- ✅ **Oracle Database** (Schema, Daten)
- ✅ **Stored Procedures** (Service Layer Business-Logik)
- ✅ **Business Rules** (Validierungen, Berechnungen in DB)
- ✅ **Externe Integrationen** (GDV, SAP, COR Life, DMS)
- ✅ **Batch-Jobs** (icis-jobs, icis-print)
- ✅ **Compliance-Anforderungen** (regulatorische Vorgaben)

**Notieren**: Warum müssen diese bleiben?
- Zu risikoreich zu ändern?
- Zu hoher Aufwand?
- Externe Abhängigkeiten?

#### Spalte 2: 🔄 Wiederverwenden/Anpassen (Reuse/Adapt)

**Frage**: "Was können wir aus ICIS+ oder ICIS-Klassik übernehmen und anpassen?"

- 🔄 **Wrapper Services** (aus ICIS+)
  - Anpassung: Als REST API exponieren (@RestController)
  - Anpassung: JSON-Serialisierung hinzufügen
  - Anpassung: OpenAPI/Swagger-Dokumentation

- 🔄 **Vaadin UI-Patterns** (aus ICIS+)
  - Anpassung: Patterns in React/Angular portieren (nicht Code 1:1)
  - Beispiel: CustomerSearchCombo → React Autocomplete Component

- 🔄 **Test-Daten & Szenarien** (aus ICIS-Klassik & ICIS+)
  - Anpassung: Integration-Tests für REST API

- 🔄 **Authentifizierungs-Mechanismus**
  - Anpassung: Wenn LDAP/SSO → JWT für REST API

- 🔄 **Business-Logik aus Forms** (wenn nicht in DB)
  - Anpassung: In neues Frontend (React/Angular) oder REST API portieren

**Notieren**: Welche Änderungen nötig? Aufwand?

#### Spalte 3: 🆕 Neu bauen (Build New)

**Frage**: "Was muss komplett neu entwickelt werden?"

- 🆕 **Modernes Frontend** (React/Angular)
  - Responsive Design
  - Accessibility (WCAG 2.1 AA)
  - Hybrid UI (Forms + Conversational)

- 🆕 **Integration Layer** (Spring Boot + REST APIs)
  - RESTful API-Design
  - API-Versionierung
  - Rate Limiting, Caching

- 🆕 **AI Integration**
  - MCP Server (wenn entschieden)
  - Chatbot UI-Komponenten
  - AI-gestützte Features (z.B. Smart Search, Auto-Complete)

- 🆕 **Moderne UX**
  - Benutzerfreundliche Workflows
  - Reduzierung von Klicks
  - Contextual Help

- 🆕 **Cloud-Deployment-Infrastruktur**
  - Azure Kubernetes Service (AKS)
  - CI/CD Pipelines
  - Monitoring & Observability (Azure Monitor, Application Insights)

**Notieren**: Warum neu? Gibt es Alternativen?

---

### Facilitator-Prompts für Canvas-Diskussion

**Während Ausfüllen**:

1. **"Welche Stored Procedures aus ICIS-Klassik sind bereits in ICIS+ gewrappt?"**
   - → Diese sind einfach als REST API zu exponieren

2. **"Können wir ICIS+ Wrapper Services als REST API Backend nutzen ohne große Refactorings?"**
   - → Bewertung der Wiederverwendbarkeit

3. **"Welche Vaadin UI-Patterns funktionieren gut und sollten das neue Frontend inspirieren?"**
   - → UI/UX Best Practices extrahieren

4. **"Gibt es Teile von ICIS-Klassik, die in ICIS+ NICHT migriert wurden?"**
   - → Warum nicht? Sind sie noch relevant?

5. **"Welche Pain Points von ICIS-Klassik wurden durch ICIS+ gelöst?"**
   - → Diese Verbesserungen auch im neuen Frontend

6. **"Welche Pain Points von ICIS-Klassik bestehen in ICIS+ noch?"**
   - → Diese im neuen Frontend adressieren!

---

## Templates & Deliverables

### Vorbereitung (vor Workshop)

**Miro/Whiteboard Templates**:

1. **Architecture Overview Canvas** (ICIS-Klassik)
2. **Forms Mask Catalog** (Tabelle mit Spalten: Name, Typ, Bounded Context, Nutzung, Komplexität, Priorität)
3. **Stored Procedure Service Catalog** (Tabelle mit Package, Procedure, Funktion, I/O, Performance, REST-Kandidat)
4. **ICIS+ Technology Stack Canvas**
5. **Vaadin Component Inventory** (Tabelle mit Component, Typ, Verwendung, Wiederverwendbarkeit)
6. **Wrapper Service Catalog** (Tabelle mit Service, Wrapped Procedure, I/O, Logik, Wiederverwendbarkeit)
7. **ICIS vs. ICIS+ Comparison Matrix** (3-Spalten)
8. **Migration Strategy Canvas** (Keep/Reuse/Build-New)
9. **Pain Points & Constraints Canvas** (2-Spalten)

**Pre-Workshop Requests an WGV**:
- [ ] 2-3 Beispiel-Masken aus ICIS-Klassik (Screenshots oder Demo-Zugriff)
- [ ] 2-3 Beispiel Stored Procedures (Code oder Dokumentation)
- [ ] Zugriff auf ICIS+ Demo-Umgebung (oder Screenshots)
- [ ] Beispiel Wrapper Service Code (1-2 Services)

---

### Erwartete Outputs

Am Ende der ICIS Deep Dive Session:

✅ **Architecture Overview**: ICIS-Klassik und ICIS+ dokumentiert  
✅ **Forms Mask Catalog**: 20-50 Masken kategorisiert (Typ, Bounded Context, Komplexität)  
✅ **Stored Procedure Service Catalog**: 10-30 Service-Procedures dokumentiert  
✅ **Wrapper Service Catalog**: 5-20 ICIS+ Services bewertet (Wiederverwendbarkeit)  
✅ **Vaadin Component Inventory**: Custom Components identifiziert  
✅ **Pain Points Catalog**: 5-15 Pain Points priorisiert  
✅ **Constraints List**: Technische & fachliche Constraints dokumentiert  
✅ **ICIS vs. ICIS+ Comparison**: Klare Unterschiede und Gemeinsamkeiten  
✅ **Migration Strategy Canvas**: Keep/Reuse/Build-New Kategorisierung  

---

## Integration mit weiteren Tag 1 Aktivitäten

### Vorher (Input für ICIS Deep Dive)

**Domain Mapping Session** liefert:
- Bounded Contexts → Masken-Kategorisierung
- Context Map → Verständnis externe Integrationen
- Domain Events → Stored Procedure Funktionen zuordnen

### Nachher (Output für nachfolgende Aktivitäten)

**ICIS Deep Dive Output fließt ein in**:

1. **Analyse von Masken** (~1.5-2h):
   - Forms Mask Catalog als Basis
   - Detaillierte Analyse von 5-10 ausgewählten Masken
   - Mapping zu Bounded Contexts

2. **Anwendungskonzept (UI/UX) Skizze** (~1.5h):
   - Vaadin UI-Patterns als Inspiration
   - Pain Points → UX-Verbesserungen
   - Power User Workflows (aus Forms) vs. Conversational UI

3. **AI Features Diskussion** (~1h):
   - Stored Procedures → Welche können AI-unterstützt aufgerufen werden?
   - Pain Points → AI-Automatisierungs-Potenzial
   - Wrapper Services → Basis für MCP Tools

4. **Initial Scope Discussion** (~1h):
   - Forms Mask Catalog → MVP-Kandidaten
   - Constraints → Scope-Grenzen
   - Wiederverwendbarkeit (ICIS+) → Aufwandsschätzung

---

## Timing & Pausen

### Empfohlener Zeitplan

**Option A: Vormittag (10:25-12:00, 95min)**

| Zeit | Aktivität | Dauer |
|------|-----------|-------|
| 10:25-10:30 | Einführung ICIS Deep Dive | 5min |
| 10:30-11:15 | Part A: ICIS-Klassik Deep Dive | 45min |
| 11:15-11:50 | Part B: ICIS+ Deep Dive | 35min |
| 11:50-12:00 | Part C: Vergleichende Analyse (Start) | 10min |

**Fortsetzung nach Mittagspause (13:00-13:15)**:
- 13:00-13:15 | Part C: Vergleichende Analyse (Abschluss) | 15min

**Total**: 95min (passt in verfügbare Zeit)

**Option B: Nachmittag (13:00-14:30, 90min)**

| Zeit | Aktivität | Dauer |
|------|-----------|-------|
| 13:00-13:05 | Einführung ICIS Deep Dive | 5min |
| 13:05-13:45 | Part A: ICIS-Klassik Deep Dive | 40min |
| 13:45-14:15 | Part B: ICIS+ Deep Dive | 30min |
| 14:15-14:30 | Part C: Vergleichende Analyse | 15min |

**Total**: 90min (knapp, aber machbar)

---

## Facilitator-Checkliste

### Vor der Session

- [ ] **Miro/Whiteboard vorbereitet** mit allen Templates
- [ ] **WGV-Präsentation koordiniert**: Wer zeigt ICIS-Klassik? Wer zeigt ICIS+?
- [ ] **Demo-Zugriffe getestet**: Können WGV live zeigen?
- [ ] **Architektur-Diagramme bereit**: `architektur_schaubild_icis_gesamt.svg` sichtbar
- [ ] **Beispiel-Code angefordert**: Stored Procedures, Wrapper Services
- [ ] **Rollen geklärt**: Wer fragt (codecentric)? Wer dokumentiert (codecentric)?

### Während der Session

- [ ] **Timeboxing einhalten**: Timer für jede Fragenkategorie
- [ ] **Aktiv dokumentieren**: Templates ausfüllen in Echtzeit
- [ ] **Visuelle Notizen**: Screenshots von Live-Demos
- [ ] **Parking Lot**: Technische Details für Tag 2 (z.B. "Wie genau funktioniert Stored Procedure X?")
- [ ] **Engagement sicherstellen**: Alle Teilnehmer einbinden (Nutzer, Architekten, Developers)

### Nach der Session

- [ ] **Templates finalisieren**: Alle Notizen sauber dokumentieren
- [ ] **Screenshots organisieren**: Live-Demo-Aufnahmen beschriften
- [ ] **Service-Kataloge exportieren**: Excel/CSV für weitere Analyse
- [ ] **Migration Strategy Canvas teilen**: Mit WGV abgleichen
- [ ] **Vorbereitung Tag 2**: Service-Inventar für technische Validierung

---

## Häufige Facilitator-Herausforderungen

### Challenge 1: "Zu technisch für Nicht-Entwickler"

**Symptom**: Nutzer/PO verlieren Interesse bei Stored Procedure-Details

**Lösung**:
- **Parallele Sessions** in Betracht ziehen:
  - Technische Teilnehmer (Architekten, Developers): Tiefer in Stored Procedures, Wrapper Services
  - Nicht-technische Teilnehmer (Nutzer, PO): Fokus auf UI-Patterns, Pain Points
- Falls nicht möglich: Balance finden
  - Technische Details kurz halten (High-Level)
  - Nutzer-relevante Themen (Pain Points, UX) ausführlicher

### Challenge 2: "WGV möchte alles zeigen"

**Symptom**: WGV präsentiert zu detailliert, 90min werden zu 3h

**Lösung**:
- **Timeboxing rigoros**: Timer sichtbar machen
- **Fokussierte Fragen**: "Zeigen Sie uns nur **ein repräsentatives Beispiel**"
- **Parking Lot**: "Spannend! Können wir das vertiefen in einer separaten Session?"
- **Priorisierung**: "Von Ihren 50 Stored Procedures: Welche 5 sind am wichtigsten?"

### Challenge 3: "Keine Dokumentation vorhanden"

**Symptom**: WGV kann Stored Procedures nicht erklären, keine Doku

**Lösung**:
- **Live-Code-Review**: Öffnen Sie den Code gemeinsam, analysieren Sie on-the-fly
- **Reverser-Engineering**: Fragen Sie: "Was macht dieser Procedure? Wer nutzt ihn?"
- **Pragmatisch**: Akzeptieren Sie Lücken, dokumentieren Sie "Unknown" in Templates
- **Folge-Action**: "Für MVP-Scope müssen wir diese Procedures dokumentieren" → Tag 2 Aufgabe

### Challenge 4: "ICIS+ ist noch nicht produktiv"

**Symptom**: ICIS+ nur teilweise deployed, wenig Erfahrung

**Lösung**:
- **Fokus auf Code, nicht Production**: Analysieren Sie Code-Patterns, auch wenn nicht live
- **Lessons Learned aus Entwicklung**: "Was haben Sie beim Entwickeln gelernt?"
- **Vorsichtige Wiederverwendungs-Bewertung**: Markieren Sie "Ungetestet in Production" in Katalogen

### Challenge 5: "Zu viele unterschiedliche Stored Procedure Patterns"

**Symptom**: Keine Standard-Signaturen, jede Procedure anders

**Lösung**:
- **Muster-Identifikation**: "Können wir 3-5 typische Patterns identifizieren?"
- **Kategorisierung**: Pattern A (einfach), Pattern B (mittel), Pattern C (komplex)
- **Migration-Implikation**: "Für REST API müssen wir standardisieren" → Tag 2 Entscheidung

---

## Erfolgskriterien

Am Ende der ICIS Deep Dive Session haben wir erfolgreich:

✅ **Gemeinsames Verständnis** von ICIS-Klassik und ICIS+ Architekturen  
✅ **Dokumentiertes Service-Inventar** mit 10-30 Stored Procedures  
✅ **Wiederverwendbarkeits-Assessment** von ICIS+ Wrapper Services (Hoch/Mittel/Niedrig)  
✅ **Identifizierte Pain Points** (5-15 priorisiert)  
✅ **Klare Constraints** (Was muss unverändert bleiben)  
✅ **Vergleichs-Matrix** ICIS-Klassik vs. ICIS+ ausgefüllt  
✅ **Migrations-Strategie Canvas** mit Keep/Reuse/Build-New Kategorien  
✅ **Input für Scope-Diskussion**: Welche Masken sind MVP-Kandidaten?  
✅ **Input für AI-Features**: Welche Stored Procedures sind AI-ready?  

**Nächster Schritt**: Detaillierte Maskenanalyse und Scope-Festlegung basierend auf Deep Dive Erkenntnissen

---

## Referenzen & Verbindungen zu anderen Dokumenten

### Kontext-Dokumente

- **Architektur-Diagramme**: `diagrams/architektur_schaubild_icis_gesamt.svg`
- **Architektur-Interpretation**: `context/architektur_schaubild_icis_gesamt.md`
- **Oracle Forms Details**: `context/icis_oracle_forms_architektur.md`
- **WGV Erwartungen**: `context/Modernisierungsworkshop-Draft.md`
- **Workshop Mapping**: `context/workshop_mapping.md` (Gap-Analyse)

### Andere Facilitation Guides

- **Domain Mapping**: `facilitation/tag1_domain_mapping_guide.md` (liefert Input: Bounded Contexts)
- **Decision Frameworks**: `facilitation/decision_frameworks.md` (für spätere Entscheidungen)

### Technische Referenzen

- **PL/SQL Functions vs. Procedures**: `context/plsql_functions_vs_procedures.md`
- **UX/UI Grundlagen**: `context/gestaltgesetze_ux_laws_cognitive_bias.md` (für UI-Pattern-Analyse)

---

**Erstellt**: 2026-04-14  
**Autor**: Sócrates Ponce (codecentric)  
**Workshop**: WGV ICIS Modernisierung, 28-30 April 2026  
**Version**: 1.0
