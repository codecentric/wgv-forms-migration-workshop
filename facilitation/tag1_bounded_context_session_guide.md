# Tag 1 Bounded Context Discovery Session - Facilitator Guide

**Session-Name**: Bounded Context Discovery innerhalb ICIS-Forms  
**Dauer**: 60-90 Minuten  
**Teil von**: Domain Mapping Aktivitäten (Tag 1)  
**Miro Frame**: Frame 3 - Domain Map (CAPTURE)

---

## Session-Kontext

### Das Problem
Die ICIS-Architekturdiagramme zeigen uns:
- **`icis-forms`**: Ein monolithisches Oracle Forms System mit ~900 Masken
- **Technische Struktur**: 3-Tier-Architektur (Client, Middle-Tier, Database)
- **Externe Integrationen**: SAP, COR Life, GDV, DMS, etc.

**Aber**: Diese Diagramme zeigen nur die **technische** Architektur, nicht die **fachlichen Domänengrenzen**.

### Warum ist das wichtig?
- Wir können nicht alle 900 Masken auf einmal migrieren
- Wir brauchen natürliche **fachliche Grenzen** für schrittweisen Ansatz
- **Bounded Contexts** helfen uns:
  - MVP-Scope zu definieren (3-5 Masken aus EINER Domäne)
  - Migrations-Roadmap zu strukturieren
  - Teams zu organisieren
  - Abhängigkeiten zu verstehen

### Die zentrale Erkenntnis
> **icis-forms ist EIN technisches System, das wahrscheinlich MEHRERE Geschäftsdomänen abdeckt.**

Beispiel-Hypothesen (zu validieren mit WGV):
- Vertragsmanagement (Policy Lifecycle)
- Schadenbearbeitung (Claims Processing)
- Kundenverwaltung (Customer Management)
- Produktverwaltung (Product Management)
- Leben-spezifisch (Life Insurance)
- KFZ-spezifisch (Motor Vehicle)

---

## Session-Ablauf

### Vorbereitung (vor der Session)

**Materialien bereitstellen**:
- [ ] Miro Board Frame 3 vorbereitet (mit LEITFRAGE-Box)
- [ ] Architekturdiagramme sichtbar machen (als Referenz)
- [ ] Fragenkatalog griffbereit (`bounded_context_discovery_questionnaire.md`)
- [ ] Sticky Notes, Whiteboard-Marker (wenn physisch)

**Von WGV anfordern** (idealerweise vorher):
- [ ] Liste der 900 Masken (wenn verfügbar, auch nur Stichprobe)
- [ ] Organigramm der Versicherungs-Teams
- [ ] Datenbank-Schema-Übersicht (ERD)
- [ ] Kontaktliste Domain-Experten

---

### Phase 1: Kontext setzen (10 Min)

**Ziel**: Teilnehmer verstehen, warum wir nach Bounded Contexts suchen

**Facilitator sagt**:
> "Wir haben die Architekturdiagramme analysiert. Sie zeigen uns, dass icis-forms ein technisches System mit ~900 Masken ist. Aber wir wissen nicht, welche fachlichen Domänen diese Masken abdecken. Das müssen SIE uns erklären, denn nur Sie kennen die Geschäftsprozesse."

**Zeigen auf Miro**:
- Frame 3 mit LEITFRAGE-Box
- Erklären: "Wir suchen nach natürlichen fachlichen Grenzen für die schrittweise Migration"

**Architekturdiagramm-Referenz**:
- Zeigen `architektur_schaubild_icis_gesamt.svg`
- Hinweis: "Hier sehen wir icis-forms als EINE Box. Aber was ist DRIN?"

---

### Phase 2: Strukturiertes Interview (60-70 Min)

**Methode**: Gehen Sie durch den Fragenkatalog systematisch

**Reihenfolge** (aus `bounded_context_discovery_questionnaire.md`):

1. **Kategorie 1: Fachliche Gruppierung** (~15 Min)
   - 1.1 Prozess-basierte Gruppierung
   - 1.2 Produktlinien-basierte Gruppierung
   - 1.3 Organisatorische Verantwortung
   
   **Facilitator-Technik**:
   - Nutzen Sie Sticky Notes für jede genannte Prozessgruppe
   - Lassen Sie WGV schätzen: "Wie viele Masken circa pro Gruppe?"
   - Zeichnen Sie erste Boxen auf Miro Frame 3

2. **Kategorie 2: Daten-basierte Abgrenzung** (~20 Min)
   - 2.1 Datenbank-Schema-Zuordnung
   - 2.2 Daten-Ownership (CRUD-Verantwortung)
   
   **Facilitator-Technik**:
   - Fragen: "Welche Tabellen gehören zu welcher Prozessgruppe?"
   - Identifizieren: "Wo sind Shared Data (z.B. Kundenstamm) vs. isolierte Daten?"
   - Zeichnen Sie Daten-Cluster auf separatem Bereich

