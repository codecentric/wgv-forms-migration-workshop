# Decision-Making Frameworks für IT-Transformation

**Zweck**: Referenz für Entscheidungsfindungs-Methoden im WGV Modernisierungsworkshop

Diese Frameworks helfen uns als Facilitators, strukturierte Diskussionen zu führen und fundierte Entscheidungen gemeinsam mit WGV zu treffen.

---

## 1. Weighted Decision Matrix (Gewichtete Entscheidungsmatrix)

### Anwendungsbereich
Technologie-Entscheidungen mit mehreren Kriterien:
- Spring Boot vs. Oracle ORDS (Integration Layer)
- React vs. Angular vs. andere (Frontend Framework)
- Deployment-Optionen (Azure App Service vs. AKS vs. Container Apps)

### Struktur

| Kriterium | Gewicht | Option A | Score A | Option B | Score B |
|-----------|---------|----------|---------|----------|---------|
| Langlebigkeit/Zukunftsfähigkeit | 25% | 8 | 2.0 | 6 | 1.5 |
| KI-Kompatibilität | 20% | 7 | 1.4 | 9 | 1.8 |
| Team Skills vorhanden | 15% | 6 | 0.9 | 8 | 1.2 |
| Vaadin-Integration möglich | 15% | 5 | 0.75 | 7 | 1.05 |
| Community Support | 10% | 9 | 0.9 | 7 | 0.7 |
| Vendor Lock-in vermeiden | 15% | 8 | 1.2 | 4 | 0.6 |
| **Total** | **100%** | | **7.15** | | **6.85** |

**Bewertung**: 1-10 Skala (1 = schlecht, 10 = exzellent)
**Score**: Bewertung × Gewicht

### Vorteile
✅ Objektiv und transparent  
✅ Forciert Diskussion über Kriterien und Gewichtung  
✅ Visuell verständlich  
✅ Dokumentiert Entscheidungsgrundlage

### Wann einsetzen
- Tag 2: Integration Layer Technologie-Entscheidung
- Tag 3: Frontend Framework Battle

### Vorbereitung für Miro
- Template mit Kriterien-Zeilen vorbereiten
- Gewichtungen gemeinsam festlegen (nicht vorgeben!)
- Live ausfüllen während der Diskussion

---

## 2. ADR (Architecture Decision Records)

### Anwendungsbereich
Dokumentation **aller** wichtigen Architektur-Entscheidungen während des Workshops

### Template

```markdown
# ADR-XXX: [Titel der Entscheidung]

**Datum**: YYYY-MM-DD  
**Status**: [Proposed | Accepted | Deprecated | Superseded]  
**Entscheider**: [Wer war beteiligt?]

## Context (Kontext)
Welches Problem/welche Frage führte zu dieser Entscheidung?
Welche Rahmenbedingungen gibt es?

## Decision (Entscheidung)
Was haben wir entschieden?

## Rationale (Begründung)
Warum haben wir uns dafür entschieden?
Welche Alternativen wurden betrachtet?

## Consequences (Konsequenzen)
Positive Konsequenzen:
+ Was wird dadurch besser?
+ Welche Vorteile entstehen?

Negative Konsequenzen:
- Welche Nachteile/Trade-offs gibt es?
- Was müssen wir in Kauf nehmen?

## Notes (Notizen)
Zusätzliche Anmerkungen, Links, Referenzen
```

### Beispiel

```markdown
# ADR-001: Spring Boot für Integration Layer

**Datum**: 2026-04-29  
**Status**: Accepted  
**Entscheider**: WGV Architects, codecentric Team

## Context
Benötigen Integration Layer zwischen Frontend und PL/SQL Stored Procedures.
Optionen: Spring Boot oder Oracle REST Data Services (ORDS).

## Decision
Wir nutzen Spring Boot mit Spring AI für die Integrationsschicht.

## Rationale
- Flexibilität für MCP-Integration (dedizierter MCP-Server möglich)
- Team hat bereits Spring Boot Expertise
- Besser testbar als ORDS
- Vendor lock-in vermeiden (cloud-agnostic)
- Spring AI Framework für KI-Integration verfügbar

Alternativen:
- Oracle ORDS: Schnellerer Start, aber weniger Flexibilität und Vendor lock-in

## Consequences
+ Volle Kontrolle über API-Design und -Implementierung
+ Cloud-agnostic (OpenTofu/Terragrunt einsetzbar)
+ Einfacher für Entwickler mit Java-Kenntnissen
+ Testbarkeit (Unit Tests, Integration Tests)

- Mehr Code zu schreiben als bei ORDS
- Wir müssen selbst warten/patchen
- Längere initiale Entwicklungszeit

## Notes
MCP-Integration wird in ADR-002 separat dokumentiert.
```

