# ICIS Deep Dive - Facilitator Cheat Sheet

**Dauer**: 90-120min | **Ziel**: ICIS-Klassik & ICIS+ Architektur verstehen, Service-Inventar erstellen, Wiederverwendbarkeit bewerten

---

## 🎯 Schnellübersicht

| Part | Dauer | Fokus | Key Output |
|------|-------|-------|------------|
| **A: ICIS-Klassik** | 40-50min | Oracle Forms + Stored Procedures | Service Catalog, Pain Points |
| **B: ICIS+** | 30-40min | Vaadin + Wrapper Services | Component Inventory, Reusability Assessment |
| **C: Vergleich** | 20-30min | ICIS vs. ICIS+ Analyse | Migration Strategy Canvas |

---

## Part A: ICIS-Klassik Deep Dive (40-50min)

### Kategorie 1: Architektur & Tech Stack (~10min, 8 Fragen)

**🔑 Kernfragen**:
- Welche Oracle Forms Version? Oracle DB Version?
- Deployment-Modell? (Forms Server, Client-Zugriff)
- Authentifizierung/Autorisierung? (LDAP, SSO, DB?)
- Session-Management? Connection Pooling?

**📋 Template**: Architecture Overview Canvas

---

### Kategorie 2: Forms-Masken (~10min, 10 Fragen)

**🔑 Kernfragen**:
- Masken-Typen? (CRUD, Wizards, Dashboards, Reports)
- **Top 20% häufigste Masken?** (MVP-Kandidaten!)
- **Komplexeste Masken?** (NICHT im MVP!)
- Masken-Organisation? (Nach Modul, Bounded Context?)
- Navigation? (Menü, Shortcuts, Workflow?)
- Master-Detail Pattern?
- Datenvalidierung? (Client/Server?)

**📋 Template**: Forms Mask Catalog (Tabelle)

| Masken-Name | Typ | Bounded Context | Nutzung (H/M/L) | Komplexität (1-5) | MVP-Priorität |
|-------------|-----|-----------------|-----------------|-------------------|---------------|

---

### Kategorie 3: Stored Procedures (~15min, 10 Fragen) ⚡ WICHTIG

**🔑 Kernfragen**:
- Organisation? (Packages, Naming Conventions?)
- **Live-Beispiel zeigen!** Typische Signatur?
- Input-Parameter? (NUMBER, VARCHAR2, RECORD, TABLE Types?)
- Output-Parameter? (RETURN, OUT, REF CURSOR?)
- Aufruf aus Forms? (PL/SQL-Block, Built-in?)
- Business-Logik? (% in DB vs. % in Forms?)
- Transaktions-Management? (COMMIT in Forms oder Procedures?)
- Dokumentation? (Kommentare, externe Doku?)
- Performance-Probleme?

**📋 Template**: Stored Procedure Service Catalog

| Package | Procedure | Funktion | Input | Output | Masken | Performance | REST-Kandidat? |
|---------|-----------|----------|-------|--------|--------|-------------|----------------|

---

### Kategorie 4: Daten & Integration (~8min, 5 Fragen)

**🔑 Kernfragen**:
- Kern-Entitäten? (Kunde, Vertrag, Schaden, ...)
- Beziehungen? (Foreign Keys, Triggers, Application-Level?)
- **Externe Systeme?** (GDV, SAP, COR Life, DMS)
- **Integrations-Mechanismen?** (DB Links, File Exchange, Web Services, MQ?)
- Batch-Prozesse?

**📋 Template**: Data Model Overview + Integration Map (Whiteboard-Skizze)

---

### Kategorie 5: Pain Points (~7min, 2 Fragen) ⚡ WICHTIG

**🔑 Kernfragen**:
- **Größte Probleme?** (Performance, Usability, Wartbarkeit, Deployment)
- **Was MUSS unverändert bleiben?** (Stored Procedures, DB-Schema, Integrationen, Workflows)

**📋 Template**: Pain Points & Constraints Canvas (2-Spalten)

---

## Part B: ICIS+ Deep Dive (30-40min)

### Kategorie 6: ICIS+ Architektur (~10min, 8 Fragen)

**🔑 Kernfragen**:
- Vaadin Version? (8, 14, 23, 24?)
- Java-Stack? (Spring Boot Version, Hibernate?)
- Application Server? (Tomcat?)
- Build-Prozess? (Maven, Frontend Plugin?)
- State-Management? (Vaadin Session, Spring Beans?)
- Auth? (Spring Security, LDAP?)
- **Deployment?** (VMs, Docker, Azure?)