3. **Kategorie 3: Integration & Abhängigkeiten** (~15 Min)
   - 3.1 Externe System-Integrationen
   - 3.2 Interne Abhängigkeiten
   
   **Facilitator-Technik**:
   - Zeigen Sie externe Systeme aus Architekturdiagramm (SAP, COR Life, GDV, DMS)
   - Fragen: "Welche Masken-Gruppen nutzen welches externe System?"
   - Zeichnen Sie Verbindungen auf Miro

4. **Kategorie 4: Sprache & Begriffe** (~15 Min)
   - 4.1 Fachbegriffe (unterschiedliche Bedeutungen in verschiedenen Kontexten?)
   - 4.2 Domänen-Experten
   
   **Facilitator-Technik**:
   - Suchen Sie nach Begriffen, die kontextabhängig sind
   - Dokumentieren Sie Ansprechpartner pro Domäne

5. **Kategorie 5: Geschäftswert & Änderungsfrequenz** (~10 Min)
   - 5.1 Kritikalität
   - 5.2 Änderungshäufigkeit
   
   **Facilitator-Technik**:
   - Nutzen Sie Farbcodierung: Rot (kritisch), Gelb (wichtig), Grün (wünschenswert)

6. **Kategorie 6: Synthesis - Bounded Contexts** (~15 Min)
   - 6.1 Bounded Context-Vorschläge formulieren
   - 6.2 MVP-Kandidaten identifizieren
   
   **Facilitator-Technik**:
   - Fassen Sie zusammen: "Basierend auf unserer Diskussion, sehe ich folgende Contexts..."
   - Fragen Sie WGV: "Macht diese Gruppierung Sinn?"
   - Validieren Sie die Grenzen

---

### Phase 3: Visualisierung & Validierung (10 Min)

**Ziel**: Bounded Contexts auf Miro Frame 3 finalisieren

**Aktivitäten**:
1. Zeichnen Sie finale Bounded Context-Boxen
2. Benennen Sie jeden Context
3. Notieren Sie Kernverantwortlichkeiten
4. Zeigen Sie Verbindungen (Pfeile zwischen Contexts)
5. Markieren Sie externe Integrationen
6. Color-Coding:
   - **Orange**: Core Domains (z.B. Vertragsmanagement, Schadenbearbeitung)
   - **Blue**: Supporting Domains (z.B. Kundenverwaltung, Produktkatalog)
   - **Gray**: Generic Domains (z.B. Dokumentenverwaltung via DMS)

**Validierung mit WGV**:
- "Haben wir etwas Wichtiges vergessen?"
- "Stimmen die Grenzen so?"
- "Gibt es Überschneidungen oder Unklarheiten?"

---

## Session-Outputs

### 1. Domain Map (Miro Frame 3)
**Was es zeigt**:
- 4-8 identifizierte Bounded Contexts
- Kernverantwortlichkeiten pro Context
- Externe Integrationen pro Context
- Verbindungen/Abhängigkeiten zwischen Contexts
- Farbcodierung (Core/Supporting/Generic)

### 2. Bounded Context Katalog (Dokumentiert)
**Template pro Context**:
```markdown
## [Context-Name, z.B. "Vertragsmanagement KFZ"]

**Verantwortlichkeit**: 
- Verwaltung des kompletten Lebenszyklus von KFZ-Versicherungsverträgen

**Geschäftsprozesse**:
- Neuantrag KFZ
- Vertragsänderung (Fahrzeugwechsel, Deckungserweiterung)
- Vertragskündigung

**Masken-Anzahl (ca.)**: ~80-120 Masken

**Datenbank-Bereiche**:
- Tabellen: VERTRAG_KFZ, FAHRZEUG, PRAEMIE_KFZ, TARIF_KFZ
- Shared: KUNDE, ADRESSE (aus Customer Context)

**Externe Integrationen**:
- KFZ-Webservice (Typklassen, DAT-Daten)
- GDV-Schnittstelle (Branchenkommunikation)
- SAP (Abrechnung)

**Team-Ownership**: 
- WGV Team: KFZ-Versicherung (Ansprechpartner: [Name])

**Abgrenzung**:
- NICHT enthalten: Schadenbearbeitung KFZ (eigener Context "Schaden KFZ")
- NICHT enthalten: Lebensversicherung (eigener Context)
```

### 3. MVP-Kandidaten Ranking
**Top 2-3 Contexts** für MVP-Scope, bewertet nach:
- ✅ Unabhängigkeit (wenige Abhängigkeiten)
- ✅ Klare Datengrenzen
- ✅ Managbare Komplexität
- ✅ Demonstrierbarer Geschäftswert
- ✅ Verfügbarkeit von Domain-Experten

---

## Integration mit anderen Tag 1-Aktivitäten

