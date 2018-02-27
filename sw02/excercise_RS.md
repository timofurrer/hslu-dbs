# Exercises RS: Relationale Schemas

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3618336_download)

## Selbststudium
Lesen Sie im Buch von Meier & Kaufmann (2016) die Kapitel 1.2.1, 2.3.1 und 2.3.2

### Wie wird der Begriff der Redundanz definiert?

### Wozu werden die Normalformen eingesetzt, und aus welchem Grund?

### Was ist eine Löschanomalie? Erklären Sie dies anhand eines konkreten Beispiels.
 
### Was ist eine funktionale Abhängigkeit?

### Was ist eine volle funktionale Abhängigkeit?

### Was ist eine transitive Abhängigkeit?

### Welchen Bezug haben diese Abhängigkeiten zu den Normalformen 1 – 3?

### Was ist der unterschied zwischen einer Tabelle und einer Relation?

### Welches sind die zwei wichtigen Schlüsseleigenschaften?

### Warum braucht es für einfach-komplexe und einfach-einfache Beziehungsmengen keine Bezeiehungstabelle?

### Wozu braucht es die siebte Regel? 

## Bonusaufgabe
Schauen Sie den ACM - Artikel von E.F. Codd auf ILIAS an: p377-codd.pdf (auf ILIAS).

### was sind aus Sicht E.F. Codd die Vorteile des relationalen Datenbankmodells gegenüber den damals verbreiteten Modellen wie z.B. dem graph- oder network model?

### Was heisst data independence und was ist diesbezüglich der Vorteil des relationalen Modells?

### Welche Arten von Datenabhängigkeiten in damaligen Systemen nennt Codd?

### Welches sind die 5 Eigenschaften von Relationen, die Codd aufzählt?

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

### Wie würde diese Tabelle in der dritten Normalform aussehen? 

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

### Wie würde diese Tabelle in der dritten Normalform aussehen?
