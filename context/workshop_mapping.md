# Workshop Mapping: Committete Agenda ↔ WGV Erwartungen

**Zweck**: Interne Analyse zur Vorbereitung von Workshop-Content (Miro Slides, Diskussionsgrundlagen)

**Quellen**:
- Committete Agenda: `20260303_commited_agend.md`
- WGV Erwartungen: `angebot/Modernisierungsworkshop-Draft.pdf`

---

## Workshop-Zeitstruktur (alle 3 Tage identisch)

**Gesamtzeit**: 09:00 - 17:00 (8 Stunden)

### Zeitaufteilung

**Vormittag** (09:00 - 12:00):
- **Arbeitszeit**: 2h 45min (165 Minuten)
- **Pause**: 15 Minuten (einzuplanen zwischen 10:00-11:00)
- **Netto-Arbeitszeit Vormittag**: 2h 45min

**Mittagspause** (12:00 - 13:00):
- **Dauer**: 1 Stunde

**Nachmittag** (13:00 - 17:00):
- **Arbeitszeit**: 3h 35min (215 Minuten)
- **Pausen**: 
  - 15 Minuten (erste Pause, ca. 14:30-14:45)
  - 10 Minuten (zweite Pause, ca. 15:30-15:40)
- **Netto-Arbeitszeit Nachmittag**: 3h 35min

### Gesamtrechnung pro Tag

| Zeitblock | Dauer |
|-----------|-------|
| Vormittag (inkl. 15min Pause) | 09:00 - 12:00 (3h) |
| Mittagspause | 12:00 - 13:00 (1h) |
| Nachmittag (inkl. 25min Pausen) | 13:00 - 17:00 (4h) |
| **Gesamt** | **8 Stunden** |
| **Netto-Arbeitszeit** | **~6h 20min** (380 Minuten) |

### Empfohlene Pausenzeiten

**Vormittag**:
- 10:10 - 10:25 (15min) nach ~70min Arbeit

**Nachmittag**:
- 14:30 - 14:45 (15min) nach ~90min Arbeit
- 15:30 - 15:40 (10min) nach weiteren ~45-60min Arbeit

**Rationale**: 
- Pausen nach 60-90min intensiver Arbeit (optimal für Konzentration)
- Längere Pause am Nachmittag nach ~1.5h (Post-Lunch-Tief berücksichtigen)
- Kurze Pause gegen 15:30 für finalen Sprint bis 17:00

---

## Tag 1: Discovery & Scoping

### Unsere Committete Agenda

- Domäne erkennen (Domänenkarte erstellen)
- Analyse von Masken (stichprobenartig)
- Anwendungskonzept (UI/UX) Skizze:
  - Analyse bestehender User Journeys (Power User Workflows)
  - Feature/Prioritätenliste
- Diskussion zum Thema AI Features
- Initial Scope Discussion

**Personenkreis**: Nutzer, Architekten, (PO/Projektleiter), (Developer)

### WGV's Schwerpunkt 1: Status Quo & Zielbild-Schärfung

#### Was bereits abgedeckt ist ✅

| WGV Erwartung | In Agenda | Anmerkung |
|---------------|-----------|-----------|
| Analyse bestehender Oracle-Formsmasken | ✅ "Analyse von Masken" | Vorhanden, aber weniger detailliert |
| UX-Requirements & Power User-Definition | ✅ "User Journeys (Power User)" | Vorhanden |
| Änderungs- und Automatisierungspotenzial | ✅ "AI Features" | Implizit in AI Features Diskussion |
| Initial Scope Discussion | ✅ "Initial Scope Discussion" | Explizit vorhanden |

#### Gaps & Fehlende Details ⚠️