### Vorteile
✅ Leichtgewichtig und schnell  
✅ Dokumentiert **Warum**, nicht nur **Was**  
✅ Versionierbar (Git)  
✅ Nachvollziehbar auch Jahre später

### Wann einsetzen
- **Während des gesamten Workshops**: Nach jeder wichtigen Entscheidung
- Tag 2: Integration Layer Technologie
- Tag 2: MCP-Ansatz (dedizierter Server vs. Spring AI)
- Tag 3: Frontend Framework
- Tag 3: AI-Tooling (Copilot vs. Claude Code)

### Vorbereitung
- Template als Markdown-Datei vorbereiten
- Nummerierung-System festlegen (ADR-001, ADR-002, ...)
- **Direkt nach Entscheidung** ausfüllen (nicht später!)

---

## 3. RICE Scoring (Priorisierung)

### Anwendungsbereich
Priorisierung von Masken für die Migration (welche zuerst?)

### Formel

```
RICE Score = (Reach × Impact × Confidence) / Effort
```

**Komponenten**:
- **Reach** (Reichweite): Wie viele Nutzer sind betroffen? (Anzahl Nutzer pro Monat)
- **Impact** (Auswirkung): Business Value (1 = minimal, 2 = low, 3 = medium, 4 = high, 5 = massive)
- **Confidence** (Sicherheit): Wie sicher sind unsere Schätzungen? (0-100%, typisch 50%, 80%, 100%)
- **Effort** (Aufwand): Person-Monate (0.5, 1, 2, 4, ...)

### Beispiel

| Maske | Reach | Impact | Confidence | Effort | RICE Score |
|-------|-------|--------|------------|--------|------------|
| Vertragsabschluss | 50 | 5 | 80% | 3 | 66.7 |
| Adressänderung | 200 | 2 | 100% | 1 | 400 |
| Schadensanlage | 30 | 4 | 70% | 2 | 42 |
| Tarifberechnung | 80 | 3 | 50% | 4 | 30 |

**Priorisierung**: Adressänderung (400) > Vertragsabschluss (66.7) > Schadensanlage (42) > Tarifberechnung (30)

### Vorteile
✅ Quantifiziert Bauchgefühl  
✅ Zwingt zu realistischen Aufwandsschätzungen  
✅ Confidence-Faktor macht Unsicherheit explizit  
✅ Vergleichbar über verschiedene Masken hinweg

### Wann einsetzen
- Tag 1: Initial Scope Discussion (3-5 Masken für MVP identifizieren)

### Vorbereitung für Miro
- Tabelle mit Masken-Liste vorbereiten
- Gemeinsam schätzen (WGV kennt Reach/Impact besser, wir helfen bei Effort)

---

## 4. Technology Radar (ThoughtWorks-Stil)

### Anwendungsbereich
Strategische Technologie-Positionierung und Roadmap

### Struktur

**Vier Quadranten**:
1. **Languages & Frameworks**
2. **Tools**
3. **Platforms**
4. **Techniques**

**Vier Ringe** (von innen nach außen):
1. **Adopt** (Nutzen wir aktiv)
2. **Trial** (Ausprobieren, evaluieren)
3. **Assess** (Beobachten, analysieren)
4. **Hold** (Vermeiden, auslaufen lassen)

### Beispiel für WGV

**Adopt**:
- Languages & Frameworks: Spring Boot, React (nach Entscheidung)
- Tools: OpenTofu, Terragrunt, Docker
- Platforms: Azure Cloud, Kubernetes
- Techniques: REST APIs, CI/CD, Infrastructure as Code

**Trial**:
- Languages & Frameworks: Spring AI (für MCP)
- Tools: Claude Code (AI-gestützte Migration)
- Platforms: Azure Container Apps (vs. AKS)
- Techniques: MCP (Model Context Protocol), AI-driven Development

