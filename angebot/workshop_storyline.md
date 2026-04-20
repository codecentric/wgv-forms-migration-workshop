# Workshop Storyline - WGV ICIS Modernisierung

## Primäre Storyline (für Slides - SCR 4-Punkt-Struktur)

### S - Situation: Wo wir stehen
WGV betreibt **900 Oracle Forms Masken**, die zentrale Versicherungsprozesse steuern (Vertrag, Partner, Schaden); **bewährte PL/SQL-Geschäftslogik** in Oracle Database bildet komplexe Domänenregeln ab, die über Jahrzehnte entwickelt wurden

### C - Complication: Was sich ändert / Das Problem
**Oracle Forms Support endet Dezember 2026** (verifiziert); Legacy-Technologie-Risiken: typischerweise schrumpfende Expertise bei 30+ Jahre alten Technologien (Hypothese - mit WGV zu validieren); die aktuelle Technologieposition ist **unhaltbar und zunehmend risikoreich**

### R1 - Resolution (WAS): Die strategische Antwort
**UI-Layer modernisieren** (React/Angular) mit **KI-gestützter Entwicklung** (Komprimierung 5-7 Jahre → 2-3 Jahre) bei gleichzeitiger **Bewahrung des PL/SQL-Backends**; **Technologiewahlfreiheit** für Frontend und Cloud-Deployment gewinnen

### R2 - Resolution (WIE): Die Ausführungsmethode
Deployment via **Strangler-Fig-Pattern** (inkrementell, risikoarm) mit **Koexistenz** (Forms + ICIS+ + neu); ermöglicht **selektive Transformation** (komplexe Masken → moderne Formulare, einfache Masken → KI-Agenten)

---

## 3-Punkt-Zusammenfassung (Option C - für Anchor Slide)

Komprimierte Version für wiederkehrende Referenz während des Workshops:

### 1. Business Imperative
Oracle Forms Support Sunset (Dezember 2026, verifiziert) + Legacy-Technologie-Risiken (typischerweise schrumpfende Expertise bei 30+ Jahre alter Technologie - Hypothese) = **unhaltbare Technologieposition**, die sofortiges Handeln erfordert

### 2. Strategische Transformation
Modernisierung von UI/UX mit Technologiewahlfreiheit (React/Angular) und Cloud-Portabilität bei gleichzeitiger **Bewahrung der PL/SQL-Geschäftslogik**; KI-gestützte Entwicklung macht die Skalierung von 900 Masken **wirtschaftlich realisierbar** (Komprimierung von 5-7 Jahren → 2-3 Jahre)

### 3. Risikogesteuerte Ausführung
Strangler-Fig-Pattern (Koexistenz + inkrementelle Ablösung) vermeidet Big-Bang-Risiken, ermöglicht kontinuierliche Wertlieferung und erlaubt **selektive Transformation** (einige Masken → KI-Agenten, komplexe Masken → moderne Formulare)

---

## Warum codecentric?

Nachgewiesene Expertise in Legacy-zu-Modern-Migrationen, KI-gestützter Entwicklungsmethodik und Versicherungsdomänen-Wissen - erforderlich, um diese Komplexität zu bewältigen und innerhalb der 2026-Deadline zu liefern.

---

## Alternative Phrasierungen

### Option A: Business-Driven (5 Punkte)

1. **Burning Platform**: Oracle Forms Premier Support endet Dezember 2026; Extended Support ist kostspielig mit begrenzter Roadmap - Handlung JETZT erforderlich

2. **Unhaltbare Position**: 900 Forms-Masken mit Support-Ende Dezember 2026 (verifiziert); Legacy-Technologie-Risiko: typischerweise schrumpfende Expertise bei 30+ Jahre alter Technologie (Hypothese - mit WGV zu validieren); technische Schulden steigen jährlich

3. **Strategische Chance**: Modernisierung ermöglicht bessere UX (hybride konversationelle + Formulare), mobilen Zugriff, Cloud-Deployment und Technologiewahlfreiheit - bei gleichzeitiger Bewahrung der PL/SQL-Geschäftslogik-Investition

4. **KI als Kraftmultiplikator**: KI-gestützte Entwicklung verwandelt eine unerschwinglich teure 5-7-Jahres-Migration in erreichbare 24-36 Monate - macht den Business Case tragfähig

5. **Risikogesteuertes Vorgehen**: Strangler-Fig-Pattern (inkrementelle Ablösung) vermeidet Big-Bang-Cutover-Risiko, ermöglicht kontinuierliche Wertlieferung und erlaubt Team-Upskilling parallel zur Migration

---

### Option B: Technical-Driven (5 Punkte)

1. **Deadline-Druck**: Oracle Fusion Middleware 12c Support-Sunset (Dez 2026) schafft Timeline-Dringlichkeit - Migration kann nicht verzögert werden

2. **Technologieschuld**: Oracle Forms sperrt WGV in veraltete UI-Technologie ein; Support endet Dezember 2026 (verifiziert); Legacy-Technologie-Risiko: typischerweise schrumpfende Expertise bei 30+ Jahre alter Technologie (Hypothese - mit WGV zu validieren); keine Roadmap für Forms-Modernisierung

3. **Strategische Entkopplung**: Frontend unabhängig modernisieren, um Cloud-Portabilität, Framework-Wahl und moderne UX zu gewinnen - bewährtes PL/SQL-Backend unverändert lassen

4. **Skalierungsherausforderung**: 900 Masken = mehrjähriger, mehrere Millionen Euro Aufwand bei traditioneller Geschwindigkeit; KI-gestützte Entwicklung komprimiert Timeline und Kosten um 60-70%

5. **Inkrementelle Transformation**: Strangler-Fig-Pattern verwaltet Risiko durch schrittweisen Rollout, Koexistenz (Forms + ICIS+ + neu) und validiert Architektur vor vollständiger Verpflichtung

---

## Workshop-Arc Alignment

| Workshop Tag | Storyline Point | Focus |
|--------------|-----------------|-------|
| **Tag 1** | Point 3 erforschen | Welche Masken? Welche transformieren? (Selektive Transformation) |
| **Tag 2** | Point 2 designen | Architektur für moderne UI + PL/SQL Backend (Strategische Transformation) |
| **Tag 3** | Point 2 beweisen | KI-gestützte Entwicklung macht es machbar (Wirtschaftliche Realisierbarkeit) |

---

## Referenzen

- **Strangler Fig Pattern**: Martin Fowler - Graduelle Migration statt Big Bang
- **Oracle Forms Migration Options**: Flynn Jones (dev.to) - APEX vs. Java vs. .NET Vergleich
- **Support Timeline**: Oracle Fusion Middleware 12c Premier Support bis Dezember 2026