| WGV Erwartung | Status | Gap-Beschreibung |
|---------------|--------|------------------|
| **ICIS Deep Dive I: ICIS-Klassik** | ⚠️ Nicht explizit | WGV erwartet **strukturierte Informationssammlung** zu Stored Procedure Services, Schnittstellen, Datenstrukturen. **Wir müssen Framework/Fragen bereitstellen**, WGV hat das Wissen. |
| **ICIS Deep Dive II: ICIS+** | ⚠️ Nicht explizit | Strukturierte Informationssammlung zu ICIS+ (Vaadin + Spring/Hibernate), Wrapper-Services, Vergleich ICIS vs. ICIS+. **Wir müssen Framework/Fragen bereitstellen**, WGV hat das Wissen. |
| **Entscheidungskriterien definieren** | ⚠️ Nicht explizit | WGV erwartet klare Kriterien: Welche Masken automatisieren? Komplett/teilweise migrieren? Was entfällt? |
| **Chatbot ↔ Formular Interaktion** | ⚠️ Oberflächlich | WGV will **konkrete** Interaktionskonzepte, nicht nur generelle AI Features |
| **Technische Anforderungen erheben** | ⚠️ Nicht explizit | Containerisierung, Flexibilität Integrationsschicht, **MCP-Fähigkeit** |

#### Erwartetes Ergebnis Tag 1

**WGV erwartet**:
- ✅ Gemeinsames Verständnis ICIS/ICIS+ Architekturen
- ✅ Kenntnis der Erwartungen (Sachbearbeitung + Technik)
- ✅ **Beispielhafte Liste von Prozessen** mit Änderungspotential + Technologievorschläge

**Unsere Agenda**: Implizit vorhanden, aber weniger konkret formuliert.

### Empfehlungen für Tag 1 Content 📋

#### Vorbereitung (codecentric)

**Wichtig**: WGV kennt ihre Systeme (ICIS, ICIS+) - **wir sind die Moderatoren/Facilitators**, nicht die Experten. Unser Job: Richtiges Framework, mentales Modell, strukturierte Fragen.

1. **ICIS Deep Dive Framework vorbereiten**:
   - **Fragenkatalog** für ICIS Classic:
     - Architektur-Überblick Fragen
     - Stored Procedures: Wie strukturiert? Wie aufgerufen?
     - Datenstrukturen: Input/Output Parameter?
     - Schnittstellen: Wie dokumentiert?
   - **Fragenkatalog** für ICIS+:
     - Vaadin Komponenten: Welche wiederverwendbar?
     - Spring/Hibernate: Wie konfiguriert?
     - Wrapper-Services: Wie wrappen sie Stored Procedures?
   - **Vergleichsmatrix-Template**: ICIS vs. ICIS+ (für WGV auszufüllen)
   - **Canvas/Framework** für strukturierte Informationssammlung

2. **Entscheidungskriterien-Framework**:
   - Miro Board: Kriterien für Automatisierung vs. Migration vs. Eliminierung
   - Matrix-Template: Komplexität, Business Value, Nutzungshäufigkeit
   - **Gemeinsam mit WGV ausfüllen** (nicht vorgeben!)

3. **Chatbot ↔ Form Interaktion Framework**:
   - Beispiel-Mockups (verschiedene Interaktionsmuster)
   - Diskussions-Framework: "Was per Formular? Was per Chat?"
   - Canvas für Interaktionskonzepte (WGV füllt aus)

4. **Technische Anforderungen Checkliste**:
   - Template zum Ausfüllen:
     - Containerisierung: Ja/Nein, Details?
     - Integrationsschicht Flexibilität: Anforderungen?
     - **MCP-Fähigkeit**: Wichtig für WGV!
   - **WGV füllt aus, wir moderieren**

#### Während des Workshops

- **ICIS Deep Dive Session** (~1.5-2h) - **Moderiert, WGV präsentiert**
  - WGV demonstriert Forms-Masken
  - WGV demonstriert ICIS+
  - WGV zeigt Stored Procedures Beispiele
  - **Wir fragen, strukturieren, dokumentieren**
  
- **Entscheidungskriterien Workshop** (~1h) - **Gemeinsam entwickeln**
  - Kriterien gemeinsam definieren
  - Auf 3-5 Beispiel-Masken anwenden
  - **WGV liefert Content, wir moderieren**

