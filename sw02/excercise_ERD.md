# Exercises ER: Entity Relationship Modelle

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3618328_download)

## Selbststudium

### Welche Assoziationstypen gibt es?

* Typ 1: Genau Eine
* Typ c: Null oder Eine
* Typ m: Eine oder mehrere
* Typ mc: Null, Eine oder Mehrere

### Was ist der Unterschied zwischen Generalisierung und Aggregation?

* Generalisierung: *is-a* Beziehung (Verallgemeinerung der Entitaeten)
* Aggregation: *part-of* Beziehung (Zusammenfuehrung von Entitaeten)

### Was ist der Unterschied zwischen Generalisierung und Spezialisierung?

* Generalisierung: *is-a* Beziehung (Verallgemeinerung der Entitaeten)
* Spezialisierung: *extends* Beziehung (Erweiterung einer Entitaet)

### Wann ist eine Spezialisierung vollständig?

Vollstaendig bedeutet, dass jede Entitaet der Generalisierung sich mindestens einer Spezialisierung zuordnen laesst.

### Wann ist sie disjunkt?

Sie schliessen sich gegenseitig aus.


## Fiktive Fallstudie
Die Firma AutoNomiX ist eine Informatikfirma mit 57 Mitarbeitern, welche an einem Arbeitsplatz in einem bestimmten Büro sitzen. Es gibt zwei Mitarbeiterkategorien: Aktionäre (Partner), und „normale“ Mitarbeiter. Aktionäre haben eine gewisse Anzahl Aktien. Die Mitarbeiter sind in verschiedenen Rollen (Projektleiter, Analyst, Programmierer) in verschiedenen Projekten beteiligt. Es gibt allerdings jeweils nur einen Projektleiter pro Projekt. Ein Projekt wird wiederum für eine Firma als Kunde durchgeführt. Kunden haben Adressen und Ansprechpartner mit Kontaktinformationen. Firmen, Mitarbeiter und Ansprechpartner sind (juristische) Personen. Weiter werden in den Projekten Dokumente erarbeitet, welche von verschiedenen Mitarbeitern als Autoren erstellt werden.

### Modellieren Sie ein konzeptionelles Entity - Relationship Diagramm zur Fallstudie AutoNomiX, basierend auf Entitätsmengen, Beziehungsmengen, Assozationen, Assoziationstypen und Merkmalen, inkl. Kennzeichnung der Schlüsselmerkmalen. Fügen Sie alle Informationen ein, welche Sie in der Beschreibung der Fallstudie erkennen können.

![alt text](https://i.imgur.com/BPyVZBU.jpg)


### Wo sehen Sie in diesem Beispiel eine Generalisierung, also eine „ist - ein“ Beziehung? Ist die zugehörige Spezialisierung vollständig?
Mitarbeiter : Projektleiter, Analyst, Programmierer
Überlappend vollständig

### Wo sehen Sie in diesem Beispiel eine Aggregation, also eine „teil-von“ Beziehung?
Arbeitsplatz : teil von Büro
