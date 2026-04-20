# Tag 2 - Architekturdiagramm Foundation/Skeleton

**Zweck:** Vorgefertigtes Grundgerüst für Miro Frame 12 (Activity 7), das während des Workshops kollaborativ detailliert wird.

**Timing:** 1 Stunde (innerhalb Activity 7)

**Facilitator:** System Architect (Lead) + Solution Architect

---

## Kontext

Dieses Dokument beschreibt die **Foundation/Skeleton** für das Architekturdiagramm, das in Miro Frame 12 vorbereitet werden soll. Es ist bewusst **nicht vollständig**, sondern bietet ein strukturiertes Grundgerüst, das WGV-Teilnehmer und codecentric gemeinsam während der Workshop-Session ausarbeiten.

**Wichtig:** Das Diagramm wird die **Zielarchitektur** (nach Modernisierung) zeigen, nicht den aktuellen ICIS-Stand.

---

## Vorbereitete Ebenen (4-Layer-Architektur)

### Layer 1: Frontend / Client Layer
**Position:** Oben im Diagramm

**Vorgefertigte Komponenten (Miro Shapes):**
```
┌─────────────────────────────────────────────────────────┐
│  Frontend Layer (Modernisiert)                          │
│                                                           │
│  [Web Browser]                                           │
│     │                                                    │
│     ├─ [React/Angular App] ← Technologie TBD im Workshop│
│     │    └─ Hybrid UI:                                  │
│     │       • Conversational Interface (AI Agent)       │
│     │       • Form-based Interface (Power Users)        │
│     │                                                    │
│     └─ [Vaadin Components] ← Wiederverwendung aus ICIS+ │
│                                                           │
└─────────────────────────────────────────────────────────┘
```

**Offene Fragen für Workshop-Diskussion:**
- Welche Frontend-Technologie? (Activity aus Tag 3 Vorschau)
- Welche Vaadin-Komponenten können wiederverwendet werden?
- Wie wird das Conversational UI integriert? (MCP Client?)

**Miro-Anweisungen:**
- Rechteck mit Titel "Frontend Layer"
- 3 Unter-Komponenten als abgerundete Rechtecke
- Gestrichelte Linie zu "Vaadin Components" mit Annotation "Wiederverwendung ICIS+"
- Leere Sticky Notes für Teilnehmer-Inputs

---

### Layer 2: Integration Layer / API Gateway
**Position:** Mitte-Oben

**Vorgefertigte Komponenten:**
```
┌─────────────────────────────────────────────────────────┐
│  Integration Layer (Neu zu entwickeln)                  │
│                                                           │
│  [API Gateway / Load Balancer]                          │
│     │                                                    │
│     ├─ [REST API Services]                              │
│     │    └─ Technologie: Spring Boot / ORDS / Hybrid   │
│     │       (Entscheidung aus Activity 4)               │
│     │                                                    │
│     ├─ [AI Integration Gateway]                         │
│     │    └─ Pattern: MCP / Spring AI / Direct          │
│     │       (Entscheidung aus Activity 6)               │
│     │                                                    │
│     └─ [Authentication & Authorization]                 │
│          └─ RBAC, Session Management                    │
│                                                           │
└─────────────────────────────────────────────────────────┘
```

**Offene Fragen für Workshop-Diskussion:**
- Welche Service-Stored-Procedures werden exponiert? (aus Activity 2 Katalog)
- Wie werden BSP/DSP/GSP/TSP gemappt? (1:1 oder Aggregation?)
- Welche API-Versionierungsstrategie?
- Wie wird AI-Traffic von Standard-Traffic getrennt?

**Miro-Anweisungen:**
- Rechteck mit Titel "Integration Layer"
- 4 Unter-Komponenten (API Gateway, REST Services, AI Gateway, Auth)
- **Platzhalter-Boxen** für Decisions aus Activity 4 & 6:
  - "Spring Boot / ORDS / Hybrid" als 3 Radio-Button-Optionen (visuell markierbar)
  - "MCP / Spring AI / Direct / Hybrid" als 4 Radio-Button-Optionen