- **UX Konzept Session** (~1h) - **Moderiert**
  - Power User Definition (WGV beschreibt, wir strukturieren)
  - Chatbot ↔ Form Interaktionskonzepte skizzieren (WGV Input)

---

## Tag 2: Technical Validation & Architecture

### Unsere Committete Agenda

- Recap Tag 1 & Verschärfung des Scopes
- Vorstellung bestehender Services / Stored Procedures
- Technische Machbarkeitsanalyse (Quick Wins)
- Abhängigkeiten und Risiken
- Integration von AI (MCP / RBAC / Hosting)
- Diskussion Integrationsschicht (Spring Boot vs. Oracle ORDS)
- Diskussion Deployment (VMs, Docker, Kubernetes)
- Entwurf Architekturdiagramm

**Personenkreis**: Architekten, Developer, (Nutzer optional)

### WGV's Schwerpunkt 2: Integrationsschicht

#### Was bereits abgedeckt ist ✅

| WGV Erwartung | In Agenda | Anmerkung |
|---------------|-----------|-----------|
| Auswahl Basistechnologien (Spring Boot vs. ORDS) | ✅ Explizit vorhanden | Genau so formuliert |
| Containerisierung & Deployment | ✅ "Deployment (VMs, Docker, K8s)" | Vorhanden |
| AI Integration (MCP, RBAC, Hosting) | ✅ Explizit vorhanden | Vorhanden |

#### Gaps & Fehlende Details ⚠️

| WGV Erwartung | Status | Gap-Beschreibung |
|---------------|--------|------------------|
| **Definition REST-API-Standards** | ⚠️ Nicht explizit | WGV erwartet konkrete Standards und **Versionierungskonzepte** |
| **MCP Deep Dive** | ⚠️ Oberflächlich | WGV erwartet **dedizierte Deep-Dive Session** zu MCP |
| **Spring AI vs. dedizierter MCP-Server** | ❌ Fehlt | Zentrale Entscheidung: Integration Layer als MCP-Host oder externe Agenten? **Fokus: Wiederverwendbarkeit** |
| **Skalierung vs. DB-Bottlenecks** | ⚠️ Nicht explizit | WGV will Diskussion: Skalierung Integrationsschicht vs. Oracle DB Limits |

#### Erwartetes Ergebnis Tag 2

**WGV erwartet**:
- ✅ Architekturvorschlag + **Diagramm** der Integrationsschicht
- ✅ **Entscheidung** für Integrationsansatz/-technologie (z.B. Spring Boot + Spring AI/MCP-Adapter)

**Unsere Agenda**: "Entwurf Architekturdiagramm" vorhanden, aber Entscheidung nicht explizit gefordert.

### Empfehlungen für Tag 2 Content 📋

#### Vorbereitung (codecentric)

1. **MCP Deep Dive Session vorbereiten** (~1-1.5h):
   - Was ist MCP? (falls nicht bekannt)
   - Spring AI Integration vs. dedizierter MCP-Server
   - **Wiederverwendbarkeit**: Mehrere AI-Agenten/Abteilungen
   - Entscheidungsmatrix vorbereiten

2. **REST API Standards Template**:
   - OpenAPI/Swagger Beispiele
   - Versionierungsstrategien (URL-based, Header-based)
   - Breaking Changes Policy

3. **Architektur-Diagramm Vorlagen**:
   - C4 Model Templates
   - Integrationsschicht-Optionen visualisieren
   - Spring Boot + Spring AI vs. Spring Boot + dedizierter MCP-Server

4. **Skalierungs-Diskussion vorbereiten**:
   - Oracle DB Connection Pooling
   - Horizontal Scaling (Stateless APIs)
   - Bottleneck-Szenarien

#### Während des Workshops

- **MCP Deep Dive** als eigener Block (~1-1.5h)
  - Technische Optionen erklären
  - Wiederverwendbarkeit diskutieren
  - **Entscheidung herbeiführen**: Integration Layer als MCP-Host?

