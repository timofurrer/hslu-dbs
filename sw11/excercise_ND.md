# Exercises ND: NoSQL Datenbanken

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3714656_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium

-> Lesen Sie Kapitel 7 im Buch Meier & Kaufmann (2016)

-> Lesen Sie das Kapitel 1 aus Edlich (2011)

## 2. Review Questions

### Aus welchen Gründen entstand die NoSQL-Bewegung?

Durch den Wunsch auch grössere Datenmengen verarbeiten zu können (ausgelöst durch das Web 2.0 ab der Jahrtausendwende). SQL Datenbanken sind auf Integrität ausgelegt, bei sehr grossen Datenmengen ist dies aber nicht immer zwingend, dadurch entstanden NoSQL Datenbanken.

### Was ist der Unterschied zwischen SQL und NoSQL?

NoSQL Datenbanken bieten (meist) keine SQL Schnittstelle und bei NoSQL ist die Datenintegrität nicht immer gegeben.

### Welche Vorteile hat SQL gegenüber NoSQL?

SQL Datenbanken haben den Vorteil dass sie die sehr mächtige Abfragesprache SQL anbieten. Mit dieser Sprache kann man sehr simpel beschreiben welches Resultat man gerne hättet, ohne zu definieren wie man zum Resultat gelangt. Somit ist die Sprache für Entwickler sowie für Leute mit wenig Kentnissen schnell verständlich. Zusätzlich ist bei den SQL Datenbanken die Konsistenz und Integrität der Daten immer gewährt.

### Welche Vorteile hat NoSQL gegenüber SQL?

NoSQL Datenbanken sind sehr gut Skalierbar und aus diesem Grund auch sehr Performant bei sehr grossen Datenmengen.

### Was heisst Schemafreiheit?

Schemafreiheit bedeutet, dass eine Datenbank kein Schema enthält, welches die Daten in Tabellen "gruppiert/zuweist". 

### In welchen Szenarien setzt man optimal auf welche der beiden Varianten?

Wenn die Datenmengen nicht zu gross sind und insgesammt sehr strukturiert (einfach in ein Schema zu packen), ist eine SQL Datenbank zu bevorzugen. Bei grossen und eher unstrukturierten Datenmengen sollte auf NoSQL gesetzt werden. Ebenfalls kommt es noch auf die Anforderungen an die Integrität der Daten an -> Hohe Integrität -> SQL

### Welche NoSQL-Systeme gibt es?

* Schlüssel-Wert-Datenbanken
* Spaltenfamilien-Datenbanken
* Dokument-Datenbanken
* Graph-Datenbanken

### Wie wird Map‐Reduce mit CouchDB umgesetzt? Wie wird dabei auf heterogene Schemata (unterschiedliche Dokumentstrukturen) eingegangen? Wie kann dies auf mehrere Rechner verteilt werden?

ToDo

### Welche Mehrwert bieten Dokumentdatenbanken gegenüber von Spalten-Wert-Datenbanken? 

Die Datensätze haben eine detailiertere Struktur und sind somit an einem Ort gespeichert, was optimal für die Abfrage-Performance von horizontal skalierten Systemen ist.

### Welchem Mehrwert bieten Spaltenfamilien-Datenbanken gegenüber Spalten-Wert-Datenbanken? 

Physisch können Spaltenfamilien gruppiert werden, was ebenfalls wieder der Performance zu gute kommt.

### Welchem Mehrwert bieten Dokumentdatenbanken gegenüber von Spaltenfamilien-Datenbanken? 

Die Daten werden Schemafrei gespeichert, somit ist es sehr flexibel wenn viele Datensätze mit unterschiedlichen Attributen existieren. Der eine Datensatz kann eine E-Mail enthalten, der andere z.B keine E-Mail dafür 3 verschiedene Rufnummern.

### Welchen Mehrwert bieten Spaltenfamilien-Datenbanken gegenüber von Dokument-Datenbanken?

Spaltenfamilien-Datenbanken können die Einzelwerte verteilt abspeichern mit einer sehr schnellen Zugriffszeit. Deshalb sind sie geeignet für grosse Datenmengen mit Lesezugriffoptimierung.
