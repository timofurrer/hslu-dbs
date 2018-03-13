# Exercises S2: Fortgeschrittenes SQL

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3666932_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## SQL-Aufgaben

### Mengenvergleich (ln)
Finden Sie die Namen der Professoren, die noch keine Prüfung abgenommen haben.


### Left outer join
Geben Sie eine Liste aller Professoren (alle Attribute) aus. Sofern ein Professor einen Assistenten hat, soll dessen Name und Fachgebiet ebenfalls ausgegeben werden.


### Full outer join
Geben Sie eine Liste aller Studenten (MatrNr und Name) und aller Vorlesungen (VorlNr und Titel), die sie hören. Sofern ein Student keine Vorlesung hört oder eine Vorlesung nicht besucht wird, sollen die entsprechenden Informationen des Studenten trotzdem ausgegeben werden.


### Right outer join
Schauen Sie sich folgenden äusseren join an:
```
select v.Titel, s.name
from vorlesungen v
left outer join hören h on h.VorlNr = v.VorlNr
right outer join Studenten s on s.MatrNr = h.MatrNr
```
Was geschieht, wenn Sie "right outer join" durch "left outer join" ersetzen?

Was geschieht, wenn Sie in der letzten Zeile "full outer join" verwenden?

## Zusammenhang Relationenalgebra und SQL: Mengenorientierte Operatoren

Die Beispiele beziehen sich auf die Uni-Datenbank.

### Umbenennung
Projizieren Sie die Relation Professoren auf die Attribute Personennummer und Name. Benennen Sie dabei das Attribut „PersNr“ in „Nr“ um. Benennen Sie die neue Relation „P“, und speichern Sie sie für die weitere Verwendung. 

Tun Sie das gleiche für die Relation Assistenten, und nennen Sie diese Relation "A".
```

```

### Vereinigung
Vereinigen Sie die beiden vorhergehend kreierten Relationen, und nennen Sie das Resultat Mitarbeiter.
```

```

### Schnittmenge
Welches sind die Namen der Mitarbeiter, die gleichzeitig Professor und Assistent sind?
```

```

### Differenz
Welches sind die Namen der Assistenten, welche nicht gleichzeitig Student sind?
```

```

### Division
Welches sind die Namen der Studenten, welche alle Vorlesungen besucht haben?

Testen können Sie dies mit folgendem Studentendatensatz:
```
insert into Studenten values (123, 'Streber', 7);
insert into hören select distinct 123, VorlNr from vorlesungen;
```
```

```
