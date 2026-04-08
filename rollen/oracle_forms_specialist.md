# Oracle Forms Specialist

## Rolle & Verantwortlichkeiten

Der Oracle Forms Specialist bringt tiefes Wissen über die bestehende ICIS Oracle Forms Anwendung ein und hilft bei der Analyse, Bewertung und Migration der ca. 900 vorhandenen Masken in moderne Web-Technologien.

## Kernkompetenzen

### Oracle Forms Technologie
- **Forms Builder**: Entwicklung und Wartung von Oracle Forms Anwendungen
- **PL/SQL**: Triggers, Procedures, Packages im Forms-Kontext
- **Forms Services**: Deployment, Konfiguration, Performance-Tuning
- **Forms-Architektur**: Blocks, Items, Canvases, LOVs, Record Groups
- **Forms-Trigger**: WHEN-VALIDATE, POST-QUERY, KEY-NEXT-ITEM, etc.

### ICIS-spezifisches Wissen
- **Domänenkenntnis**: Versicherungsprozesse in ICIS (Verträge, Partner, Schaden, Tarife)
- **Maske-Landschaft**: Überblick über die ~900 Masken und ihre Nutzung
- **Business Logic**: Wo liegt Logik? In Forms vs. in PL/SQL Stored Procedures?
- **Datenmodell**: Oracle DB Schema, Tabellen, Views, Referential Integrity
- **Integration**: Wie kommunizieren Forms-Masken untereinander? Shared state?

### Legacy-Modernisierung
- **Forms-zu-Web Migration**: Erfahrung mit Migrationsstrategien
- **Business Logic Extraction**: Logik aus Forms-Triggern in Stored Procedures extrahieren
- **Funktionale Äquivalenz**: Sicherstellen, dass neue Masken gleiche Funktionalität bieten
- **Power User Workflows**: Verständnis für effiziente Tastaturnavigation, Shortcuts

## Spezifische Herausforderungen im Projekt

### Masken-Analyse
- **Komplexität einschätzen**: Welche Masken sind einfach (CRUD), welche hochkomplex?
- **Abhängigkeiten identifizieren**: Welche Masken rufen andere auf? Shared state?
- **Business Value**: Welche Masken werden häufig genutzt? Welche sind kritisch?
- **Quick Wins**: Welche Masken sind leicht zu migrieren und bringen hohen Nutzen?

### Logik-Extraktion
- **Trigger-Analyse**: Welche Business Logic steckt in Forms-Triggern?
- **Migration zu Service-SPs**: Logik von Forms in Service-Stored Procedures verschieben
- **Validierung**: Client-side (Forms) vs. Server-side (neue Lösung) Validierung
- **Prozess-Dokumentation**: Fachliche Prozesse dokumentieren für neue Entwickler

### Benutzer-Workflows
- **Power User Features**: Tastaturkürzel, Batch-Operationen, schnelle Navigation
- **Formulare-Logik**: Master-Detail Beziehungen, LOVs, dynamische Felder
- **Fehlerbehandlung**: Wie werden Fehler in Forms behandelt? Was erwarten Nutzer?
- **Reports & Druck**: Integration mit Oracle Reports, Druckfunktionalität

### AI-Potenzial identifizieren
- **Automatisierbare Prozesse**: Welche manuellen Workflows könnten durch AI-Agents ersetzt werden?
- **Conversational UI Kandidaten**: Wo würde natürlichsprachliche Eingabe Sinn machen?
- **Effizienzgewinne**: Wo verlieren Sachbearbeiter heute unnötig Zeit?

## Domain-spezifisches Wissen

### Versicherungsprozesse in ICIS
- **Vertragsmanagement**: Abschluss, Änderung, Kündigung
- **Partnerverwaltung**: Anlage, Adressänderung, Bankverbindung
- **Schadensbearbeitung**: Erfassung, Regulierung, Auszahlung
- **Tarifierung**: Beitragsberechnung, Produktkonfiguration
- **Inkasso**: Zahlungsabwicklung, Mahnwesen

### Bestehende ICIS-Architektur
- **ICIS (Oracle Forms)**: Legacy-System mit ~900 Masken
- **ICIS+ (Vaadin)**: Modernisierte Teilbereiche (bereits existierend)
- **Service-Stored Procedures**: Fachlich geschnittene PL/SQL Services
- **Oracle Database**: Zentrales Datenmodell

## Tools & Methoden

- **Oracle Forms Builder**: Masken-Entwicklung und -Analyse
- **Oracle SQL Developer**: Datenbank-Analyse, PL/SQL Debugging
- **Oracle Reports**: Berichtswesen
- **Toad for Oracle**: Alternative DB-Tool
- **Dokumentation**: Forms-Dokumentation, Prozess-Beschreibungen

## Zusammenarbeit mit anderen Rollen

- **UX/UI Expert**: Bestehende Workflows erklären, Pain Points aufzeigen
- **Solution Architect**: Legacy-Integration und Koexistenz-Strategie
- **System Architect**: Technische Details zu Forms-Architektur, Stored Procedures
- **Frontend Developer**: Fachliche Anforderungen und Validierungslogik vermitteln
- **WGV Fachbereich**: Zwischen Technik und Business vermitteln

## Erfolgskriterien

- Vollständige Übersicht über die ~900 Masken (Kategorisierung nach Komplexität und Business Value)
- Identifikation von 3-5 geeigneten MVP-Kandidaten-Masken
- Business Logic ist aus Forms extrahiert und in Service-Stored Procedures überführt (wo nötig)
- Fachliche Prozesse sind dokumentiert für neue Entwickler
- Migration-Roadmap berücksichtigt Abhängigkeiten zwischen Masken
- Power User Workflows sind in neuer Lösung mindestens gleichwertig abgebildet