- Verbindungspfeile nach unten zu Layer 3

---

### Layer 3: Backend / Database Layer
**Position:** Mitte-Unten

**Vorgefertigte Komponenten:**
```
┌─────────────────────────────────────────────────────────┐
│  Backend Layer (Unverändert - Preservation)             │
│                                                           │
│  [Oracle Database 19c]                                  │
│     │                                                    │
│     ├─ [PL/SQL Service Stored Procedures]               │
│     │    ├─ BSP (Berichts-SP)                           │
│     │    ├─ DSP (Daten-SP)                              │
│     │    ├─ GSP (Geschäftslogik-SP)                     │
│     │    └─ TSP (Transaktions-SP)                       │
│     │                                                    │
│     ├─ [Datenbank-Tabellen]                             │
│     │    └─ ICIS-Schema (bestehend)                     │
│     │                                                    │
│     └─ [Database Triggers & Constraints]                │
│                                                           │
└─────────────────────────────────────────────────────────┘
```

**Annotation (prominent platziert):**
```
⚠️ **Wichtig:** Dieser Layer bleibt UNVERÄNDERT
   - Keine PL/SQL-Migration
   - Keine Schema-Änderungen
   - Bewährte Geschäftslogik wird bewahrt
```

**Offene Fragen für Workshop-Diskussion:**
- Welche Service-SPs sind am wichtigsten? (Priorisierung aus Activity 2)
- Gibt es Performance-Bottlenecks bei bestimmten SPs?
- Brauchen wir Database Connection Pooling? (aus Deployment-Diskussion Activity 5)

**Miro-Anweisungen:**
- Rechteck mit Titel "Backend Layer (Unverändert)"
- Grüne Farbe oder Häkchen-Symbol für "Preservation"
- 4 SP-Typen als Badges/Labels (nicht editierbar, nur Referenz)
- Sticky Notes für Teilnehmer-Kommentare zu SP-Performance

---

### Layer 4: External Systems / Integrations
**Position:** Rechts (vertikal angeordnet)

**Vorgefertigte Komponenten:**
```
┌──────────────────────────────────┐
│  Externe Systeme (Bestand)      │
│                                  │
│  [SAP]                           │
│  [COR Life]                      │
│  [GDV (Gesamtverband)]          │
│  [DMS (Dokumentenmanagement)]   │
│  [ICIS+ (Koexistenz)]           │
│  [Oracle Forms (Koexistenz)]    │
│                                  │
│  Neue AI-Systeme (TBD):         │
│  [LLM Provider]                  │
│     └─ Claude / GPT / ...       │
│                                  │
└──────────────────────────────────┘
```

**Offene Fragen für Workshop-Diskussion:**
- Wie wird die Koexistenz mit Oracle Forms gemanagt? (Strangler Fig)
- Welche Schnittstellen zu SAP/COR Life müssen neu gemappt werden?
- Welcher LLM-Provider? (Cloud vs. On-Premise?)
- Wie werden externe API-Calls getrackt? (Monitoring)

**Miro-Anweisungen:**
- Rechteck mit Titel "Externe Systeme"
- 6 bestehende Systeme als farbige Badges (Blau für "Bestand", Grau für "Koexistenz")
- 1 neues AI-System als gestricheltes Rechteck (Orange für "Neu")
- Verbindungspfeile von Layer 2 (Integration Layer) zu jedem System

---

## Deployment & Infrastructure Annotation

**Position:** Unten oder als Overlay

**Vorgefertigte Komponenten:**
```
┌─────────────────────────────────────────────────────────┐
│  Deployment Environment (Entscheidung aus Activity 5)   │
│                                                           │
│  [Infrastructure]                                        │
│     └─ VMs / Docker / Kubernetes / Azure Container Apps │
│                                                           │
│  [Monitoring & Observability]                            │
│     └─ Logs, Metrics, Traces (TBD)                      │
│                                                           │
└─────────────────────────────────────────────────────────┘
```

