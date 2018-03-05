# Exercises RS: Relationale Schemas

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3618336_download)

## Selbststudium
Lesen Sie im Buch von Meier & Kaufmann (2016) die Kapitel 1.2.1, 2.3.1 und 2.3.2

### Wie wird der Begriff der Redundanz definiert?

Redundanz bedeutet, dass gewisse Daten mehrfach vorhanden sind. Wenn eine Redundanz vorhanden ist, koennen die *redundanten*  Daten ohne Informationsverlust weggelassen werden.

### Wozu werden die Normalformen eingesetzt, und aus welchem Grund?

* Greater overall database organization.
* Reduction of redundant data.
* Data consistency within the database.
* A much more flexible database design.
* A better handle on database security.

### Was ist eine Löschanomalie? Erklären Sie dies anhand eines konkreten Beispiels.

Eine Loeschanomalie tritt auf, wenn man in einer nicht-normalisierten Datenbank durch das Loeschen gewisser Datensaetze auch Informationen verliert, die nicht haetten verloren gehen sollen. Bsp:

| M# | Name | B# | Bezeichnung
|-:|-:|-:|-:|
| M1 | David | B1 | Chef |
| M2 | Domi | B2 | Leiter |
| M1 | David | B3 | Koenner |

Wuerde man *Domi* aus dieser Tabelle entfernen, wuerden die Bezeichnungen *B1* und *B3* auch verloren gehen, obwohl man dies nicht explizit gewollt hat.
 
### Was ist eine funktionale Abhängigkeit?

Jeder Wert von A bestimmt eindeutig den Wert von B. 

### Was ist eine volle funktionale Abhängigkeit?

Wenn A ein zusammengesetzter Schluessel ist: Volle Funktionale Abhaenhigkeit heisst, dass B nur von A, aber nicht von Untermengen von A (Teilschluessel) abhaengig ist.

### Was ist eine transitive Abhängigkeit?

Wenn C von B und B von A abhaengt. Aber nicht in die andere Richtung.

### Welchen Bezug haben diese Abhängigkeiten zu den Normalformen 1 – 3?

#### Normalform 1

Es wird ueberprueft, ob alle Merkmale funktional abhaengig zueinander sind.

#### Normalform 2

Es wird ueberprueft, ob alle Merkmale voll funktional abhaengig zueinander sind.

#### Normalform 3

Die Tabelle wird zusaetzlich zu *1* und *2* noch auf transitive Abhaengigkeiten geprueft.

### Was ist der unterschied zwischen einer Tabelle und einer Relation?

Eine Relation beschreibt tabellarisch die Beziehungen zwischen zwei Tabellen.

### Welches sind die zwei wichtigen Schlüsseleigenschaften?

* Eindeutigkeit
* Minimalitaet

### Warum braucht es für einfach-komplexe und einfach-einfache Beziehungsmengen keine Bezeiehungstabelle?

Die Ausgangstabelle speichert den PK der ausgelagerten Tabelle direkt als FK in einer Spalte.

### Wozu braucht es die siebte Regel? 

**Regel 7**: Aggregation

Die Entitaetsmenge und die Beziehungsmenge muessen als eigenstaendige Tabelle definitiert sein.

## Normalformen
Analysieren Sie folgende Tabelle hinsichtlich der Abhängigkeiten.

|Spiel|Entwickler|User|Geschlecht|Alter|Kategorie|Erstregistrierung|Bezeichnung|
|----:|---------:|---:|---------:|----:|--------:|----------------:|----------:|
|World of Warcraft|Blizzard|Chack|M|55|50+|19.03.00|Rollenspiel|
|Rift|Trion|Angela|F|55|50+|22.05.01|Rollenspiel|
|Guildwars|NcSoft|Burack|M|49|30|-|49|17.04.01|Rollenspiel|
|Star Wars Online|Electronic Arts|Chack|M|55|50+|08.08.05|SciFi|
|Rift|Trion|Burack|M|49|30|-|49|17.05.02|Rollenspiel|
|World of|Warcraft|Blizzard|Angela|F|55|50+|28.08.08|Rollenspiel|
|Star Wars Online|Electronic|Arts|Burack|M|49|30|-|49|17.11.11|SciFi|

### In welcher Normalform ist diese Tabelle? Begründen Sie ihre Antwort ganz genau aufgrund ihrer Analyse.

Die Tabelle ist in der ersten Normalform.
Es gibt nur eine einzige Tabelle und es sind keine Schluessel vorhanden.

### Wie würde diese Tabelle in der dritten Normalform aussehen? 

Mehrere Tabellen:
* Spiel
* User
* Bezeichnung

### In welcher Normalform ist die folgende Tabelle?

|Kunde: KNr, Name, Ort|Buch (inkl. Preis)|Verkaufsdatum|Sachgebiet|Verkaufspersonal: PNr, Name, Stellung|
|--------------------:|-----------------:|------------:|---------:|------------------------------------:|
|1, Blatter, Fribourg|The Stand, 30.- / Tiptopf, 25.-|04.11.2014 / 09.11.2014|Roman / Kochen|1, Spahni, Filialleiter / 1. Spahni, Filialleiter|
|2, Tobler, Bern|Ehrenschuld, 45.- / Flugzeuge der Welt, 55.- / Die Jury, 65.-|09.11.2014 / 25.11.2014 / 30.11.2014|Roman / Sachbuch / Thriller|1, Spahni, Filialleiter / 3, Bieri, Lehrtochter / 2, Schaller, Verkäufer|
|3, Brunner, Fribourg|The Stand, 31.- / Die Jury, 55.-|04.11.2014 / 30.11.2014|Roman / Thriller|2, Schaller, Verkäufer / 3, Bieri, Lehrtochter|
|4, Salis, Bern|Das Rad der Zeit, 16.- / Gartenbau, 19.-|04.11.2014 / 25.11.2014|Fantasy / Natur|3, Bieri, Lehrtochter / 1, Spahni, Filialleiter|
|5, Walter, Biel|Gartenbau, 19.- / Alaskafieber, 26.- / Stiller, 12.-|25.11.2014 / 01.11.2014 / 09.11.2014|Natur / Reisen / Roman|1, Spahni, Filialleiter / 2, Schaller, Verkäufer / 3, Bieri, Lehrtochter|
|6, Zurfluh, Basel|Stiller, 17.- / Sturmhöhe, 25.-|14.11.2014 / 14.11.2014|Roman / Roman|2, Schaller, Verkäufer / 2, Schaller, Verkäufer|
|7, Marty, Basel|Mietrecht, 23.- / Stiller, 11.- / Alaskafieber, 17.-|16.11.2014 / 17.11.2014 / 17.11.2014|Recht / Roman / Reisen|3, Bieri, Lehrtochter / 2, Schaller, Verkäufer / 1, Spahni, Filialleiter|

Die Tabelle ist unnormalisiert.

### Wie würde diese Tabelle in der dritten Normalform aussehen?

Mehrere Tabellen:
* Kunde
* Adresse
* Buch
* Verkaufspersonal
* Sachgebiet
* Verkauf
* Stellung

## Umsetzung eines ER-Diagramms in ein relationales Schema

### Wie würde diese Tabelle in der dritten Normalform aussehen?
In der vorherigen Session haben Sie eine Übung gemacht, bei der Sie ein ER-Modell für eine Firma erstellt haben. Setzen sie Ihr ER-Modell der Übung AutoNomiX (oder das ER-Modell der Musterlösung) in ein relationales Schema um. Laden und installieren Sie dazu die MySQL Workbench.

### Können sie nachvollziehen, wie die Entitäten und Beziehungen im Code abgebildet wurden?
