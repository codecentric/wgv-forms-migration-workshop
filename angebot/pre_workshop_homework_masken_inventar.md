# Vorbereitung Workshop Tag 1 - Masken-Inventar

**An**: WGV Workshop-Teilnehmer  
**Von**: codecentric Team  
**Betreff**: Vorbereitung für Maskenanalyse (28. April 2026)  
**Zeitaufwand**: Ca. 2-3 Stunden

---

## Zielsetzung

Um unsere gemeinsame Workshop-Zeit optimal zu nutzen, bitten wir Sie, **vor dem Workshop** eine Übersicht Ihrer Oracle Forms Masken zu erstellen. Diese Basis-Informationen ermöglichen es uns, am Workshop-Tag direkt in die **Analyse und Priorisierung** einzusteigen, statt Zeit mit Datenerfassung zu verbringen.

---

## Was wir benötigen

Eine **Excel-Liste** mit folgenden Informationen für Ihre ~900 Oracle Forms Masken:

### Pflichtfelder

| Spalte | Beschreibung | Beispiel | Hinweise |
|--------|--------------|----------|----------|
| **Mask ID** | Eindeutige Kennung der Maske | `VERT_001`, `M12345` | Technische ID aus Oracle Forms |
| **Mask Name** | Funktionale Bezeichnung | `Vertragsabschluss Neugeschäft` | Name, den Sachbearbeiter kennen |
| **Fachlicher Bereich** | Zuordnung zur Domäne | `Vertragsverwaltung`, `Schadenbearbeitung`, `Kundenverwaltung` | Welche Fachabteilung nutzt diese Maske? |
| **Nutzungshäufigkeit** | Wie oft wird die Maske genutzt? | `Täglich`, `Wöchentlich`, `Monatlich`, `Selten` | Grobe Einschätzung reicht |
| **Anzahl Nutzer** | Wie viele Sachbearbeiter nutzen die Maske? | `~50`, `5-10`, `>100` | Schätzung ist ausreichend |
| **Komplexität** | Ihre subjektive Einschätzung | `Low`, `Medium`, `High` | Siehe Erklärung unten |

### Optionale Felder

| Spalte | Beschreibung | Beispiel |
|--------|--------------|----------|
| **Notizen** | Besonderheiten, Abhängigkeiten | `Integriert mit SAP`, `Legacy-Code`, `Performance-Probleme` |
| **Anzahl Felder** | Grobe Anzahl der Eingabefelder | `~10`, `50+`, `<5` |
| **Externe Systeme** | Verbindungen zu anderen Systemen | `SAP`, `COR Life`, `DMS`, `GDV` |

---

## Komplexitäts-Einschätzung: Low / Medium / High

**Frage**: "Wie komplex ist diese Maske aus fachlicher und technischer Sicht?"

### Low (Einfach)

**Charakteristik**:
- Wenige Felder (~5-15)
- Einfache Business-Logik
- Ein einzelnes Datenmodell (z.B. nur Kunde, nur Adresse)
- Keine oder minimale Integration mit externen Systemen
- Standardmäßige CRUD-Operationen (Create, Read, Update, Delete)

**Beispiele**:
- Einfache Adressänderung
- Kundensuche
- Statusabfrage

---

### Medium (Mittel)

**Charakteristik**:
- Mittlere Anzahl Felder (~15-40)
- Komplexere Business-Regeln (z.B. Berechnungen, Validierungen)
- Mehrere verknüpfte Datenmodelle (z.B. Kunde + Vertrag)
- 1-2 externe Integrationen
- Mehrstufige Workflows

**Beispiele**:
- Vertragsabschluss
- Schadenanlage
- Tarifberechnung

---

### High (Komplex)

**Charakteristik**:
- Viele Felder (>40)
- Sehr komplexe Geschäftslogik
- Viele verknüpfte Datenmodelle (Kunde + Vertrag + Schaden + Dokumente + ...)
- Mehrere externe Systeme (SAP, COR Life, GDV, DMS)
- Komplexe Workflows mit vielen Entscheidungspunkten
- Spezialwissen erforderlich (nur 1-2 Experten können die Maske bedienen)

**Beispiele**:
- Komplexe Schadensbearbeitung mit Gutachten
- Lebensversicherungs-Policierung
- Multi-Sparten-Verträge

---

## Template: Excel-Vorlage

**Bitte verwenden Sie die beigefügte Excel-Vorlage**: `WGV_Masken_Inventar_Template.xlsx`

Die Vorlage enthält:
- ✅ Alle Pflichtspalten mit Beispiel-Daten
- ✅ Dropdowns für Nutzungshäufigkeit und Komplexität
- ✅ Kommentare/Hinweise in den Spaltenüberschriften
- ✅ Eine Beispielzeile zur Orientierung

---

## Hinweise zur Datenqualität