**Miro-Anweisungen:**
- Overlay-Box mit transparentem Hintergrund (um alle Layers zu umschließen)
- 4 Radio-Button-Optionen für Deployment (visuell markierbar nach Activity 5)
- Sticky Notes für Monitoring-Anforderungen

---

## Referenz zu bestehenden ICIS-Architekturen

**Während des Workshops verfügbar (als separate Miro Frames oder Links):**

1. **ICIS-Klassik (Oracle Forms):** `/diagrams/icis_oracle_forms_architektur.svg`
   - Zeigt 3-Tier-Architektur: UI Presentation, Application Logic, Data Manager, PL/SQL Engine
   - Hilfreich für Verständnis der **aktuellen** Forms-Architektur

2. **ICIS-Gesamt (Überblick):** `/diagrams/architektur_schaubild_icis_gesamt.svg`
   - Zeigt komplettes System: ICIS+, Forms, APEX, Externe Integrationen (SAP, COR Life, GDV, DMS)
   - Hilfreich für Kontext der **Koexistenz**-Strategie

3. **ICIS+ (JEE/Vaadin):** `/diagrams/icis_plus_jee_architekture.svg`
   - Zeigt Vaadin/Sencha UI, Spring Services, Backend Adapters
   - Hilfreich für **Wiederverwendung** von Komponenten

**Miro-Anweisungen:**
- Erstelle 3 kleine Thumbnail-Frames mit Links zu vollständigen Diagrammen
- Platziere sie in der Nähe von Frame 12 als "Referenzmaterial"

---

## Kollaborative Elemente für Workshop-Session

### 1. Sticky Note Zones (vorbereitet)

**Zone A - Technologie-Entscheidungen:**
- Platzhalter für Decisions aus Activities 4, 5, 6
- Farbe: Orange

**Zone B - Offene Fragen:**
- Fragen, die während des Zeichnens entstehen
- Farbe: Rot

**Zone C - Risiken & Constraints:**
- Performance-Bottlenecks, Security-Anforderungen, Compliance
- Farbe: Gelb

**Zone D - Quick Wins:**
- Komponenten-Wiederverwendung, bestehende APIs
- Farbe: Grün

### 2. Annotation-Legende

**Vorbereitet als Miro-Textbox (rechts oben im Frame):**
```
Legende:
━━━  Bestehend (unverändert)
┄┄┄  Neu zu entwickeln
⟷   Koexistenz
→   Datenfluss
⚠️   Risiko / Achtung
✓   Entscheidung getroffen
?   Offene Frage
```

### 3. Facilitator-Prompts (als versteckte Notizen in Miro)

**Fragen zum Stellen während des Zeichnens:**
- "Welche Service-SPs aus dem Katalog (Activity 2) müssen hier exponiert werden?"
- "Wie fließen Daten vom Frontend zur Datenbank? Welche Transformationen?"
- "Wo wird die AI-Logik ausgeführt? Frontend, Integration Layer, oder extern?"
- "Welche Authentifizierung nutzt WGV aktuell? Kann sie wiederverwendet werden?"
- "Wie wird die Koexistenz mit Oracle Forms technisch gelöst? Session-Sharing?"

---

## Erwartetes Output nach 1 Stunde

**Minimal:**
- 4 Layers mit Komponenten gefüllt
- 3 Technologie-Entscheidungen visuell markiert (Integration, Deployment, AI)
- 5-10 Sticky Notes mit offenen Fragen

**Optimal:**
- Datenfluss-Pfeile zwischen Layers gezeichnet
- Service-SP-Mapping skizziert (z.B. "BSP_VERTRAG_DETAILS → /api/contracts/{id}")
- Deployment-Diagramm mit konkrete Infrastruktur-Komponenten (z.B. "3 Pods in AKS")
- Risiko-Annotationen an kritischen Stellen (z.B. "Latenz: Forms→DB direkt vs. via REST")

---

## Miro-Setup-Anweisungen (für Vorbereitung)

### Frame 12 erstellen:

1. **Größe:** Breites Frame (ca. 3000 x 2000 Pixel in Miro)
2. **Hintergrund:** Weiß mit leichtem Grid (optional)
3. **Title:** "Ziel-Architektur: ICIS Modernisiert (Kollaborativ)"

### Komponenten vorzeichnen:

- **Layer-Rechtecke:** 4 horizontale Swimlanes (Frontend, Integration, Backend, External)
- **Basis-Komponenten:** Wie oben beschrieben als Shapes einfügen
- **Decision-Platzhalter:** Radio-Buttons oder Checkboxen für Activities 4, 5, 6

### Interaktive Elemente hinzufügen:

- **Sticky Notes:** 20-30 leere Notes in 4 Farben (Orange, Rot, Gelb, Grün)
- **Pfeile/Connectors:** 10-15 Pfeile bereithalten (nicht verbunden, nur verfügbar)
- **Text-Boxes:** 5-10 leere Textboxen für Ad-hoc-Annotationen

### Referenz-Material verlinken:

- Kleine Thumbnails der 3 bestehenden ICIS-Diagramme platzieren
- Links zu Interpretation-Dateien (`context/*.md`) als Miro-Links

---

## Facilitation-Strategie während Activity 7

### Phase 1: Foundation Review (10 Minuten)

**Facilitator:** "Wir haben ein Grundgerüst vorbereitet mit 4 Layers. Lasst uns kurz durchgehen, ob diese Struktur Sinn macht."

**Aktion:**
- Durchgang Layer 1 → Layer 4
- Klärung von Begriffen (falls nötig)
- Erste Sticky Notes für offene Fragen

### Phase 2: Technology Decisions Mapping (15 Minuten)

**Facilitator:** "Aus den vorherigen Activities haben wir 3 Entscheidungen getroffen. Lasst sie uns hier visuell eintragen."

**Aktion:**
- Integration Layer Technologie markieren (aus Activity 4)
- Deployment Environment markieren (aus Activity 5)
- AI Integration Pattern markieren (aus Activity 6)

### Phase 3: Service-SP Mapping (20 Minuten)

**Facilitator:** "Aus dem Service-SP-Katalog (Activity 2) - welche sind für den MVP am wichtigsten? Wie werden sie exponiert?"

**Aktion:**
- WGV wählt 3-5 kritische Service-SPs
- Zeichne Mapping: SP → REST Endpoint (Beispiel-Notation)
- Diskutiere Aggregation vs. 1:1-Mapping

### Phase 4: Data Flow & Interactions (10 Minuten)

**Facilitator:** "Wie fließen Daten durch das System? Zeichnen wir einen typischen User-Request."

**Aktion:**
- User-Action im Frontend → API-Call → SP → Response
- Pfeile mit Nummern annotieren (1, 2, 3, ...)
- Sticky Notes für Performance-Fragen

### Phase 5: Risks & Open Questions (5 Minuten)

**Facilitator:** "Was sind die größten Risiken in dieser Architektur? Was müssen wir noch klären?"

**Aktion:**
- Rote Sticky Notes für Risiken platzieren
- Gelbe Sticky Notes für Constraints
- Parking Lot für tiefergehende Fragen

---

## Nachbereitungshinweis

**Nach dem Workshop:**
- Miro-Diagramm exportieren als PNG/PDF
- In ADR-Dokument integrieren (siehe Activity 7 in `tag2_architecture_decisions_guide.md`)
- Offene Fragen in Backlog übertragen
- Architekturdiagramm in Tools wie PlantUML, C4 Model oder Structurizr formalisieren (optional, für Dokumentation)

---

## Referenzen

- **Martin Fowler - Strangler Fig Pattern:** https://martinfowler.com/bliki/StranglerFigApplication.html
- **C4 Model (Context, Containers, Components, Code):** https://c4model.com/
- **Oracle Forms Migration Options:** `/context/oracle_forms_migration_options_reference.md`
- **ICIS Architecture Diagrams:** `/diagrams/` (3 SVG-Dateien)
- **Tag 2 Architecture Decisions Guide:** `/facilitation/tag2_architecture_decisions_guide.md`