**Assess**:
- Languages & Frameworks: Oracle APEX (für CRUD Masken)
- Tools: GitHub Copilot (Alternative zu Claude Code)
- Platforms: -
- Techniques: Conversational UI Patterns

**Hold**:
- Languages & Frameworks: Oracle Forms (wird abgelöst)
- Tools: ARM Templates (Vendor lock-in, ersetzt durch OpenTofu)
- Platforms: On-Premise VMs (Migration zu Cloud)
- Techniques: Manuelle Deployments (ersetzt durch CI/CD)

### Vorteile
✅ Visuell und strategisch  
✅ Zeigt Entwicklungsrichtung  
✅ Team-Alignment über Technologie-Strategie  
✅ Kommuniziert Entscheidungen an Stakeholder

### Wann einsetzen
- Tag 2/3: Nach wichtigen Technologie-Entscheidungen
- Nachbereitung: Im Lösungsentwurf als strategische Übersicht

### Vorbereitung für Miro
- Radar-Template vorbereiten (Kreise + Quadranten)
- Post-its für Technologien
- Gemeinsam platzieren

---

## 5. Trade-off Sliders

### Anwendungsbereich
Explizit machen von impliziten Spannungen und Anforderungen

### Struktur

Slider zwischen zwei Polen (0-100%):

```
Speed ←─────────●─────→ Thoroughness
         (60%)

Innovation ←──●──────────→ Stability
        (20%)

Flexibility ←────────●───→ Simplicity
            (70%)

AI-driven ←──────●───────→ Manual Control
          (50%)
```

### Beispiel-Diskussionen

**UX Requirements**:
- **Schnelligkeit ↔ Intuitivität**: Wo steht WGV? (Power User bevorzugen Schnelligkeit)
- **Expertensystem ↔ Prozesssteuerung**: Freie Navigation vs. geführte Workflows?
- **Tastatursteuerung ↔ Maus/Touch**: Wie wichtig sind Shortcuts?

**AI-Integration**:
- **AI-gesteuert ↔ Manuelle Kontrolle**: Wie viel Autonomie für AI-Agents?
- **Chatbot ↔ Formular**: Welche Interaktion wo?

**Architektur**:
- **Flexibilität ↔ Einfachheit**: Microservices vs. Monolith?
- **Innovation ↔ Stabilität**: Neue Technologien vs. Bewährtes?

### Vorteile
✅ Macht implizite Trade-offs explizit  
✅ Verhindert "Wir wollen alles"-Diskussionen  
✅ Einfach zu verstehen und zu diskutieren  
✅ Zeigt Prioritäten klar auf

### Wann einsetzen
- Tag 1: UX Requirements & Power User Definition
- Tag 2: Architektur-Entscheidungen (Flexibilität vs. Einfachheit)

### Vorbereitung für Miro
- Slider-Templates vorbereiten
- Gemeinsam Positionen diskutieren und setzen
- Fotografieren/dokumentieren

---

## 6. Cynefin Framework (Komplexitäts-Einschätzung)

### Anwendungsbereich
Entscheidung: Welche Masken brauchen welchen Migrations-Ansatz?

### Fünf Domänen

```
┌──────────────┬──────────────┐
│  COMPLEX     │   CHAOTIC    │
│  (Emergent)  │   (Crisis)   │
│              │              │
│ Probe-Sense- │  Act-Sense-  │
│  Respond     │   Respond    │
├──────────────┼──────────────┤
│ COMPLICATED  │   CLEAR      │
│ (Knowable)   │  (Obvious)   │
│              │              │
│ Sense-Analyze│ Sense-       │
│  -Respond    │ Categorize-  │
│              │  Respond     │
└──────────────┴──────────────┘
       │  CONFUSED/DISORDER   │
       └─────────────────────┘
```

### Anwendung auf Masken

**Clear (Obvious/Simple)**:
- Einfache CRUD-Masken
- Klare Business Rules
- **Ansatz**: Oracle APEX (Low-Code)
- **Beispiel**: Einfache Adressänderung

**Complicated (Knowable)**:
- Komplexe, aber verstehbare Logik
- Experten können Lösung finden
- **Ansatz**: Standard-Migration (AI-gestützt)
- **Beispiel**: Vertragsabschluss mit vielen Feldern