- **REST API Design Session** (~45min-1h)
  - Standards definieren
  - Versionierung festlegen

- **Architektur-Diagramm gemeinsam erstellen** (~1-1.5h)
  - Whiteboard/Miro
  - Konsens erreichen
  - **Entscheidungen dokumentieren**

---

## Tag 3: Frontend & AI-Driven Development

### Unsere Committete Agenda

- Einordnung von Frontend Frameworks
- AI-Driven Development Workshop (Großteil des Tages):
  - Basics
  - Anwendung am Oracle Masken Beispiel

**Personenkreis**: Developer, Architekten (für Frontend Teil + wenn AI-Driven Development interessant)

### WGV's Schwerpunkt 3: Frontend-Technologie & KI-gestützter Entwicklungsprozess

#### Was bereits abgedeckt ist ✅

| WGV Erwartung | In Agenda | Anmerkung |
|---------------|-----------|-----------|
| Einordnung Frontend Frameworks | ✅ Explizit vorhanden | Genau so formuliert |
| AI-Driven Development | ✅ "AI-Driven Development Workshop" | Vorhanden |
| Anwendung am Oracle Masken Beispiel | ✅ Explizit vorhanden | Vorhanden |

#### Gaps & Fehlende Details ⚠️

| WGV Erwartung | Status | Gap-Beschreibung |
|---------------|--------|------------------|
| **GitHub Copilot vs. Claude Code Vergleich** | ❌ Fehlt | WGV erwartet **expliziten Vergleich**: IDE-Integration vs. Code-Generierung |
| **Prompt/Kontext-Definition** | ⚠️ Nicht explizit | Wie instrumentieren wir KI mit PL/SQL + Stored Procedure Interfaces? |
| **Live-Coding Spike** | ⚠️ Implizit | WGV erwartet **gemeinsame** KI-gestützte Migration einer einfachen Maske (hands-on!) |
| **Framework Battle** | ⚠️ Oberflächlich | WGV erwartet Vergleich basierend auf **spezifischen Anforderungen**: Langlebigkeit, KI-Kompatibilität, Vaadin-Integration, Power User Features |

#### Erwartetes Ergebnis Tag 3

**WGV erwartet**:
- ✅ **Entscheidung** für einen Technologie Stack
- ✅ **Erster validierter KI-Workflow** für die Migration

**Unsere Agenda**: Nicht explizit als Ergebnis formuliert.

### Empfehlungen für Tag 3 Content 📋

#### Vorbereitung (codecentric)

1. **AI-Tooling Vergleich vorbereiten**:
   - GitHub Copilot Demo/Setup
   - Claude Code Demo/Setup
   - Vergleichsmatrix: IDE-Integration, Code-Qualität, Kontext-Verständnis

2. **Live-Coding Spike vorbereiten** (~1.5-2h):
   - Einfache Oracle Forms Maske auswählen (mit WGV abstimmen)
   - Stored Procedure Interface dokumentieren
   - Beide Tools (Copilot + Claude Code) testen
   - **Gemeinsam** mit WGV Developers live migrieren

3. **Framework Battle Matrix**:
   - React vs. Angular (vs. andere?)
   - Bewertungskriterien:
     - Langlebigkeit/Zukunftsfähigkeit
     - KI-Kompatibilität (LLM Training Data)
     - Vaadin-Integration möglich?
     - Power User Features (Tastatursteuerung, Datendichte)
   - Scoring-System

4. **KI-Workflow definieren**:
   - Template: Wie gehen wir vor?
   - Prompt-Engineering: PL/SQL Infos + Stored Procedure Interfaces → Frontend Code
   - Best Practices dokumentieren

#### Während des Workshops

- **AI-Tooling Vergleich Session** (~1h)
  - GitHub Copilot Demo
  - Claude Code Demo
  - Diskussion: Was passt besser für WGV?

