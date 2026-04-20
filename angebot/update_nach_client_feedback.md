# Update nach Client-Feedback (WGV PM Sanity-Check)

**Datum**: 2026-04-18  
**Anlass**: Sanity-Check Meeting mit WGV Projektmanager

---

## Client-Feedback (WGV PM)

**Kernaussage**: 
> "Der Fokus des Workshops liegt auf der Evaluation der **technischen Machbarkeit und Readiness** von WGV, eine neue Frontend-Lösung zu integrieren, die nicht von Oracle Forms abhängt (ICIS-Migration). UI/UX Themen sollten präsentiert werden, aber sind **nicht hohe Priorität** - mehr als **Approach-Präsentation**, wie codecentric mit UX/UI Transformation umgeht."

**Implikationen**:
1. ✅ Technische Machbarkeit = Haupt-Fokus (passt zu Tag 2 Struktur)
2. ⚠️ UI/UX = Methodologie-Präsentation (NICHT kollaborative Workshop-Session)
3. ✅ Committete Agenda (`2026-04-15_Entwurf_Agenda_v3.md`) entspricht Client-Erwartungen

---

## Durchgeführte Änderungen

### 1. Frame 5 (UI/UX) - Typ-Änderung von HYBRID zu INPUT

**Vorher**:
- Typ: INPUT + CAPTURE (HYBRID)
- Zeit: 90 min
- Inhalt: Kollaborative Pattern-Zuordnung, WGV sticky notes, gemeinsame Entscheidung
- Ziel: WGV identifiziert, welche Masken zu welchem Pattern passen

**Nachher**:
- Typ: **INPUT** (codecentric Präsentation)
- Zeit: **45-60 min** (Präsentation 30-40 min + Q&A 15-20 min)
- Inhalt: codecentric zeigt **Methodologie** für UX/UI Transformation
  - User Research & Journey Mapping
  - Information Architecture
  - Pattern Library Entwicklung
  - Iteratives Mockup & Prototyping
  - Projekterfahrung aus anderen Migrationen
  - Empfehlung für WGV (Hybrid Approach)
- Ziel: WGV **versteht**, WIE codecentric UX/UI Transformation angeht (für spätere Phasen)

**Begründung**: Client will "approach presentation", keine ausführliche kollaborative UX-Session.

**Datei**: `/angebot/miro_board_structure.md` - Frame 5 Layout und Beschreibung komplett überarbeitet

---

### 2. Frame 3 (Domain Map) - Zeit erweitert auf 150 min

**Vorher**:
- Zeit: 120 min

**Nachher**:
- Zeit: **150 min**

**Begründung**: 
- Facilitation Guide (`tag1_bounded_context_session_guide.md`) benötigt 150-175 min (Event Storming 45-60 + Bounded Context Discovery 90-115)
- Gewonnene Zeit aus Frame 5 Reduktion (-30-45 min) wird hier investiert
- Vollständiger ICIS/ICIS+ Deep Dive ist kritisch für technische Machbarkeit

**Datei**: `/angebot/miro_board_structure.md` - Frame 3 Time Allocation aktualisiert

---

### 3. Information Architecture Integration

**Rationale**: IA ist relevant sowohl für System-Modellierung/Architektur als auch für UX/UI.

**Integration an 2 Stellen**:

#### 3a. Frame 3 (Business-Sicht IA)

**Wo**: `/facilitation/bounded_context_discovery_questionnaire.md` - Kategorie 2 erweitert

**Neue Kategorie 2.2**: Information Architecture (Informationsstruktur)

**Inhalt**:
- **Informations-Hierarchie**: Hierarchisch vs. vernetzt? (z.B. Kunde → Vertrag → Schaden)
- **Core Entities**: Welche zentralen Informationsobjekte? (Kunde, Vertrag, Schaden, Produkt, Partner)
- **Shared Entities**: Was wird über Bounded Contexts geteilt? (Adresse, Dokument, Produktkatalog)
- **Entitäts-Beziehungen**: Wie hängen Core Entities zusammen? (1:N, M:N Beziehungen)

**Output**: High-level Information Architecture Diagramm (Entity-Relationship-Übersicht)

**Zusätzliche Zeit**: +0 min (ist Teil der 150 min Bounded Context Discovery, Kategorie 2 erweitert von ~20 min auf ~30 min)

**Frame 3 Layout ergänzt** (in `/angebot/miro_board_structure.md`):
- Neuer Bereich "INFORMATION ARCHITECTURE (HIGH-LEVEL)"
- Visualisierung: Entity-Boxen mit Beziehungspfeilen (z.B. KUNDE → VERTRAG → SCHADEN)
- Shared Data Liste

#### 3b. Frame 8 Part 1 (Technische Detail-Sicht IA)

**Wo**: `/angebot/miro_board_structure.md` - Frame 8 Part 1 Layout erweitert

**Neuer Bereich**: INFORMATION ARCHITECTURE (DETAIL-EBENE)

**Inhalt**:
- **Entity-Zugriff pro SP**: Welche Stored Procedures greifen auf welche Entities zu?
  - Beispiel: SP_KUNDE_SUCHEN → Read: KUNDE, ADRESSE
  - Beispiel: SP_SCHADEN_ANLEGEN → Create: SCHADEN, Read: KUNDE
- **CRUD-Operations dokumentieren**: Create, Read, Update, Delete pro Entity
- **Daten-Fluss-Muster**: Welche SPs greifen auf Shared Entities zu vs. Bounded-Context-spezifisch?