**Complex (Emergent)**:
- Viele Abhängigkeiten, nicht vollständig planbar
- Muster entstehen erst bei Nutzung
- **Ansatz**: Iterativ, Experimente, Prototypen
- **Beispiel**: Hybride Chatbot+Form-Interaktion

**Chaotic (Crisis)**:
- Unklar, instabil, dringend
- **Ansatz**: Erstmal stabilisieren, dann kategorisieren
- **Beispiel**: Broken Masken, die sofort ersetzt werden müssen

**Confused/Disorder**:
- Wir wissen nicht, in welcher Domäne wir sind
- **Ansatz**: Informationen sammeln, dann einordnen

### Vorteile
✅ Verhindert "One-size-fits-all"-Denken  
✅ Hilft, richtigen Ansatz für jede Maske zu finden  
✅ Framework für Automatisierung vs. Migration Entscheidung

### Wann einsetzen
- Tag 1: Änderungs- und Automatisierungspotenzial
- Tag 1: Entscheidung welche Masken wie angehen

### Vorbereitung für Miro
- Cynefin-Diagramm vorbereiten
- Masken-Liste als Post-its
- Gemeinsam einordnen

---

## 7. Impact/Effort Matrix (2×2)

### Anwendungsbereich
Quick Wins Identifikation

### Struktur

```
        High Impact
            │
     ┌──────┼──────┐
     │      │      │
     │  ■   │  ●   │  ■ Strategic Projects
     │ Strat│Quick │  ● Quick Wins
     │      │ Wins │  ▲ Fill-ins
─────┼──────┼──────┼───── (Effort)
     │      │      │  ✖ Avoid / Time Wasters
     │  ▲   │  ✖   │
     │ Fill │Avoid │
     └──────┴──────┘
            │
        Low Impact
```

### Beispiel für Masken

**Quick Wins** (Low Effort, High Impact):
- Häufig genutzte, einfache Masken
- **Beispiel**: Partnersuche, einfache Adressänderung

**Strategic Projects** (High Effort, High Impact):
- Komplex aber wichtig
- **Beispiel**: Vertragsabschluss, Schadensbearbeitung

**Fill-ins** (Low Effort, Low Impact):
- Nice-to-have, wenn Zeit übrig
- **Beispiel**: Selten genutzte Reports

**Avoid** (High Effort, Low Impact):
- Nicht priorisieren
- **Beispiel**: Alte Masken, die kaum genutzt werden

### Vorteile
✅ Sehr einfach und intuitiv  
✅ Sofort verständlich  
✅ Schnelle Priorisierung möglich  
✅ Visuell klar

### Wann einsetzen
- Tag 1: Initial Scope Discussion
- Tag 1: Quick Wins identifizieren für MVP

### Vorbereitung für Miro
- 2×2 Matrix vorbereiten
- Masken als Post-its
- Gemeinsam platzieren

---

## 8. MoSCoW Prioritization

### Anwendungsbereich
Feature/Requirement Priorisierung, Scope-Management

### Kategorien

- **Must have**: Ohne diese Features geht es nicht (MVP-kritisch)
- **Should have**: Wichtig, aber nicht kritisch (kann in Phase 2)
- **Could have**: Nice-to-have, wenn Zeit/Budget vorhanden
- **Won't have (this time)**: Explizit ausgeschlossen für diesen Scope

### Beispiel für Frontend Features

**Must have**:
- Formular-basierte Dateneingabe
- Validierung (Client + Server)
- Tastaturnavigation (Power User)
- Integration mit Stored Procedures

**Should have**:
- Chatbot-Integration für einfache Fragen
- Responsive Design (Mobile)
- Keyboard Shortcuts

**Could have**:
- Advanced Chatbot Features
- Voice Input
- Offline-Fähigkeit

**Won't have (this time)**:
- Mobile App (native)
- Komplette AI-Automatisierung
- Migration aller 900 Masken in Phase 1

### Vorteile
✅ Zwingt zu harten Entscheidungen  
✅ Verhindert Scope Creep  
✅ Klar kommunizierbar  
✅ Einfach zu verstehen

### Wann einsetzen
- Tag 1: Scope Discussion
- Tag 2: Architektur-Features definieren
- Nachbereitung: Pilotprojekt-Scope definieren