| Vorher | Diese Session | Nachher |
|--------|---------------|---------|
| **Event Storming Light** → | Bounded Context Discovery | → **Mask Analysis Matrix** |
| Liefert: Domain Events | Nutzt: Events zur Prozess-Abgrenzung | Nutzt: Contexts zur Masken-Strukturierung |

**Workflow**:
1. Event Storming identifiziert **was passiert** (Domain Events)
2. Bounded Context Discovery identifiziert **wer ist verantwortlich** (Contexts)
3. Mask Analysis Matrix identifiziert **welche konkreten Masken** (MVP-Kandidaten)

---

## Häufige Herausforderungen & Lösungen

### Challenge 1: "Wir haben keine klaren Grenzen"
**Symptom**: WGV sagt "alles hängt mit allem zusammen"

**Lösung**:
- Fragen Sie nach **Datenbesitz**: "Wer erstellt Verträge? Wer erstellt Schäden?"
- Fragen Sie nach **Teams**: "Welche Teams arbeiten zusammen, welche separat?"
- Akzeptieren Sie Überschneidungen: Bounded Contexts sind nicht 100% isoliert

### Challenge 2: "Wir kennen die Masken-Anzahl nicht genau"
**Symptom**: Keine Inventarliste der 900 Masken verfügbar

**Lösung**:
- Arbeiten Sie mit Schätzungen: "Ungefähr wie viel Prozent der Masken sind KFZ?"
- Fokussieren Sie auf **bekannte** Masken-Cluster
- Dokumentieren Sie: "Zu klären: Genaue Masken-Zuordnung"

### Challenge 3: "Leben ist bei COR Life, nicht bei uns"
**Symptom**: Teile der Domäne sind ausgelagert

**Lösung**:
- Dokumentieren Sie dies als **externen Context**: "Leben (Partner: COR Life)"
- Identifizieren Sie **Integration-Masken**: "Welche ICIS-Masken rufen COR Life auf?"
- Markieren Sie dies auf der Domain Map

### Challenge 4: "Wir haben zu viele Contexts"
**Symptom**: >10 potenzielle Bounded Contexts identifiziert

**Lösung**:
- Fassen Sie Sub-Contexts zusammen: "KFZ Vertrag" + "KFZ Schaden" → "KFZ"
- Priorisieren Sie: "Welche 5 sind am wichtigsten?"
- Nutzen Sie Hierarchie: "KFZ ist ein Sub-Context von Versicherung"

---

## Cheat Sheet: Erkennungsmerkmale für Bounded Contexts

| Merkmal | Frage | Indikator für separaten Context |
|---------|-------|--------------------------------|
| **Prozess** | Welcher Geschäftsprozess? | Komplett unterschiedliche Prozess-Flows |
| **Daten** | Welche Tabellen werden genutzt? | Separate Datenbank-Schema-Cluster |
| **Sprache** | Welche Fachbegriffe? | Gleiche Wörter, andere Bedeutungen |
| **Teams** | Wer ist verantwortlich? | Unterschiedliche WGV-Teams |
| **Integration** | Welche externen Systeme? | Dedizierte externe System-Integrationen |
| **Änderungsfrequenz** | Wie oft ändern sich Anforderungen? | Unabhängige Change-Zyklen |

---

## Nächste Schritte nach der Session

1. **Dokumentieren**: 
   - [ ] Bounded Context Katalog erstellen
   - [ ] Miro Frame 3 Screenshot speichern
   - [ ] Entscheidungen festhalten

2. **Validieren**:
   - [ ] Mit WGV-Stakeholdern reviewen
   - [ ] Fehlende Informationen nachfordern
   - [ ] Anpassungen basierend auf Feedback

3. **Vorbereiten für Frame 4** (Mask Analysis Matrix):
   - [ ] 10-15 konkrete Masken aus identifizierten Contexts auswählen
   - [ ] Pro Context: 2-3 Masken-Beispiele
   - [ ] Domain-Experten für Masken-Details identifizieren

4. **Tag 2 Vorbereitung**:
   - [ ] Bounded Contexts informieren Architektur-Diskussionen
   - [ ] Integration Layer Design nutzt Context-Grenzen
   - [ ] Deployment-Strategie pro Context erwägen

---

## Referenzen

- **Fragenkatalog**: `facilitation/bounded_context_discovery_questionnaire.md`
- **Miro Frame**: Frame 3 in `angebot/miro_board_structure.md`
- **Architektur-Kontext**: `context/architektur_schaubild_icis_gesamt.md`
- **Forms Detail**: `context/icis_oracle_forms_architektur.md`
- **DDD Guide**: `facilitation/tag1_domain_mapping_guide.md`

---

**Erstellt**: 2026-04-17  
**Für**: WGV ICIS Modernisierungs-Workshop Tag 1  
**Facilitator**: codecentric Team