**Output**: Entity-SP-Mapping (verbindet Business-Sicht aus Frame 3 mit technischer Detail-Sicht)

**Zusätzliche Zeit**: +0 min (ist Teil der 60-75 min SP-Präsentation)

**Vorteil der 2-Ebenen-Integration**:
- Frame 3: WGV erklärt **Business-Sicht** (Welche Entities gibt es? Wie hängen sie zusammen?)
- Frame 8: WGV zeigt **Technische Detail-Sicht** (Wie greifen SPs auf Entities zu?)
- Beide Sichten zusammen ergeben vollständiges IA-Bild für System-Architektur UND UX/UI

---

## Zeitbudget-Änderungen Übersicht

| Frame | Vorher | Nachher | Änderung | Begründung |
|-------|--------|---------|----------|------------|
| Frame 3 (Domain Map) | 120 min | **150 min** | **+30 min** | Vollständiger ICIS Deep Dive, inkl. IA Business-Sicht |
| Frame 5 (UI/UX) | 90 min (HYBRID) | **45-60 min** (INPUT) | **-30-45 min** | Methodologie-Präsentation statt kollaborativ |
| Frame 8 Part 1 (Services/SP) | 60 min | 60 min (unverändert) | +0 min | IA Detail-Sicht integriert ohne Zeitaufschlag |

**Tag 1 Gesamt**: 383-398 min (6h 23min - 6h 38min) - passt zu verfügbarer Zeit (380 min + kleine Überziehung akzeptabel)

---

## Implikationen für andere Dokumente

### ✅ Keine Änderung erforderlich

**`/angebot/2026-04-15_Entwurf_Agenda_v3.md`** (Committete Agenda):
- Bleibt unverändert
- Client bestätigt: Agenda entspricht Erwartungen
- "Anwendungskonzept (UI/UX) Skizze: 1,5 Stunden" passt zu Frame 5 neu (45-60 min Präsentation ist Teil der 1,5h slot, Rest für Pausen/Puffer)

### ⚠️ Zu aktualisieren (wenn relevant)

**`/angebot/agenda_miro_aktivitaeten_abgleich.md`**:
- Frame 5 Typ: HYBRID → INPUT
- Frame 5 Zeit: 90 min → 45-60 min
- Frame 3 Zeit: 120 min → 150 min

**`/angebot/agenda_alternative_ohne_ai_coding.md`**:
- Alternative Planung (ohne AI-Coding) bleibt konzeptionell gültig
- Frame 5 sollte dort auch auf INPUT reduziert werden (falls genutzt)

**`/angebot/agenda_alternative_erweiterte_ux.md`**:
- Alternative mit erweiterter UX ist NICHT mehr relevant (Client will keine ausführliche UX-Session)
- Kann archiviert oder als "nicht gewählte Option" markiert werden

**`/facilitation/tag1_uiux_konzept_guide.md`** (wenn vorhanden):
- Sollte um Hinweis ergänzt werden: "Client Feedback: UX/UI als Methodologie-Präsentation (INPUT), nicht kollaborative Session"

---

## Nächste Schritte

### Vor dem Workshop (noch zu klären)

1. **Frame 16 (AI-Driven Dev Workshop)**:
   - ☐ Kollege definiert Inhalt und Zeitplan
   - ☐ Fokus auch auf technische Readiness? (Tooling-Setup, CI/CD-Integration)

2. **Tag 1 Facilitation Guides finalisieren**:
   - ☐ `tag1_domain_mapping_guide.md` - Referenz auf IA in Kategorie 2.2 ergänzen
   - ☐ `tag1_bounded_context_session_guide.md` - Phase 2 Zeitbudget auf 30 min aktualisieren (war 20 min)

3. **Miro Board Setup**:
   - ☐ Frame 3 mit IA-Bereich vorbereiten (Entity-Boxen, Relationship-Arrows)
   - ☐ Frame 5 als INPUT-Frame gestalten (Präsentations-Folien, kein CAPTURE-Bereich)
   - ☐ Frame 8 Part 1 SP-Katalog-Template mit Entity-Zugriff-Spalte erweitern

4. **UX/UI Präsentation vorbereiten** (Frame 5):
   - ☐ Methodologie-Folien erstellen (User Research, IA, Pattern Library, Prototyping)
   - ☐ Projekterfahrung aus ähnlichen Migrationen dokumentieren
   - ☐ Empfehlung für WGV (Hybrid Approach) mit Beispielen

---

## Zusammenfassung

**Kernänderungen**:
1. ✅ Frame 5 (UI/UX): HYBRID → INPUT (45-60 min Methodologie-Präsentation)
2. ✅ Frame 3 (Domain Map): 120 min → 150 min (vollständiger ICIS Deep Dive)
3. ✅ Information Architecture integriert in Frame 3 (Business-Sicht) + Frame 8 Part 1 (Detail-Sicht)

**Alignment mit Client-Feedback**:
- ✅ Fokus auf technische Machbarkeit (Tag 2 bleibt stark, Tag 1 Frame 3 erweitert)
- ✅ UI/UX als Approach-Präsentation (nicht hohe Priorität)
- ✅ Committete Agenda bleibt gültig

**Nächster Meilenstein**: Workshop am 28.-30. April 2026

---

**Bearbeitet**: `/angebot/miro_board_structure.md`, `/facilitation/bounded_context_discovery_questionnaire.md`  
**Status**: Änderungen implementiert, bereit für Miro Board Setup
