Folgenden Teilnehmerkreis haben wir uns für die Tage vorgestellt. Teilnehmer in Klammern sind optional, da es vielleicht für sie interessant sein kann, oder wir nicht genau wissen, ob die anderen Rollen alles bei Ihnen abdecken was wir uns vorstellen. Ich hoffe mit der Agenda unten wird es klarer:
Tag 1:
Nutzer
Architekten
(eventueller zukünftiger Product Owner / Projektleiter)
(ein Developer, der den Architekten bei tiefergehenden technischen Fragen unterstützen könnte)

Tag 2:
Architekten
Developer
(Wenn die Leute neugierig sind, auch Nutzer, da wir auf AI eingehen werden und so vielleicht noch Möglichkeiten klarer werden. Es wird aber eher technisch)

Tag 3:
Developer
Architekten (für den Frontend Teil am Anfang und länger, wenn sie AI-Driven Development lernen wollen)

Hier dann nochmal einen kurzen Umriss der Agenda die wir uns aktuell vorstellen:

Tag 1:
Wir versuchen möglichst viel Wissen aufzunehmen. An dem Tag wird viel Input von Ihrer Seite benötigt:
Domäne erkennen (Wir stellen Fragen an das System und erstellen dadurch eine Domänenkarte)
Analyse von Masken, ihrem Nutzen und wie sie funktionieren (stichprobenartig)
Anwendungskonzept (UI/UX) Skizze:
- Analyse bestehender User Journeys in Oracle Forms (Schwerpunkt: Power User Workflows)
- Identifikation von Pain Points und Ineffizienzen in der aktuellen Benutzerführung
- Diskussion: Hybrides UI-Konzept (Chatbot-Elemente vs. Formular-basierte Eingabe)
  - Wann macht Conversational UI Sinn?
  - Wo sind klassische Forms effizienter?
- Erarbeitung von UI-Patterns für häufige Anwendungsfälle:
  - Datenerfassung (z.B. Vertragsabschluss)
  - Datenanpassung (z.B. Adressänderung, Deckungssumme)
  - Lesezugriffe/Recherche
- Anforderungen an Responsiveness und Barrierefreiheit
- Skizzierung von 2-3 exemplarischen Screen-Mockups für priorisierte Masken

- Feature/Prioritäten Liste
  Diskussion zum Thema AI Features

Tag 2:
Hier gibt es eine Mischung aus technischen Details klären und wir erarbeiten ein Architekturkonzept
Verschärfung des Scopes:
- Priorisierung der 900 Masken:
  - Welche Masken haben höchsten Business Value?
  - Welche sind am häufigsten genutzt?
  - Welche sind technisch am einfachsten zu migrieren? (Quick Wins)
- Definition der MVP-Funktionalität für Phase 1
- Abgrenzung: Was bleibt unverändert? (Backend/PL/SQL) vs. Was wird modernisiert? (Frontend)
- Entscheidung: Welche Vaadin-Komponenten aus ICIS+ können/sollen wiederverwendert werden?
- Festlegung: Welche Masken eignen sich für APEX Low-Code vs. Custom Development?
- Identifikation von Prozessen, die durch AI-Agents ersetzt/optimiert werden können
- Klärung der Integrationspunkte zwischen Alt- und Neusystem während der Migration
- Definition von "Done" Kriterien für eine migrierte Maske
Integration von AI ins System, wie geht das und was gilt es zu beachten (MCP/ Integration ins System / RBAC / Hosting...) (1-2h)
Vorstellung bestehender Services / Stored Procedures
Entwurf eines möglichen Architekturdiagramms (Frontend / Integrationsschicht)

Tag 3:
Hier gibt es einen kurzen Exkurs zum Thema Frontend Frameworks, der Großteil wird aber ein Workshop zum Thema AI-Driven Development
Einordnung von Frontend Frameworks
Großteil des Tages: AI-Driven Development Workshop
Basics
Anwendung am Oracle Masken Beispiel