- **Live-Coding Spike** (~1.5-2h) **[Highlight!]**
  - Gemeinsam eine Maske migrieren
  - Hands-on mit KI-Tools
  - Learnings dokumentieren

- **Framework Battle** (~1-1.5h)
  - Kriterien durchgehen
  - Gemeinsam bewerten
  - **Entscheidung treffen**

- **KI-Workflow Workshop** (~1h)
  - Workflow dokumentieren
  - Best Practices festhalten
  - **Validierung**: Ist dieser Workflow für 900 Masken skalierbar?

---

## Nachbereitung (Post-Workshop)

### Unsere Committete Agenda

**Nicht explizit in der Agenda enthalten** - aber **im Angebot enthalten und von WGV akzeptiert**.

**Unser Scope umfasst**:
1. Workshop-Vorbereitung
2. Workshop-Durchführung (3 Tage)
3. **Nachbereitung der Workshop-Erkenntnisse und Entscheidungen**

### WGV's Nachbereitung: Roadmap, Pilotierung & Lösungsentwurf

#### Was WGV explizit erwartet

| WGV Erwartung | Status | Anmerkung |
|---------------|--------|-----------|
| **Erstellung Lösungsentwurf** | ✅ In Scope | Zusammentragen der Entscheidungen, Finalisierung Zielbild (C4-Diagramm?), Beschreibung Integrationsschicht |
| **Definition Pilotprojekt** | ✅ In Scope | Auswahl fachlicher Kontext (z.B. "Schaden-Anlage"), Pilot-Inhalte: Frontend, Backend-Call, Integration Layer, Chatbot |
| **Roadmap & Next Steps** | ✅ In Scope | Umfang, Terminplanung, Aufwandschätzung |

#### Erwartetes Ergebnis Nachbereitung

**WGV erwartet**:
- ✅ **Architekturvorschlag** (finalisiert)
- ✅ **Scope für Pilotvorhaben** mit konkretem fachlichen Kontext
- ✅ **Roadmap** (Inhaltsverzeichnis, Termine, Kapazitäten)

**Status**: ✅ **Alles im Scope**, muss geplant und durchgeführt werden.

### Empfehlungen für Nachbereitung 📋

#### Nach dem Workshop (codecentric - Teil unseres Angebots)

**Timeline**: 1-2 Wochen nach Workshop

1. **Lösungsentwurf erstellen**:
   - Alle Entscheidungen aus dem Workshop zusammenfassen
   - C4-Diagramm finalisieren
   - Integrationsschicht dokumentieren (REST + MCP)
   - Technology Stack dokumentieren
   - Architektur-Decisions Records (ADRs) schreiben

2. **Pilotprojekt definieren** (basierend auf Workshop-Erkenntnissen):
   - Fachlichen Kontext festlegen (gemeinsam im Workshop identifiziert)
   - Pilot-Scope detaillieren:
     - Neues Frontend (Design + Funktion)
     - Backend-Call zu Stored Procedures
     - Integrationsschicht implementieren
     - KI-Support (Chatbot-Integration)
   - Aufwand schätzen
   - Timeline vorschlagen
   - Ressourcen-Bedarf klären

3. **Roadmap erstellen**:
   - Inhaltsverzeichnis: Was wird dokumentiert?
   - Phasen definieren (MVP, Phase 2, Phase 3, ...)
   - Terminplanung (grob)
   - Kapazitäten/Aufwandschätzung
   - Risiken & Abhängigkeiten

4. **Dokumentation finalisieren**:
   - Workshop-Protokoll
   - Entscheidungsdokumentation
   - Technologie-Bewertungen
   - Nächste Schritte

#### Deliverables Nachbereitung

- 📄 **Lösungsentwurf-Dokument** (PDF/Markdown)
- 📊 **Architektur-Diagramme** (C4 Model)
- 📋 **Pilotprojekt-Scope** (detailliert)
- 🗺️ **Roadmap** (Phasen, Timeline, Aufwand)
- 📝 **ADRs** (Architecture Decision Records)

