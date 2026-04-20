# Bounded Context Discovery Questionnaire - ICIS Forms

**Zweck**: Identifizierung von Bounded Contexts innerhalb der ~900 Oracle Forms Masken

**Kontext**: Die ICIS-Forms-Anwendung ist ein monolithisches System, das wahrscheinlich mehrere fachliche Domänen abdeckt. Dieses Fragenkatalog hilft uns, die fachlichen Grenzen zu entdecken, die für die schrittweise Modernisierung entscheidend sind.

**Zeit**: ~60-90 Minuten (Teil der Domain Mapping Aktivitäten am Tag 1)

---

## Leitfrage (Guiding Question)

> **"Innerhalb der ~900 ICIS-Forms-Masken: Welche fachlichen Domänen existieren, und wie können wir sie voneinander abgrenzen?"**

Diese Frage ist zentral, weil:
- Wir können nicht alle 900 Masken auf einmal migrieren
- Wir brauchen natürliche fachliche Grenzen für die schrittweise Migration
- Bounded Contexts helfen uns, einen sinnvollen MVP-Scope zu definieren
- Die Architekturdiagramme zeigen nur die technische Struktur, nicht die fachlichen Grenzen

---

## Fragenkatalog

### Kategorie 1: Fachliche Gruppierung der Masken (~15 Min)

#### 1.1 Prozess-basierte Gruppierung
**Frage**: Wenn Sie die 900 Masken in große Prozess-Gruppen einteilen müssten, welche wären das?

**Hilfestellung**: 
- Denken Sie an die Hauptprozesse eines Versicherungsunternehmens (z.B. Vertragsmanagement, Schadenbearbeitung, Kundenservice, etc.)
- Gibt es Masken-Cluster, die einen kompletten Geschäftsprozess abbilden?

**Beispiel-Antworten**:
- [ ] Vertragsmanagement (Neuantrag, Änderung, Kündigung)
- [ ] Schadenbearbeitung (Meldung, Regulierung, Zahlungsfreigabe)
- [ ] Kundenverwaltung (Stammdaten, Korrespondenz)
- [ ] Produktverwaltung (Tarife, Bedingungen, Kalkulationen)
- [ ] _Weitere: _______________________

**Output**: Liste der identifizierten Prozess-Cluster mit ungefähren Masken-Anzahlen

---

#### 1.2 Produktlinien-basierte Gruppierung
**Frage**: Gibt es Masken, die spezifisch für bestimmte Versicherungsprodukte sind?

**Hilfestellung**:
- Leben vs. Sach vs. KFZ vs. Haftpflicht
- Gibt es dedizierte Masken-Sätze für verschiedene Produktlinien?

**Beispiel-Antworten**:
- [ ] Leben (Life Insurance) - Anzahl Masken: ___
- [ ] KFZ (Motor Vehicle) - Anzahl Masken: ___
- [ ] Sach/Haftpflicht (Property/Liability) - Anzahl Masken: ___
- [ ] Produktübergreifende Masken - Anzahl: ___

**Output**: Produktlinien-Matrix mit Masken-Zuordnung

---

#### 1.3 Organisatorische Verantwortung
**Frage**: Gibt es verschiedene WGV-Teams, die für unterschiedliche Masken-Bereiche verantwortlich sind?

**Hilfestellung**:
- Welche Teams arbeiten mit welchen Masken?
- Gibt es klare Ownership-Grenzen?
- Wo gibt es Überschneidungen oder Unklarheiten?

**Output**: Organisationsstruktur-Übersicht mit Masken-Ownership

---

### Kategorie 2: Daten-basierte Abgrenzung & Information Architecture (~30 Min)

#### 2.1 Datenbank-Schema-Zuordnung
**Frage**: Arbeiten verschiedene Masken-Gruppen mit unterschiedlichen Datenbank-Schemata oder Tabellen-Clustern?

**Hilfestellung**:
- Gibt es dedizierte Tabellen für bestimmte Geschäftsprozesse?
- Wo gibt es Shared Data (z.B. Kundenstammdaten) vs. isolierte Daten?

**Beispiel-Struktur**:
```
Vertragsdaten (Policy):
  - VERTRAG, VERTRAGSPOSITION, PRAEMIE, ...
  - Verwendet von Masken: [Liste]

Schadendaten (Claims):
  - SCHADEN, SCHADENEREIGNIS, SCHADENZAHLUNG, ...
  - Verwendet von Masken: [Liste]

Kundendaten (Customer) [SHARED]:
  - KUNDE, ADRESSE, KONTAKT, ...
  - Verwendet von: ALLEN Masken
```

**Output**: Datenbank-Schema-Cluster mit Masken-Zuordnung

---

#### 2.2 Information Architecture (Informationsstruktur)
**Frage**: Wie ist die Informationsstruktur in ICIS organisiert? Welche Core Entities gibt es und wie hängen sie zusammen?