### Vorbereitung für Miro
- Vier Spalten (Must, Should, Could, Won't)
- Features als Post-its
- Gemeinsam kategorisieren

---

## Workshop-Anwendungs-Matrix

### Tag 1: Discovery & Scoping

| Framework | Anwendung | Zeitaufwand |
|-----------|-----------|-------------|
| **Impact/Effort Matrix** | Quick Wins Identifikation | ~30min |
| **RICE Scoring** | Masken-Priorisierung | ~45min |
| **Cynefin Framework** | Komplexitäts-Einschätzung | ~30min |
| **Trade-off Sliders** | UX Requirements diskutieren | ~30min |
| **MoSCoW** | Scope festlegen | ~30min |

### Tag 2: Architecture & Integration

| Framework | Anwendung | Zeitaufwand |
|-----------|-----------|-------------|
| **Weighted Decision Matrix** | Spring Boot vs. ORDS | ~45min |
| **Weighted Decision Matrix** | MCP-Ansatz (Spring AI vs. dediziert) | ~45min |
| **ADR** | Entscheidungen dokumentieren | ~15min pro ADR |
| **Technology Radar** | Technologie-Positionierung | ~30min |

### Tag 3: Frontend & AI

| Framework | Anwendung | Zeitaufwand |
|-----------|-----------|-------------|
| **Weighted Decision Matrix** | Frontend Framework Battle | ~1h |
| **ADR** | Framework-Entscheidung dokumentieren | ~15min |
| **Trade-off Sliders** | AI vs. Manual Control | ~20min |

### Nachbereitung

| Framework | Anwendung | Zeitaufwand |
|-----------|-----------|-------------|
| **ADR Collection** | Alle Entscheidungen zusammenfassen | 2-3h |
| **Technology Radar** | Finales Strategie-Diagramm | 1h |
| **MoSCoW** | Pilotprojekt-Scope | 1h |

---

## Praktische Tipps für die Facilitation

### Vorbereitung

1. ✅ **Templates in Miro vorbereiten** (vor dem Workshop)
2. ✅ **Beispiele pre-füllen** um Methode zu erklären (dann löschen und neu machen)
3. ✅ **Kriterien-Listen vorbereiten** aber **nicht die Gewichtung** (gemeinsam festlegen!)

### Während des Workshops

4. ✅ **Scoring kollaborativ** in Echtzeit durchführen
5. ✅ **Diskussionen moderieren** bei unterschiedlichen Einschätzungen
6. ✅ **Fotografieren/Screenshot** von jedem Ergebnis sofort
7. ✅ **Direkt dokumentieren** (ADRs innerhalb 24h schreiben!)

### Nach dem Workshop

8. ✅ **ADRs finalisieren** innerhalb 1-2 Tagen
9. ✅ **Ergebnisse in Lösungsentwurf** einarbeiten
10. ✅ **Entscheidungen nachvollziehbar** dokumentieren (nicht nur "Was", sondern "Warum")

---

## Auswahlhilfe: Welches Framework wofür?

| Situation | Empfohlenes Framework |
|-----------|----------------------|
| Technologie-Wahl zwischen 2-3 Optionen | Weighted Decision Matrix |
| Viele Masken priorisieren | RICE Scoring oder Impact/Effort Matrix |
| Entscheidung dokumentieren | ADR |
| Strategische Tech-Übersicht | Technology Radar |
| Implizite Spannungen klären | Trade-off Sliders |
| Komplexität einschätzen | Cynefin Framework |
| Scope festlegen | MoSCoW |
| Quick Wins finden | Impact/Effort Matrix |

---

## Referenzen & Weiterführende Links

- **ADR**: https://adr.github.io/
- **Weighted Decision Matrix**: https://www.atlassian.com/team-playbook/plays/decision-matrix
- **RICE Scoring**: https://www.intercom.com/blog/rice-simple-prioritization-for-product-managers/
- **Technology Radar**: https://www.thoughtworks.com/radar
- **Cynefin Framework**: https://www.youtube.com/watch?v=N7oz366X0-8 (Dave Snowden)
- **MoSCoW**: https://www.agilebusiness.org/page/ProjectFramework_10_MoSCoWPrioritisation
