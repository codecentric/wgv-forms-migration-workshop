# WGV Workshop Expectations - Interpretation

**Quelle-Dokument**: `angebot/Modernisierungsworkshop-Draft.pdf`  
**Typ**: WGV's detaillierte Erwartungen und Schwerpunkte für den Workshop

## Gesamtziel

Entwurf einer modernen Zielarchitektur, die auf der bestehenden Businessfunktionalität aufsetzt und primär die **Integrationsschicht und das Frontend** betrachtet. 

**Haupttreiber**: Ablöse der Oracle Forms-Masken

---

## Schwerpunkt 1: Status Quo & Zielbild-Schärfung

### Fokus
Auswahl und Betrachtung von Prozessen mit Modernisierungsbedarf, Verständnis bisherige Architekturkomponenten, Zusammenspiel Frontend – Backend und grobes Verständnis der bestehenden Schnittstellen.

### Themen

#### ICIS Deep Dive I: ICIS-Klassik
- Analyse bestehender Oracle-Formsmasken und Verwendung von Businessfunktionalität in Form von Schichtenservices
- Beispielhafte Analyse der bestehenden Schichtenservices in Form von Stored Procedures Services, ihrer Schnittstellen und Datenstrukturen

#### ICIS Deep Dive II: ICIS+
- Analyse bestehender ICIS+ Masken in Vaadin inkl. Java-Framework (Spring, Hibernate)
- Verwendung von Businessfunktionalität in Form von bereitgestellten Wrapper-Services (Schichtenservices für ICIS+ gewrappt)
- Beispielhafte Analyse der bestehenden Schichtenservices im Vergleich zur Verwendung in ICIS (Forms)

#### Änderungs- und Automatisierungspotenzial
- Betrachtung ausgewählter Masken mit Modernisierungsbedarf
- **Entscheidungskriterien definieren**:
  - Welche Masken oder Teile davon können durch Automatisierung ersetzt werden?
  - Welche Masken werden von Oracle Forms wegmigriert?
    - Komplett
    - Teile davon
    - Was kann entfallen

#### UX-Requirements & Power User-Definition
- Verständnis der Arbeitsweise der Sachbearbeiter in ICIS und ICIS+ (Schnelligkeit vs. Intuitivität, Expertensystem vs. Prozesssteuerung)
- **Ermittlung erster Veränderungspotentiale**:
  - Was benötigt eine Interaktion zur Bearbeitung ein Formular?
  - Was könnte über andere Formen wie z.B. Chatbot bearbeitet werden?
  - Wie kann die Interaktion zwischen Chatbot und Formular konkret aussehen?

#### Technische Anforderungen
- Technische Anforderungen erheben und konkretisieren:
  - **Containerisierung**
  - **Flexibilität der Integrationsschicht**
  - **MCP-Fähigkeit**
- Bewertung der unterschiedlichen Anforderungen in Bezug auf ICIS/ICIS+

### Ergebnis 1 (Erwartete Resultate)

✅ **Gemeinsames Verständnis** der Architekturen von ICIS und Unterschiede ICIS/ICIS+

✅ **Kenntnis der Erwartungen** aus der:
- Sachbearbeitung (Nutzer-Perspektive)
- Technik (Technische Anforderungen)

✅ **Beispielhafte Liste von Prozessen** mit Änderungspotential:
- Vorschläge zur Abbildung der Prozesse
- Vorschläge für mögliche Technologien

---

## Schwerpunkt 2: Integrationsschicht

### Fokus
Design einer flexiblen Integrationsschicht und KI-Integration

### Themen

#### Architektur der Integrationsschicht
- **Auswahl von Basistechnologien**: z.B. Java/Spring Boot oder Oracle REST Data Services
- **Definition der REST-API-Standards** und Versionierungskonzepte

#### KI-Integration: Model Context Protocol (MCP)
- **Deep Dive**: Wie können KI-Agenten, KI-Clients, LLMs standardisiert eingebunden werden?
- **Evaluierung von Frameworks**:
  - Spring AI innerhalb der Integrationsschicht **vs.** dedizierter MCP-Server
  - **Fokus: Wiederverwendbarkeit** - Der Mehrwert eines dedizierten MCP-Servers besteht primär in der Wiederverwendbarkeit der bereitgestellten Functions und Datentöpfe durch mehrere unabhängige KI-Agenten oder Abteilungen
- **Entscheidung**: Soll die Integrationsschicht selbst als MCP-Host fungieren oder REST-Endpunkte für einen externen Agenten bereitstellen?

#### Containerisierung
- **Deployment-Strategie**: z.B. Azure, Kubernetes
- **Skalierung** der Integrationsschicht vs. Datenbank-Bottlenecks

### Ergebnis Schwerpunkt 2 (Erwartete Resultate)

✅ **Erste Architekturvorschläge und -diagramm** der Integrationsschicht und ihres Deployments

✅ **Entscheidung** für Integrationsansatz und -technologie (z.B. Spring Boot mit Spring AI/MCP-Adapter)

---

## Schwerpunkt 3: Frontend-Technologie & KI-gestützter Entwicklungsprozess

### Fokus
Betrachtung und Berücksichtigung von KI im künftigen Entwicklungsprozess sowie Auswahl Technologie-Stack aufgrund der bisherigen Ergebnisse und Definition der "KI-Pipeline" zur Code-Erstellung.

### Themen

