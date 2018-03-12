# Exercises S1: SQL Grundlagen

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3665910_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## Selbststudium
Lesen Sie Kapitel 3.1 – 3.3 aus dem Buch von Meier & Kaufmann (2016)

### Welche Benutzergruppen gibt es und wie interagieren sie mit der Datenbank?

* Datenarchitekt/in: Tabellen und Formate einheitlich festlegen und Daten beschreiben
* Datenbank-Spezialist/in: Tabellen installieren, kontrollieren und sicherstellen und Benutzerrechte vergeben
* Anwendungs-programmierer/in: Tabellen abfragen, verändern oder löschen
* Datenanalyst/in: Tabellen abfragen, auswerten und verändern

### Was ist der Unterschied zwischen mengenorientierten und relationalen Operatoren?

Mengenorientierte Operatoren:
* Vereinigung
* Durchschnitt
* Subtraktion
* Kartesisches Produkt

Relationale Operatoren:
* Projektion
* Selektion
* Verbund (Join)
* Division

### Wie ist der Zusammenhang von Kreuzprodukt und Division?

### Was ist der Zusammehang von mengenorientierten Abfragesprachen und der Relationenalgebra?

### Wie wird die Selektion in SQL umgesetzt?

### Wie wird die Projektion in SQL umgesetzt?

### Wie wird der Join in SQL umgesetzt?

### Wie zeigt sich die Eigenschaft von SQL, dass sie deskriptiv ist?

### Was bedeutet die Aussage, dass SQL relational vollständig ist?

## Zusammenhang Relationenalgebra und SQL Grundlagen

Für die folgenden Aufgaben, geben Sie die Lösung jeweils (1) als SQL-Code und (2) als mathematische Formel der Relationenalgebra an.
Die Beispiele beziehen sich auf die Uni-Datenbank. Sie können den SQL-Code auch auf dem Server ausprobieren (siehe Folien)

### Selektion - Welche Professoren haben Rang 'C4'?

### Projektion - Projizieren Sie die Relation Professoren auf die Attribute Personennummer und Name. Tun Sie in einem zweiten Schritt dasselbe für die Relation Assistenten.

### Kreuzprodukt - Welche mögliche Kombinationen von Vorlesungen und Professoren gibt es?

### Verbund

#### Welche Vorlesungen können als Nachfolger der Vorlesungen mit 4 SWS besucht werden?
#### Listen Sie in der ersten Spalte die Titel der Vorlesungen mit 4 SWS auf, und in der zweiten Spalte die Titel ihrer möglichen Nachfolger.
#### Zeichnen sie zudem den zugehörigen Abfragebaum.
#### Zeichnen sie zudem den zugehörigen Abfragebaum.

## Daten manipulieren

### Erstellen Sie eine Tabelle Hilfsassistenten, welche die gleichen Attribute wie die Tabelle Assistenten aufweist.

### Fügen Sie die Hilfsassistenten Chomsky (Fachgebiet Sprachphilosophie, arbeitet für Kant) und Newton (Naturphilosophie, Curie) ein.

### Ändern Sie das Fachgebiet von Newton zu idealistische Metaphysik.

### Löschen Sie Chomsky

## Daten aggregieren

### Wieviele Professoren mit Rang C3 gibt es?

### Was ist die minimale, maximale und durchschnittliche Anzahl Semester?

### Wieviele Semesterwochenstunden (SWS, ~= ECTS) unterrichten die Professoren mit Rang C4?