**📋 Template**: ICIS+ Technology Stack Canvas

---

### Kategorie 7: Vaadin Components (~8min, 7 Fragen)

**🔑 Kernfragen**:
- Häufigste Vaadin-Komponenten?
- **Custom Components?** (Wiederverwendbar für neues Frontend?)
- Formular-Struktur? (Binder, Validatoren?)
- Navigation? (Vaadin Router?)
- Master-Detail Pattern?
- Responsive/Mobile? (Anforderung für neues Frontend?)
- **UI-Patterns übernehmen?**

**📋 Template**: Vaadin Component Inventory

| Component | Typ (Standard/Custom) | Verwendung | Wiederverwendbarkeit | Migrations-Strategie |
|-----------|----------------------|------------|---------------------|---------------------|

---

### Kategorie 8: Wrapper Services (~10min, 8 Fragen) ⚡ WICHTIG

**🔑 Kernfragen**:
- Was sind Wrapper Services? (Java Services → Stored Procedures?)
- **Wie rufen sie Procedures auf?** (JDBC, Spring JdbcTemplate, MyBatis?)
- **Live-Code-Beispiel zeigen!**
- **Typ-Mapping?** (Oracle Types → Java Types)
- Business-Logik in Wrappers? (Nur Mapping oder auch Validierung?)
- Transaktions-Management? (Spring @Transactional?)
- **Als REST API wiederverwendbar?** (Hoch/Mittel/Niedrig?)
- Testing? (Unit-Tests, Integration-Tests?)

**📋 Template**: Wrapper Service Catalog

| Service | Wrapped Procedure | Input (Java) | Output (Java) | Logik? | REST-ready? | Änderungen? |
|---------|-------------------|--------------|---------------|--------|-------------|-------------|

---

### Kategorie 9: Vergleich (~7min, 2 Fragen)

**🔑 Kernfragen**:
- **Selber Prozess in ICIS vs. ICIS+**: Unterschiede? (Procedures, Datenmodell, Business Rules)
- **Lessons Learned?** (Was lief gut? Was anders machen?)

---

## Part C: Vergleichende Analyse (20-30min)

### Aktivität 1: ICIS vs. ICIS+ Comparison Matrix (~15min)

**📋 Template**: 3-Spalten-Matrix

| Dimension | ICIS-Klassik | ICIS+ | Implikationen Neues Frontend |
|-----------|--------------|-------|------------------------------|
| Technology Stack | Forms + Oracle DB | Vaadin + Spring + Oracle DB | React/Angular + Spring Boot + Oracle DB |
| UI Patterns | Forms, keyboard | Web, Vaadin | Client-side, responsive, keyboard |
| Service Layer | Direct Procedures | Wrapper Services | **Wrapper → REST API!** |
| Data Mapping | Forms built-in | Java/Hibernate | **Java-Mapping wiederverwendbar!** |
| Transaction | Forms-gesteuert | Spring @Transactional | Spring @Transactional |
| User Base | Power User | Gemischt | Forms + Conversational UI |
| Deployment | Client-Server | Web App | Cloud-native (Azure, K8s) |
| Maintenance | Hoch (Legacy) | Mittel | REST entkoppelt → besser |

**Facilitator-Fragen**:
- "Was aus ICIS+ übernehmen?"
- "Was aus ICIS-Klassik bewahren?"

---

### Aktivität 2: Migration Strategy Canvas (~10-15min)

**📋 Template**: 3-Spalten-Canvas

| ✅ Keep (Unverändert) | 🔄 Reuse/Adapt (Wiederverwenden) | 🆕 Build New (Neu bauen) |
|----------------------|----------------------------------|-------------------------|
| ✅ Oracle Database | 🔄 Wrapper Services → REST API | 🆕 React/Angular Frontend |
| ✅ Stored Procedures | 🔄 Vaadin UI-Patterns → portieren | 🆕 Integration Layer (REST) |
| ✅ Business Rules (DB) | 🔄 Test-Daten & Szenarien | 🆕 AI Integration (MCP) |
| ✅ Externe Integrationen | 🔄 Auth-Mechanismus → JWT | 🆕 Moderne UX |
| ✅ Batch-Jobs | 🔄 Forms-Logik → Frontend portieren | 🆕 Cloud-Deployment |
| ✅ Compliance | | 🆕 Monitoring & Observability |