#### KI-Entwicklungsprozess
- **Wie nutzen wir GitHub Copilot oder Claude Code**, um Oracle Forms-Logik effizient in die Zieltechnologie zu portieren?
  - **Vergleich der KI-Tools**: Oft bessere IDE-Integration von GitHub Copilot vs. bessere Code-Generierung durch Claude Code
  - **Definition des Prompts/Kontexts**: Wie instrumentieren wir die KI mit den PL/SQL-Infos und Schnittstellendefinitionen der Stored Procedure Services, um Frontend-Code zu generieren?
- **Methode**: Live-Coding Spike (gemeinsame KI-gestützte Migration einer einfachen Maske in die präferierte Frontend-Technologie)

#### Framework Battle der ausgewählten Technologie-Stacks
- **Vergleich basierend auf WGV-Anforderungen**:
  - Langlebigkeit/Zukunftsfähigkeit
  - KI-Kompatibilität
  - Integration von Vaadin-Teilen
  - Eignung für Power User Features (Tastatursteuerung, Datendichte)

### Ergebnis Schwerpunkt 3 (Erwartete Resultate)

✅ **Entscheidung** für einen Technologie Stack

✅ **Erster validierter KI-Workflow** für die Migration

---

## Nachbereitung: Roadmap, Pilotierung & Lösungsentwurf

### Fokus
Zusammenführung der Ergebnisse in ein Dokument und Planung der nächsten Schritte.

### Themen

#### Erstellung Lösungsentwurf
- Zusammentragen der Entscheidungen aus den Workshops
- **Finalisierung des Zielbildes** (C4-Diagramm?)
- Beschreibung der Integrationsschicht (REST + MCP)

#### Definition Pilotprojekt
- **Auswahl eines konkreten fachlichen Kontextes** (z.B. "Schaden-Anlage") als Pilot
- **Vorgeschlagene Pilot-Inhalte**:
  - Neues Frontend, Design und Funktion
  - Backend-Call
  - Integrationsschicht
  - KI-Support (Chatbot-Integration)

#### Roadmap & Next Steps
- **Entwurf einer Roadmap**:
  - Umfang (Inhaltsverzeichnis)
  - Skizze einer Terminplanung
  - Aufwandschätzung

### Ergebnis Nachbereitung (Erwartete Resultate)

✅ **Architekturvorschlag** (finalisiertes Zielbild)

✅ **Scope für ein Pilotvorhaben** und Ausblick auf eine Roadmap (Inhaltsverzeichnis und Kerninhalte ggf. Termine und Kapazitäten)

✅ **Scope für Pilotprojekt** mit konkretem fachlichen Kontext

---

## Wichtige Beobachtungen

### 1. MCP als zentrales Thema
Model Context Protocol (MCP) hat einen dedizierten, detaillierten Fokus in Schwerpunkt 2. WGV erwartet eine fundierte Diskussion über:
- Standardisierte KI-Integration
- Wiederverwendbarkeit über mehrere KI-Agenten/Abteilungen hinweg
- Entscheidung: Integration Layer als MCP-Host vs. externe Agenten

### 2. AI-Tooling Vergleich
GitHub Copilot vs. Claude Code wird explizit genannt:
- Copilot: Bessere IDE-Integration
- Claude Code: Bessere Code-Generierung
- Erwartung: Praktischer Vergleich im Workshop

### 3. Live-Coding Spike
WGV erwartet eine **praktische Demonstration**: Gemeinsame KI-gestützte Migration einer einfachen Maske in die gewählte Technologie.

### 4. Wiederverwendbarkeit als Fokus
Bei MCP-Integration wird der Fokus auf **Wiederverwendbarkeit** gelegt - mehrere unabhängige KI-Agenten und Abteilungen sollen dieselben Functions/Datentöpfe nutzen können.

### 5. Konkrete Entscheidungen erwartet
WGV erwartet klare **Entscheidungen** als Output:
- Integration Layer Technologie
- Frontend Framework
- MCP-Ansatz
- Pilot-Scope

### 6. Detaillierter als unsere Agenda
Dieses PDF enthält **WGVs sehr detaillierte Erwartungen** mit spezifischen technischen Anforderungen, während unsere committete Agenda (20260303_commited_agend.md) auf höherem Level bleibt.

### 7. ICIS+ Analyse wichtig
WGV legt großen Wert auf die Analyse von **ICIS+ (Vaadin)** und den Vergleich mit ICIS Classic - dies zeigt, dass Wiederverwendung bestehender ICIS+ Komponenten relevant ist.

### 8. Power User Features explizit genannt
Tastatursteuerung und Datendichte werden als wichtige Anforderungen für das Frontend genannt - klassisches Merkmal von Versicherungs-Expertensystemen.

## Relevanz für Workshop-Vorbereitung

Diese Erwartungen sollten in unsere Workshop-Planung einfließen:

1. **Tag 1**: ICIS Deep Dive (Classic + Plus), UX-Anforderungen, Automatisierungspotenzial → passt zu Schwerpunkt 1
2. **Tag 2**: Integration Layer Design, **MCP Deep Dive**, Deployment → entspricht Schwerpunkt 2
3. **Tag 3**: Frontend-Framework Battle, **AI-Tooling (Copilot vs. Claude Code)**, Live-Coding Spike → entspricht Schwerpunkt 3

Die Rolle-Definitionen sollten diese spezifischen Erwartungen berücksichtigen, insbesondere:
- Solution Architect: MCP-Entscheidung, Wiederverwendbarkeit
- System Architect: Spring AI vs. dedizierter MCP-Server
- Staff Frontend/Backend Developer: Live-Coding Spike, AI-Workflow