**Wichtig**:
- ✅ **Schätzungen sind vollkommen ausreichend!** Sie müssen nicht exakt zählen.
- ✅ **Bei Unsicherheit**: Markieren Sie die Zeile (z.B. gelb hinterlegen) und wir klären es im Workshop.
- ✅ **Nicht alle 900 Masken müssen perfekt erfasst sein**. Wenn Sie 80-90% schaffen, ist das großartig.
- ✅ **Fehlende Daten**: Lassen Sie Zellen leer, wenn Sie keine Info haben. Besser leer als geraten.

**Ziel ist nicht Perfektion, sondern eine solide Datenbasis für den Workshop!**

---

## Wie wir die Daten nutzen werden

Am Workshop-Tag (28. April 2026) verwenden wir Ihre Daten für:

1. **Quick Filtering** (~20min): Wir filtern die 900 Masken auf ~50-100 Kandidaten für die Modernisierung
   - Beispiel: "Zeige nur Masken, die täglich genutzt werden und >10 Nutzer haben"

2. **Pattern-Based Clustering** (~30min): Wir gruppieren Masken nach Fachbereich und Komplexität
   - Beispiel: "Welche Masken sind 'Low Complexity' im Bereich Kundenverwaltung?"

3. **Priorisierung** (~20min): Wir bewerten 10-15 repräsentative Masken im Detail
   - Beispiel: RICE-Scoring (Reach × Impact × Confidence / Effort)

4. **MVP-Auswahl** (~15min): Gemeinsame Entscheidung für 3-5 Masken für Phase 1

**Ohne diese Vorarbeit** würden wir 60-90 Minuten Workshop-Zeit für Datenerfassung verlieren!

---

## Zeitaufwand & Verantwortlichkeiten

**Geschätzter Aufwand**:
- **Kleine Teams** (1-2 Personen): 2-3 Stunden
- **Größere Teams** (3-5 Personen): 1-2 Stunden (aufgeteilt)

**Empfohlene Aufteilung**:
- **IT/Architekten**: Mask ID, Fachlicher Bereich, Externe Systeme
- **Fachbereich/Nutzer**: Nutzungshäufigkeit, Anzahl Nutzer, Komplexität
- **Gemeinsam**: Review und Qualitätssicherung

**Tipp**: Nutzen Sie vorhandene Dokumentation (falls verfügbar):
- Bestehende Masken-Listen aus ICIS-Doku
- Deployment-Dokumentation (welche Masken werden deployed?)
- Analytics/Logs (Nutzungsdaten)

---

## Deadline

**Bitte senden Sie uns die Excel-Liste bis spätestens**:
📅 **25. April 2026, 17:00 Uhr**

**Email an**: [workshop@codecentric.de]  
**Betreff**: WGV Masken-Inventar - Workshop-Vorbereitung

**Fragen?** Melden Sie sich gerne bei uns!

---

## Warum diese Vorbereitung wichtig ist

> **Ohne Vorbereitung**:
> - 90 Minuten Datenerfassung im Workshop
> - Weniger Zeit für Analyse und Entscheidungen
> - Oberflächliche Diskussionen
> 
> **Mit Vorbereitung**:
> - ✅ Direkt in Analyse einsteigen
> - ✅ Tiefere Diskussionen über Priorisierung
> - ✅ Bessere Entscheidungsgrundlage für MVP-Auswahl
> - ✅ Mehr Workshop-Zeit für strategische Fragen

Ihre Vorarbeit macht den Workshop **3x effektiver**!

---

## Anhang: Häufige Fragen (FAQ)

**F: Was, wenn wir nicht alle 900 Masken erfassen können?**  
A: Fokussieren Sie sich auf die **häufig genutzten Masken** (täglich/wöchentlich). Selten genutzte Masken können wir im Workshop überspringen.

**F: Wir haben keine genauen Nutzungsdaten. Was tun?**  
A: Schätzen Sie basierend auf Erfahrung. "Täglich", "Wöchentlich", "Monatlich", "Selten" reicht völlig aus.

**F: Wie detailliert müssen die Notizen sein?**  
A: Kurz und prägnant. Beispiele: "SAP-Integration", "Performance-Problem", "Nur 1 Experte kennt sich aus", "Legacy-Code".

**F: Können wir die Vorlage anpassen?**  
A: Ja! Fügen Sie gerne eigene Spalten hinzu (z.B. "Zuständiger Entwickler", "Letzte Änderung"). Die Pflichtspalten sollten aber erhalten bleiben.

**F: Was ist mit ICIS+ Masken (Vaadin)?**  
A: Falls Sie ICIS+ Masken separat erfassen möchten, gerne! Markieren Sie diese z.B. in einer eigenen Spalte "System: ICIS-Klassik / ICIS+".

---

**Vielen Dank für Ihre Vorbereitung!**

Wir freuen uns auf einen produktiven Workshop am 28. April 2026.

Bei Fragen stehen wir Ihnen jederzeit zur Verfügung.

**Ihr codecentric Team**

---

**Anhänge**:
- 📎 `WGV_Masken_Inventar_Template.xlsx` (Excel-Vorlage)