**Facilitator-Fragen**:
- "Welche Procedures schon in ICIS+ gewrappt?" → Einfach REST-ready!
- "Wrapper Services als REST API ohne Refactoring?"
- "Vaadin-Patterns für neues Frontend?"

---

## 🎯 Erwartete Outputs

Am Ende haben wir:

✅ Architecture Overview (ICIS-Klassik & ICIS+)  
✅ Forms Mask Catalog (20-50 Masken)  
✅ Stored Procedure Service Catalog (10-30 Procedures)  
✅ Wrapper Service Catalog (5-20 Services mit Wiederverwendbarkeits-Bewertung)  
✅ Vaadin Component Inventory (Custom Components)  
✅ Pain Points Catalog (5-15 priorisiert)  
✅ Constraints List (Technisch & Fachlich)  
✅ ICIS vs. ICIS+ Comparison Matrix  
✅ Migration Strategy Canvas (Keep/Reuse/Build-New)  

---

## ⏱️ Timing

**Option A: Vormittag (10:25-12:00 + 13:00-13:15)**
- 10:25-10:30: Intro (5min)
- 10:30-11:15: Part A (45min)
- 11:15-11:50: Part B (35min)
- 11:50-12:00: Part C Start (10min)
- 13:00-13:15: Part C Ende (15min)

**Option B: Nachmittag (13:00-14:30)**
- 13:00-13:05: Intro (5min)
- 13:05-13:45: Part A (40min)
- 13:45-14:15: Part B (30min)
- 14:15-14:30: Part C (15min)

---

## 💡 Facilitator-Tipps

### Rolle

- ✅ **WGV präsentiert** (sie sind die Experten)
- ✅ **Wir fragen strukturiert** (Fragenführung)
- ✅ **Wir dokumentieren** (Templates in Echtzeit ausfüllen)
- ❌ **Nicht**: WGV erklären, wie ihr System funktioniert

### Timeboxing

- ⏱️ **Timer sichtbar** machen
- 🎯 **Fokussierte Fragen**: "Zeigen Sie **ein** repräsentatives Beispiel"
- 🅿️ **Parking Lot**: Details für Tag 2 verschieben

### Live-Demos

- 📺 **Fordern Sie Live-Beispiele**: "Zeigen Sie uns eine Stored Procedure!"
- 📸 **Screenshots machen** von Code, Masken
- 🎥 **Screen-Recording** erwägen (falls erlaubt)

### Engagement

- 👥 **Alle einbinden**: Nutzer (Pain Points), Architekten (Architektur), Developer (Code)
- 🗣️ **Aktive Moderation**: "Was sagt der Fachbereich dazu?"

### Dokumentation

- 📝 **In Echtzeit**: Templates während Session ausfüllen
- 🖼️ **Visuell**: Whiteboard, Post-its, Diagramme
- ✅ **Review**: Am Ende kurz zusammenfassen

---

## 🚨 Häufige Challenges

| Challenge | Lösung |
|-----------|--------|
| Zu technisch für Nutzer | Balance: High-Level für Nutzer, Details mit Devs |
| WGV zeigt alles (3h statt 90min) | Timeboxing! "Nur repräsentatives Beispiel!" |
| Keine Dokumentation | Live-Code-Review, "Unknown" akzeptieren |
| Zu viele Procedure-Patterns | 3-5 typische Patterns identifizieren |

---

## 📚 Pre-Workshop Checkliste

- [ ] Miro/Whiteboard mit allen 9 Templates vorbereitet
- [ ] WGV-Präsentation koordiniert (Wer zeigt was?)
- [ ] Demo-Zugriffe getestet
- [ ] Architektur-Diagramme bereit (`architektur_schaubild_icis_gesamt.svg`)
- [ ] Beispiel-Code angefordert (Procedures, Wrapper Services)
- [ ] Rollen geklärt (Wer fragt? Wer dokumentiert?)

---

## 🔗 Integration mit Tag 1

**Input von Domain Mapping**:
- Bounded Contexts → Masken kategorisieren
- Context Map → Externe Integrationen verstehen

**Output für nachfolgende Aktivitäten**:
- **Maskenanalyse**: Forms Mask Catalog als Basis
- **UI/UX Konzept**: Vaadin-Patterns als Inspiration, Pain Points → UX-Verbesserungen
- **AI Features**: Stored Procedures → AI-Integration-Potenzial
- **Scope Discussion**: Kataloge → MVP-Kandidaten

---

**Quick Reference** | WGV ICIS Modernisierung | Tag 1 | Version 1.0
