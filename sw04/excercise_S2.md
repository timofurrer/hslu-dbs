# Exercises S2: Fortgeschrittenes SQL

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3666932_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## SQL-Aufgaben

### Mengenvergleich (ln)
Finden Sie die Namen der Professoren, die noch keine Prüfung abgenommen haben.

```sql
SELECT name 
FROM professoren 
WHERE persnr NOT IN (
  SELECT persnr 
  FROM pruefen
);
```


### Left outer join
Geben Sie eine Liste aller Professoren (alle Attribute) aus. Sofern ein Professor einen Assistenten hat, soll dessen Name und Fachgebiet ebenfalls ausgegeben werden.

```sql
SELECT * FROM professoren LEFT OUTER JOIN assistenten ON assistenten.boss = professoren.persnr;
```


### Full outer join
Geben Sie eine Liste aller Studenten (MatrNr und Name) und aller Vorlesungen (VorlNr und Titel), die sie hören. Sofern ein Student keine Vorlesung hört oder eine Vorlesung nicht besucht wird, sollen die entsprechenden Informationen des Studenten trotzdem ausgegeben werden.

```sql
SELECT s.matrnr, s.name, v.vorlnr, v.titel FROM vorlesungen as v FULL OUTER JOIN hoeren ON hoeren.vorlnr = v.vorlnr FULL OUTER JOIN studenten as s ON s.matrnr = hoeren.matrnr;
```

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

```sql
CREATE VIEW P as SELECT persnr as Nr, name FROM professoren;
CREATE VIEW A as SELECT persnr as Nr, name FROM assistenten;
```

### Vereinigung
Vereinigen Sie die beiden vorhergehend kreierten Relationen, und nennen Sie das Resultat Mitarbeiter.

```sql
CREATE VIEW Mitarbeiter as SELECT * FROM P UNION SELECT * FROM A;
```

### Schnittmenge
Welches sind die Namen der Mitarbeiter, die gleichzeitig Professor und Assistent sind?

```sql
SELECT name FROM professoren INTERSECT SELECT name FROM assistenten;
```

### Differenz

Welches sind die Namen der Assistenten, welche nicht gleichzeitig Student sind?

```sql
SELECT name FROM assistenten EXCEPT SELECT name FROM studenten;
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
