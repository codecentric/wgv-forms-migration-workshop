# Ausgangslage

ICIS ist eine Oracle-basierte Versicherungssoftware, die früher mal bei vielen Kunden eingesetzt worden ist \- mittlerweile wird diese aber in einem gemeinschaftlichen Konsortium von WGV, BGV und der Lippischen weiter entwickelt. codecentric hatte schon mal geholfen, ein Teil von ICIS durch neue Oberflächen ICIS+ zu modernisieren basierend auf Vaadin.

ICIS soll jetzt weiter modernisiert bzw. zukunftsfähig gemacht werden. In diesem Rahmen ist die Entscheidung getroffen worden, dass man die Oracle-DB und auch die Logik in PL-SQL behalten möchte. Dies muss in der neuen Zielarchitektur berücksichtigt werden.

Die PL/SQL-Geschätfslogik wird bereits heute als fachlich geschnittene Stored Procedures in Form von Services bereitgestellt. Diese bieten versicherungstechnische Prozesse wie “Vertrag abschließen” oder “Partneradresse ändern” an. Die Menge dieser Service-Stored Procedures wird von der WGV fortlaufend ergänzt, indem noch bestehende Logik aus den Oracle Forms Masken extrahiert wird. Dies ist ein bereits bei ICIS+ eingeübter Prozess.

# Zielbild

![][image1]

Der in der Darstellung rot eingerahmte Teil soll im Zuge der Modernisierung erstellt werden:

- Integrationsschicht: eine Schicht, die Backend-Funktionen für die verschiedenen Frontends zentral und standardisiert bereitstellt. Auch LLMs als Client der Schnittstellen muß vorgesehen werden.
- Frontend: Es sind Standard-Technologien für die Entwicklung der Frontends zu definieren.
- Modularisierung & Entwicklungsprozesse: Es soll ein modularisierter Ansatz (“Containerisierung”) verfolgt werden und die Zielumgebung sollte die Azure-Cloud sein. Als eine Möglichkeit wurde bereits “Kubernetes” von der WGV genannt.

# Rahmenbedingungen / Erwartungen

- Es sind recht komplexe, Oracle-Forms-basierte Masken vorhanden, die sukzessive abgelöst werden sollen. Insgesamt gibt es ca. 900 Masken.
- Für die Entwicklung der Frontends sollen AI-Tools genutzt werden, dies ist bei Technologie/Entwicklunsprozess zu berücksichtigen. Ziel ist es, die 900 Masken sehr effizient abzulösen.
- Zielumgebung ist Azure und Co Pilot ist vorhanden. Im Call wurde aber auch von der Möglichkeit gesprochen, Claude Code einzusetzen.
- Es ist auch der Entwicklungsprozess insgesamt inkl. der Containerisierung der Frontends zu berücksichtigen.
- Wichtig: die Masken werden nicht alle 1:1 abgelöst, sondern es ist fachlich zu prüfen, ob Teil der “alten” Prozesse nicht durch AI-Ansätze (Agents & Co) abgelöst bzw. anders gedacht werden können. Im Rahmen der Modernisierung soll daher auch die Automatisierung der fachlichen Prozesse vorangetrieben werden.
- Die Integrationsschicht soll eine REST-Schnittstelle zur Verfügung stellen. Hierbei ist zu berücksichtigen, dass die entstehenden Schnittstellen lange aktiv sein werden \- das erfordert u.a. ein Versionierungskonzept
- Bei der Benutzerführung im neuen Frontend strebt die WGV eine enge Verzahnung zwischen KI-Chatbot-artigen Elementen und Formular-GUIs an. Zum Beispiel soll der Sachbearbeiter eingeben können “Ändere die Deckungssumme auf X€” und die KI nimmt diese Änderung dann vor. Aber:
  - Jede Änderung soll vom Sachbearbeiter vorher noch einmal überprüft werden können
  - Gleichzeitig sind die Sachbearbeiter auch "schnell arbeitende Experten” und benötigen entsprechende “Power-User”-Funktionen
  - \=\> UX-Design wird im Projekt wichtig werden
- Als Frontend-Technolgien sind bei der WGV Vaadin, aber auch moderne Frameworks wie React und Angular bekannt. Für die Frontend-Technologien gelten folgende Erwartungen
  - Hinreichend weite Verbreitung, so dass die Erstellung von Masken durch KI möglich ist (viele LLM-Lernbeispiele im Netz)
  - Ausgewählte Vaadin-Teile aus ICIS+ sollen möglichst integriert werden können
  - Auch hier wird eine “langlebige Lösung” angestrebt, d.h. das allerneuste JavaScript-Framework, das gerade gehypt wird, sich aber noch nicht in größeren Projekten bewiesen hat, ist nicht die richtige Lösung.
- Für ganz einfache CRUD-Masken spricht die WGV auch von der Verwendung von [APEX](https://www.oracle.com/apex/), der von Oracle präferierten Technologie zur Oracle-Forms-Ablösung. APEX ist eine auf Web-Technolgien basierende Low-Code-Plattform von Oracle.

# Next Steps

- codecentric zeigt eine mögliche Vorgehensweise auf nach dem Prinzip “Ziel groß denken, aber klein starten”.
- Bei der Vorgehensweise in Phasen denken, z.B. “Architektur festlegen (Rahmen schaffen) \-\> AI-Tooling mit konkreten Masken ausprobieren (Pilot) \-\> Start der Umsetzung….
- Parallel sollten wir ein Vorgehen zur AI-Nutzung in den Fachprozessen darlegen, aber vielleicht in einem späteren Schritt.
