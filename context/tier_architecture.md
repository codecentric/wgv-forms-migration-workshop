# 3-Tier-Architektur Konzept - Interpretation

**Quelle-Diagramm**: `diagrams/tier_architecture.svg`  
**Interpretation erstellt**: 2026-04-16  
**Typ**: Konzeptionelle Referenz (keine Metadaten vorhanden)

---

## ⚠️ Wichtiger Hinweis

Dieses Diagramm enthält **keine Metadaten** (kein Datum, kein Autor, keine Versionsnummer). Es sollte daher als **konzeptionelle Referenz** und **Architektur-Muster-Erklärung** verstanden werden, nicht als detaillierte Beschreibung des aktuellen ICIS-Systemzustands.

**Zweck**: Vermittlung des grundlegenden 3-Tier-Architekturkonzepts im Oracle Forms Kontext

---

## Überblick

Dieses Diagramm illustriert das klassische **3-Tier-Architektur-Muster** (auch: "Multi-Tier Architecture" oder "n-Tier Architecture"), das typischerweise in Oracle Forms-Anwendungen zum Einsatz kommt. Die Architektur trennt eine Anwendung in drei logische und physische Schichten: **Präsentation** (Client), **Geschäftslogik** (Middle-Tier), und **Datenhaltung** (Database).

Dieses Muster war über Jahrzehnte der de-facto Standard für Enterprise-Anwendungen und bildet die Grundlage für das Verständnis der ICIS-Architektur.

---

## Die drei Tiers im Detail

### Client-Tier (Präsentationsschicht)

**Zweck**: Benutzerinteraktion und Darstellung

**Komponenten im Diagramm**:

1. **Java-Applet**: 
   - Client-seitige Java-Anwendung im Browser
   - Kann PJC (Pluggable Java Components) enthalten
   - Webutil für erweiterte Client-Funktionalität
   - Plugin-Entwicklungen für kundenspezifische Erweiterungen

2. **Forms-Applet**: 
   - Oracle Forms JInitiator oder Java Plugin
   - Rendert Oracle Forms-UI im Browser

3. **Report-Browser**: 
   - Client zum Anzeigen von Oracle Reports

4. **Java**: 
   - Standalone Java-Clients oder Rich Clients

5. **HTML**: 
   - Web-basierte Clients (Browser)

**Charakteristik**: "Thin Client" oder "Rich Client" je nach Implementierung

---

### Middle-Tier (Anwendungslogik-Schicht)

**Zweck**: Geschäftslogik, Session-Management, Request-Verarbeitung

**Komponenten im Diagramm**:

1. **FMB (Forms Module Binary)**:
   - Kompilierte Oracle Forms-Definitionen
   - Unterkomponenten:
     - **Canvas**: Layout-Definitionen für Bildschirme
     - **Data Block**: Datenblock-Definitionen (Tabellen-Zuordnungen)
     - **Trigger**: Event-Handler (WHEN-NEW-FORM-INSTANCE, etc.)
     - **Program Units**: PL/SQL-Prozeduren und Funktionen in Forms
     - **LOVs (List of Values)**: Auswahllisten-Definitionen

2. **Reports**: 
   - Oracle Reports-Definitionen für Berichte und Dokumente

3. **Java**: 
   - Java-basierte Geschäftslogik (z.B. in ICIS+ über Spring)

4. **Web-Service**: 
   - SOAP oder RESTful Web Services für externe Integrationen

**Kommunikationsprotokoll**: JDBC (Java Database Connectivity) zur Datenbank

---

### Database-Tier (Datenhaltungsschicht)

**Zweck**: Persistente Datenspeicherung und datennahe Geschäftslogik

**Komponenten im Diagramm**:

1. **MMB**: 
   - Möglicherweise "Menu Module Binary" (Oracle Forms Menü-Definitionen)

2. **PL/L** (vermutlich PL/SQL):
   - Stored Procedures, Functions, Packages
   - Geschäftslogik auf Datenbankebene
   - **Zentral für ICIS**: Service-Stored Procedures bleiben auch in modernisierter Architektur erhalten

3. **Views**: 
   - Datenbank-Views für Abstraktion und Sicherheit

4. **Weitere vertikale Komponenten**:
   - Vermutlich: Jobs, Trigger, Sequences, etc.
   - Datenbank-interne Logik

**Technologie**: Oracle Database (im ICIS-Kontext)

---

## Architektur-Prinzipien

### Separation of Concerns

Jede Schicht hat eine klare Verantwortlichkeit:
- **Client**: Nur Präsentation und Benutzerinteraktion
- **Middle-Tier**: Geschäftslogik, Validierung, Orchestrierung
- **Database**: Datenhaltung und datennahe Logik

### Vorteile der 3-Tier-Architektur

✅ **Skalierbarkeit**: Middle-Tier kann horizontal skaliert werden (mehrere Application Server)  
✅ **Wartbarkeit**: Änderungen in einer Schicht beeinflussen andere Schichten minimal  
✅ **Sicherheit**: Database-Tier ist nicht direkt vom Client erreichbar  
✅ **Wiederverwendbarkeit**: Geschäftslogik im Middle-Tier kann von verschiedenen Clients genutzt werden  
✅ **Deployment-Flexibilität**: Tiers können auf unterschiedlichen Servern deployt werden