---

## Zusammenfassung: Gaps & Prioritäten

### Kritische Gaps (High Priority) 🔴

1. **ICIS/ICIS+ Deep Dive Framework fehlt** (Tag 1)
   - WGV hat das Wissen über ICIS (Forms) und ICIS+ (Vaadin)
   - **Wir brauchen**: Strukturiertes Framework/Fragenkatalog zur Informationssammlung
   - Wiederverwendung von ICIS+ Komponenten ist relevant
   - **Rolle**: Wir moderieren, WGV präsentiert

2. **MCP Deep Dive zu oberflächlich** (Tag 2)
   - WGV erwartet dedizierte Session
   - Zentrale Entscheidung: Spring AI vs. dedizierter MCP-Server
   - Fokus auf **Wiederverwendbarkeit** über mehrere AI-Agenten
   - **Rolle**: Wir präsentieren Optionen, gemeinsam entscheiden

3. **Live-Coding Spike nicht explizit** (Tag 3)
   - WGV erwartet **gemeinsame, hands-on** Migration einer Maske
   - Nicht nur Demo, sondern gemeinsames Coding
   - **Rolle**: Wir moderieren/führen, WGV lernt mit

### Moderate Gaps (Medium Priority) 🟡

4. **Entscheidungskriterien nicht explizit** (Tag 1)
   - WGV will klare Kriterien für Automatisierung vs. Migration
   - **Rolle**: Wir liefern Framework, gemeinsam definieren

5. **Nachbereitung muss geplant werden** (Post-Workshop)
   - ✅ **Im Scope enthalten** (Workshop-Vorbereitung, Durchführung, Nachbereitung)
   - Muss zeitlich eingeplant werden (1-2 Wochen nach Workshop)
   - Deliverables: Lösungsentwurf, Pilot-Definition, Roadmap

6. **REST API Standards fehlen** (Tag 2)
   - Versionierungskonzepte
   - Breaking Changes Policy

7. **GitHub Copilot vs. Claude Code Vergleich** (Tag 3)
   - Expliziter Vergleich erwartet
   - Hands-on mit beiden Tools

### Kleinere Gaps (Low Priority) 🟢

8. **Chatbot ↔ Form Interaktion** (Tag 1)
   - Konkrete Interaktionskonzepte, nicht nur generell

9. **Framework Battle Details** (Tag 3)
   - Bewertung gegen spezifische WGV-Anforderungen

10. **Skalierung vs. DB-Bottlenecks** (Tag 2)
    - Diskussion über Oracle DB Limits

---

## Nächste Schritte

### Vor dem Workshop

1. ✅ **Mit WGV klären/abstimmen**:
   - Welche ICIS+ Komponenten sollen betrachtet werden?
   - Welche Beispiel-Maske für Live-Coding Spike?
   - Wer von WGV präsentiert ICIS/ICIS+ Deep Dive?

2. ✅ **Facilitation-Content vorbereiten** (basierend auf Gaps):
   - **ICIS/ICIS+ Informationssammlungs-Framework**:
     - Fragenkataloge (ICIS Classic, ICIS+)
     - Canvas/Templates zum Ausfüllen
     - Vergleichsmatrix-Vorlage
   - **MCP Deep Dive Präsentation**:
     - Optionen erklären (Spring AI vs. dedizierter Server)
     - Entscheidungsmatrix
   - **Live-Coding Spike Setup**:
     - Copilot + Claude Code vorbereitet
     - Beispiel-Maske Dokumentation
   - **Entscheidungskriterien Framework**:
     - Templates für gemeinsame Definition
   - **Framework Battle Matrix**:
     - Bewertungsframework

3. ✅ **Workshop-Agenda detaillieren** (intern):
   - Detaillierte Tagesagenda mit Zeitslots
   - Explizite Entscheidungspunkte markieren
   - Output-Erwartungen pro Session
   - Rollen klären (Wer moderiert? Wer präsentiert?)