**Hilfestellung**:
- **Informations-Hierarchie**: Ist die Struktur hierarchisch oder vernetzt?
  - Beispiel hierarchisch: Kunde → Vertrag → Schaden (Baum-Struktur)
  - Beispiel vernetzt: Kunde ↔ Vertrag ↔ Schaden ↔ Partner (Netzwerk)
- **Core Entities**: Was sind die zentralen Informationsobjekte?
  - Beispiele: Kunde, Vertrag, Schaden, Produkt, Partner, Dokument
- **Shared Entities**: Welche Informationen werden über Bounded Contexts hinweg geteilt?
  - Beispiele: Kundenstamm, Adressdaten, Produktkatalog, Dokumente
- **Entitäts-Beziehungen**: Wie hängen die Core Entities zusammen?
  - Beispiel: 1 Kunde kann N Verträge haben, 1 Vertrag kann M Schäden haben

**Beispiel-Struktur** (zu dokumentieren):
```
CORE ENTITIES:
  - KUNDE (Master-Entity)
    └─→ VERTRAG (1:N Beziehung)
        └─→ SCHADEN (1:M Beziehung)
    └─→ PARTNER (M:N Beziehung)
  
  - PRODUKT (eigenständige Entity)
    └─→ VERTRAG (referenziert Produkt)

SHARED DATA (über alle Contexts):
  - ADRESSE (genutzt von Kunde, Partner, Schaden-Ort)
  - DOKUMENT (genutzt von allen)
  - BANKVERBINDUNG (genutzt von Kunde, Partner)
```

**Facilitator-Technik**:
- Zeichnen Sie die Haupt-Entities auf Miro als Boxen
- Verbinden Sie sie mit Pfeilen (Beziehungen)
- Markieren Sie Shared Entities mit anderem Farbcode
- Fragen Sie WGV: "Fehlt etwas Wichtiges?"

**Output**: High-level Information Architecture Diagramm (Entity-Relationship-Übersicht)

---

#### 2.3 Daten-Ownership
**Frage**: Welche Masken SCHREIBEN (erstellen/ändern) vs. nur LESEN bestimmte Datenentitäten?

**Hilfestellung**:
- Wer ist "Master" für Kundendaten? Vertragsdaten? Schadendaten?
- Gibt es klare Create/Update/Delete-Verantwortlichkeiten?

**Output**: CRUD-Matrix (welcher Kontext ist für welche Entität zuständig)

---

### Kategorie 3: Integration & Abhängigkeiten (~15 Min)

#### 3.1 Externe System-Integrationen
**Frage**: Welche Masken-Gruppen integrieren mit welchen externen Systemen?

**Referenz externe Systeme** (aus Architekturdiagramm):
- SAP (Finanzen)
- COR Life (Lebensversicherung)
- GDV-Schnittstelle (Branchenkommunikation)
- Imagemaster DMS (Dokumentenmanagement)
- KFZ-Webservice

**Beispiel-Mapping**:
```
Leben-Masken → COR Life Integration
KFZ-Masken → KFZ-Webservice + GDV
Schaden-Masken → DMS (Dokumentenablage)
Vertrag-Masken → SAP (Abrechnung), DMS
```

**Output**: Integration-Map (welche Domäne nutzt welche externe Integration)

---

#### 3.2 Interne Abhängigkeiten
**Frage**: Gibt es Masken-Gruppen, die stark voneinander abhängig sind vs. relativ unabhängig funktionieren?

**Hilfestellung**:
- Welche Masken müssen immer zusammen funktionieren?
- Wo gibt es lose Kopplung vs. enge Kopplung?
- Könnten bestimmte Masken-Gruppen theoretisch isoliert modernisiert werden?

**Output**: Abhängigkeits-Graph (zeigt starke vs. schwache Kopplung)

---

### Kategorie 4: Sprache & Begriffe (Ubiquitous Language) (~15 Min)

#### 4.1 Fachbegriffe
**Frage**: Gibt es Fachbegriffe, die in verschiedenen Masken-Bereichen unterschiedliche Bedeutungen haben?

**Beispiel**:
- Bedeutet "Vertrag" in Leben-Masken etwas anderes als in KFZ-Masken?
- Gibt es produktspezifische Begriffe, die nicht produktübergreifend verwendet werden?

**Output**: Glossar mit Kontextgrenzen (wo gilt welche Definition)

---

#### 4.2 Domänen-Experten
**Frage**: Welche WGV-Mitarbeiter (Domain Experts) kennen sich in welchen Masken-Bereichen am besten aus?

**Hilfestellung**:
- Gibt es spezialisierte Experten für Leben, KFZ, Schaden, etc.?
- Wer könnte uns bei der Analyse spezifischer Masken-Gruppen helfen?

**Output**: Liste von Ansprechpartnern pro identifizierter Domäne

---

### Kategorie 5: Geschäftswert & Änderungsfrequenz (~10 Min)

#### 5.1 Kritikalität
**Frage**: Welche Masken-Gruppen sind geschäftskritisch vs. nice-to-have?