### Herausforderungen

⚠️ **Komplexität**: Mehr Schichten = mehr Komponenten zu managen  
⚠️ **Netzwerk-Latenz**: Kommunikation zwischen Tiers kann Performance beeinflussen  
⚠️ **Debugging**: Fehler können über mehrere Tiers verteilt sein  

---

## Relevanz für ICIS-Modernisierung

### Was bleibt konzeptionell erhalten?

Das **3-Tier-Prinzip** bleibt auch in der modernisierten Architektur bestehen, nur mit anderen Technologien:

| Tier | Legacy (Forms) | ICIS+ (Modern) | Geplante Modernisierung |
|------|----------------|----------------|-------------------------|
| **Client** | Forms-Applet, Java-Applet | Vaadin (Browser), Sencha (Mobile) | React/Angular (SPA) |
| **Middle** | Forms Server (.fmb) | Spring Framework (Java) | Spring Boot + Microservices |
| **Database** | PL/SQL Stored Procedures | PL/SQL + JPA | PL/SQL (bleibt) + REST-API-Schicht |

### Architektur-Evolution verstehen

Dieses Diagramm hilft, die **Evolution von ICIS** zu verstehen:

1. **Phase 1 (Legacy)**: Oracle Forms 3-Tier (dieses Diagramm)
2. **Phase 2 (ICIS+)**: Java/Vaadin 3-Tier mit PL/SQL-Backend
3. **Phase 3 (Geplant)**: React/Angular + Spring Boot + PL/SQL (weiterhin 3-Tier!)

**Erkenntnis**: Die **Tier-Struktur bleibt**, nur die **Technologien in den Tiers ändern sich**.

---

## Workshop-Relevanz

### Tag 1: Domäne erkennen & ICIS-System Verständnis

**Nutzen dieses Diagramms**:
- Erklärung des 3-Tier-Konzepts für Nicht-Techniker
- Gemeinsames Vokabular schaffen ("Was meinen wir mit 'Middle-Tier'?")
- Verständnis, dass ICIS-Klassik bereits eine mehrschichtige Architektur hat

**Diskussionsfragen**:
- "Wo in dieser Architektur liegt aktuell Ihre Geschäftslogik?" (Antwort: Sowohl Middle-Tier als auch Database-Tier)
- "Welche Tier-Grenzen könnten auch Domain-Grenzen sein?"

### Tag 2: Technische Validierung & Architektur

**Nutzen dieses Diagramms**:
- Basis für Diskussion: "Welche Tier-Komponenten können wiederverwendet werden?"
- Deployment-Ansätze: "Wie deployen wir die neuen Tiers? (Docker/Kubernetes)"
- Integration Layer: "Wie kommunizieren die neuen Tiers miteinander?"

**Architektur-Entscheidungen**:
- Bleibt die 3-Tier-Architektur oder gehen wir zu Microservices (n-Tier)?
- Wird die Database-Tier-Logik (PL/SQL) in den Middle-Tier verschoben?

### Tag 3: Frontend Technology & AI-Driven Development

**Nutzen dieses Diagramms**:
- Verständnis: "Wir ersetzen nur den Client-Tier (Oracle Forms → React/Angular)"
- Middle-Tier und Database-Tier bleiben konzeptionell gleich
- AI-Features sind eine Erweiterung des Client-Tiers (Conversational UI)

---

## Verbindung zu anderen Dokumenten

**Verwandte konzeptionelle Dokumente**:
- Dieses Diagramm ist **allgemein**, die folgenden sind **ICIS-spezifisch**:

**Konkrete ICIS-Architekturen**:
- `context/icis_oracle_forms_architektur.md`: Detaillierte Oracle Forms 3-Tier-Architektur (ICIS-Klassik)
- `context/icis_plus_jee_architekture.md`: ICIS+ JEE-Architektur (Feb 2021, Vaadin/Spring)
- `context/architektur_schaubild_icis_gesamt.md`: Gesamtsystem-Architektur (Mai 2022, inkl. externer Integrationen)

**Empfehlung**: 
1. Beginne mit diesem Diagramm (Konzept verstehen)
2. Dann zu konkreten ICIS-Architekturen (Ist-Zustand)
3. Dann zu Modernisierungsstrategie (Soll-Zustand)

---

## Zusammenfassung

Dieses Diagramm ist eine **pädagogische Referenz** für das 3-Tier-Architektur-Muster im Oracle Forms Kontext. Es zeigt:

- ✅ **Klare Trennung** der Verantwortlichkeiten (Client, Middle, Database)
- ✅ **Komponenten** typischer Oracle Forms-Anwendungen (FMB, PL/SQL, Applets)
- ✅ **Kommunikationswege** zwischen den Tiers (JDBC)

**Für den Workshop**: Nutzen Sie es als **Ausgangspunkt für Diskussionen** über Architektur-Prinzipien, nicht als genaue Beschreibung des aktuellen ICIS-Zustands. Die konkreten ICIS-Architekturen sind in den anderen Diagrammen dokumentiert.

---

**Erstellt**: 2026-04-16  
**Autor**: Sócrates Ponce (codecentric)  
**Zweck**: Konzeptionelle Referenz für 3-Tier-Architektur im WGV ICIS Modernisierungs-Workshop  
**Version**: 1.0
