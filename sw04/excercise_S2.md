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
SELECT * 
FROM professoren 
LEFT OUTER JOIN assistenten 
    ON assistenten.boss = professoren.persnr;
```


### Full outer join
Geben Sie eine Liste aller Studenten (MatrNr und Name) und aller Vorlesungen (VorlNr und Titel), die sie hören. Sofern ein Student keine Vorlesung hört oder eine Vorlesung nicht besucht wird, sollen die entsprechenden Informationen des Studenten trotzdem ausgegeben werden.

```sql
SELECT s.matrnr, s.name, v.vorlnr, v.titel 
FROM vorlesungen AS v 
FULL OUTER JOIN hoeren 
    ON hoeren.vorlnr = v.vorlnr 
FULL OUTER JOIN studenten AS s 
    ON s.matrnr = hoeren.matrnr;
```

### Right outer join
Schauen Sie sich folgenden äusseren join an:

```sql
SELECT v.Titel, s.name
FROM vorlesungen v
LEFT OUTER JOIN hoeren h ON h.VorlNr = v.VorlNr
RIGHT OUTER JOIN Studenten s ON s.MatrNr = h.MatrNr
```
#### Was geschieht, wenn Sie "right outer join" durch "left outer join" ersetzen?
Beim 'RIGHT OUTER JOIN' werden alle Studenten ausgegeben, auch jene, die keine Vorlesung besuchen. <br>
Beim 'LEFT OUTER JOIN' werden alle Vorlesungen ausgegeben, auch jene, die von keinem Studenten besucht werden.

#### Was geschieht, wenn Sie in der letzten Zeile "full outer join" verwenden?
Es werden alle Studenten und alle Vorlesungen ausgegeben.

## Zusammenhang Relationenalgebra und SQL: Mengenorientierte Operatoren

Die Beispiele beziehen sich auf die Uni-Datenbank.

### Umbenennung
Projizieren Sie die Relation Professoren auf die Attribute Personennummer und Name. Benennen Sie dabei das Attribut „PersNr“ in „Nr“ um. Benennen Sie die neue Relation „P“, und speichern Sie sie für die weitere Verwendung. 

Tun Sie das gleiche für die Relation Assistenten, und nennen Sie diese Relation "A".

```sql
CREATE VIEW P AS SELECT persnr AS Nr, name FROM professoren;
CREATE VIEW A AS SELECT persnr AS Nr, name FROM assistenten;
```

### Vereinigung
Vereinigen Sie die beiden vorhergehend kreierten Relationen, und nennen Sie das Resultat Mitarbeiter.

```sql
CREATE VIEW Mitarbeiter AS SELECT * FROM P UNION SELECT * FROM A;
```

### Schnittmenge
Welches sind die Namen der Mitarbeiter, die gleichzeitig Professor und Assistent sind?

```sql
SELECT name 
FROM professoren 
INTERSECT 
SELECT name 
FROM assistenten;
```

### Differenz

Welches sind die Namen der Assistenten, welche nicht gleichzeitig Student sind?

```sql
SELECT name 
FROM assistenten 
EXCEPT 
SELECT name 
FROM studenten;
```

### Division

Welches sind die Namen der Studenten, welche alle Vorlesungen besucht haben?

Testen können Sie dies mit folgendem Studentendatensatz:
```sql
INSERT INTO Studenten VALUES (123, 'Streber', 7);
INSERT INTO hoeren SELECT DISTINCT 123, VorlNr FROM vorlesungen;
```
Mit folgendem Query:
```sql
SELECT name 
FROM (SELECT s.name, COUNT (*) AS num
      FROM studenten s
      RIGHT OUTER JOIN hoeren h ON s.matrnr = h.matrnr
      GROUP BY name) AS stud 
WHERE num = (SELECT COUNT(*)
             FROM vorlesungen);
```