**Bewertungsskala**: 
- **Kritisch**: System kann ohne diese nicht funktionieren
- **Wichtig**: Starke Beeinträchtigung bei Ausfall
- **Wünschenswert**: Komfortfunktionen

**Output**: Priorisierungs-Matrix nach Geschäftswert

---

#### 5.2 Änderungshäufigkeit
**Frage**: Welche Masken-Bereiche ändern sich häufig vs. selten?

**Hilfestellung**:
- Wo gibt es häufige Anpassungen wegen Gesetzesänderungen?
- Wo ist der Code stabil und erprobt?

**Beispiel**:
- GDV-Schnittstellen-Masken: Ändern sich bei GDV-Releases
- Stammdaten-Masken: Sehr stabil
- Produkt-Masken: Ändern sich bei neuen Tarifen

**Output**: Änderungsfrequenz-Heatmap

---

### Kategorie 6: Kandidaten für Bounded Contexts (~15 Min)

#### 6.1 Synthesis: Bounded Context-Vorschläge
**Basierend auf den obigen Antworten**: Welche Bounded Contexts erscheinen sinnvoll?

**Template für jeden Context**:
```
Name: [z.B. "Vertragsmanagement KFZ"]

Verantwortlichkeit: 
  - Was macht dieser Context?
  - Welche Geschäftsprozesse deckt er ab?

Masken-Anzahl (ca.): 
  - [Schätzung]

Datenbank-Bereiche:
  - [Tabellen/Schemas]

Externe Integrationen:
  - [z.B. KFZ-Webservice, GDV]

Team-Ownership:
  - [Welches WGV-Team]

Abgrenzung zu anderen Contexts:
  - [Was gehört NICHT dazu]
```

**Output**: Liste von 4-8 vorgeschlagenen Bounded Contexts mit Details

---

#### 6.2 MVP-Kandidaten
**Frage**: Welcher der identifizierten Bounded Contexts wäre ein guter Kandidat für den MVP (3-5 Masken)?

**Bewertungskriterien**:
- ✅ Relativ unabhängig von anderen Contexts
- ✅ Klar abgegrenzte Daten
- ✅ Managbare Komplexität
- ✅ Geschäftswert ist demonstrierbar
- ✅ Nicht zu viele externe Abhängigkeiten

**Output**: Rangliste der Contexts für MVP-Eignung

---

## Facilitator-Hinweise

### Vorbereitung
- [ ] Liste der 900 Masken (wenn verfügbar) mit Namen/Kurzbeschreibungen
- [ ] Organigramm WGV (Versicherungs-Teams)
- [ ] Datenbank-Schema-Übersicht (ERD wenn vorhanden)
- [ ] Architekturdiagramm ausdrucken/auf Miro vorbereiten

### Während der Session
- **Timeboxing**: Jede Kategorie hat ein Zeitlimit
- **Visualisierung**: Zeichnen Sie Bounded Context-Grenzen auf Whiteboard/Miro
- **Sticky Notes**: Masken-Namen auf Sticky Notes → können in Contexts gruppiert werden
- **Parking Lot**: Fragen, die später geklärt werden müssen

### Nach der Session
- [ ] Dokumentieren Sie die identifizierten Bounded Contexts
- [ ] Erstellen Sie Context Map (zeigt Beziehungen zwischen Contexts)
- [ ] Validieren Sie mit WGV-Stakeholdern
- [ ] Nutzen Sie Ergebnisse für Frame 4 (Mask Analysis Matrix)

---

## Integration mit anderen Tag 1-Aktivitäten

| Aktivität | Bezug zu Bounded Contexts |
|-----------|---------------------------|
| **Event Storming Light** | Identifiziert Domain Events → helfen, Prozess-Grenzen zu erkennen |
| **Context Mapping Interview** | Nutzt Ergebnisse dieses Fragebogens als Input |
| **Core Domain Chart** | Priorisiert die identifizierten Contexts (Core vs. Supporting vs. Generic) |
| **Mask Analysis Matrix** | Nutzt Bounded Contexts zur Strukturierung der Masken-Auswahl |

---

## Erwartete Outputs

1. **Domain Map** (Miro Frame 3):
   - Visualisierung der identifizierten Bounded Contexts
   - Verbindungen/Abhängigkeiten zwischen Contexts
   - Externe Integrationen pro Context

2. **Bounded Context Katalog**:
   - 4-8 definierte Contexts mit Details
   - CRUD-Verantwortlichkeiten
   - Team-Ownership

3. **MVP-Empfehlung**:
   - Top 2-3 Contexts für MVP-Scope
   - Begründung basierend auf Unabhängigkeit, Komplexität, Geschäftswert

---

**Erstellt**: 2026-04-17  
**Für**: WGV ICIS Modernisierungs-Workshop Tag 1  
**Referenz**: `context/architektur_schaubild_icis_gesamt.md`, `context/icis_oracle_forms_architektur.md`