4. ✅ **Nachbereitung planen**:
   - Timeline festlegen (1-2 Wochen nach Workshop)
   - Deliverables definieren
   - Ressourcen allokieren

### Während des Workshops

- **Entscheidungen dokumentieren** (in Echtzeit)
- **Ergebnisse festhalten** (für Lösungsentwurf)
- **Pilot-Kontext identifizieren** (mit WGV gemeinsam)

### Nach dem Workshop

- **Lösungsentwurf erstellen** (1-2 Wochen)
- **Pilotprojekt definieren** (Abstimmung mit WGV)
- **Roadmap skizzieren**

---

## Content-Erstellung Checkliste (für Miro Slides)

### Tag 1: Discovery & Scoping

- [ ] **ICIS/ICIS+ Informationssammlungs-Framework**
  - [ ] **Fragenkatalog ICIS Classic** (Forms + Stored Procedures)
    - [ ] Architektur-Überblick Fragen
    - [ ] Stored Procedures: Struktur, Aufruf, Parameter
    - [ ] Schnittstellen-Dokumentation
  - [ ] **Fragenkatalog ICIS+** (Vaadin + Wrapper-Services)
    - [ ] Vaadin Komponenten: Wiederverwendbarkeit?
    - [ ] Spring/Hibernate Konfiguration
    - [ ] Wrapper-Services: Wie funktioniert das Wrapping?
  - [ ] **Vergleichsmatrix-Vorlage** (ICIS vs. ICIS+)
  - [ ] **Canvas für strukturierte Dokumentation** (WGV füllt aus)

- [ ] **Entscheidungskriterien Framework**
  - [ ] Template: Automatisierung vs. Migration vs. Eliminierung
  - [ ] Bewertungsmatrix (Komplexität, Business Value, Nutzung)
  - [ ] **Gemeinsam mit WGV ausfüllen** (nicht vorgeben!)

- [ ] **UX Konzept Session Framework**
  - [ ] Power User Definition Canvas (WGV füllt aus)
  - [ ] Chatbot ↔ Form Interaktionsmuster (Mockups als Beispiele)
  - [ ] Diskussionsleitfaden (strukturierte Fragen)

- [ ] **Technische Anforderungen Erhebungs-Framework**
  - [ ] Template zum Ausfüllen (Containerisierung, Integration Layer, MCP)
  - [ ] Diskussionsleitfaden
  - [ ] **WGV füllt aus, wir moderieren**

### Tag 2: Integrationsschicht & Architektur

- [ ] **MCP Deep Dive Präsentation**
  - [ ] Was ist MCP?
  - [ ] Spring AI vs. dedizierter MCP-Server
  - [ ] Wiederverwendbarkeit-Fokus
  - [ ] Entscheidungsmatrix

- [ ] **REST API Standards**
  - [ ] OpenAPI/Swagger Templates
  - [ ] Versionierungsstrategien
  - [ ] Breaking Changes Policy

- [ ] **Architektur-Diagramm Templates**
  - [ ] C4 Model Vorlage
  - [ ] Integration Layer Optionen

- [ ] **Skalierungs-Diskussion**
  - [ ] Connection Pooling
  - [ ] Horizontal Scaling
  - [ ] Bottleneck-Szenarien

### Tag 3: Frontend & AI-Driven Development

- [ ] **AI-Tooling Vergleich**
  - [ ] GitHub Copilot Demo/Setup
  - [ ] Claude Code Demo/Setup
  - [ ] Vergleichsmatrix

- [ ] **Live-Coding Spike Vorbereitung**
  - [ ] Beispiel-Maske dokumentieren
  - [ ] Stored Procedure Interface
  - [ ] Setup für beide Tools

- [ ] **Framework Battle Matrix**
  - [ ] Bewertungskriterien
  - [ ] Scoring-System
  - [ ] Entscheidungsvorlage

- [ ] **KI-Workflow Template**
  - [ ] Prompt-Engineering Guidelines
  - [ ] Best Practices
  - [ ] Workflow-Diagramm
