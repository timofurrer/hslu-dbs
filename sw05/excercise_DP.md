# Exercises DP: Datenbankprogrammierung

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3671997_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## Selbststudium
Lesen Sie Kapitel 3.5 aus dem Buch von Meier & Kaufmann (2016)

### Was ist ein Cursor? Definieren Sie das Konzept in Ihren eigenen Worten.



### Aus welchem Grund (warum) und zu welchem Zweck (wozu) braucht man Cursors?



### Wozu werden Datenbanksprachen in andere Sprachen eingebettet?

## Hello JDBC

-> Laden Sie die Datei 03 HelloJdbcPgsql.zip von ILIAS und bringen Sie das im Unterricht besprochene Beispiel mit Ihrer lokalen Uni-Datenbank auf PostgreSQL zum laufen.

-> Erweitern Sie dieses JDBC-Pogramm, so dass es die Namen aller Vorlesungen zu einem Professor darstellt. Benutzen Sie dazu keinen Join, sndern die while-Schliefe innerhalb von Java.

## Stored Procedures

-> Erstellen Sie auf Ihrer lokalen Postgresql-Installation eine Tabelle:
```sql
CREATE TABLE t(datum date primary key, yay boolean);
```
-> Dann erstellen Sie eine Stored Procedure f:

```sql
CREATE OR REPLACE FUNCTION f (startdate date, anz int)
RETURNS VOID
AS $$
DECLARE
  i int;
  nextDay date;
BEGIN
  i := 1;
  nextDay := startdate;
  WHILE (anz>=i) LOOP
    IF (extract(dow from nextDay) in (6,0)) THEN
      INSERT INTO t(datum, yay)
      VALUES (nextDay, true);
    ELSE
      INSERT INTO t(datum, yay)
      VALUES(nextDay, false);
    END IF;
    i := i + 1;
    nextDay := nextDay + INTERVAL '1 day';
  END LOOP;
END;
$$
LANGUAGE 'plpgsql'
```

-> Anschliessend können Sie die die Prozedur wie folgt aufrufen:

```sql
select f('2016-11-11', 111);
```

-> Schauen Sie sich nun die Tabelle an:
```sql
SELECT * FROM t
```

### Frage: welche Semantik hat die Prozedur f (was genau macht das Programm)? Was bedeuten die Daten, welche die Prozedur generiert?

## Verbindung von JDBC mit Stored Procedures

-> Erstellen Sie ein Java-Programm, welches folgende Aktionen durchführt:
* Eingabe zweier Parameter via main(String[] args): Anfangsdatum und Anzahl Tage
* Verbindungsaufnahme mit ihrem lokalen PostgreSQL Server
* Löschen der Tabelle t mit delete
* Aufruf der oben definierten Stored-Function f mit den eingegebenen Parametern
* Ausgabe des Inhalts der Kalender-Tabelle mit System.out.println()

-> Für den Aufruf von SQL-Statements, die kein Resultset zurückgeben, muss die Methode Statement.execute() verwendet werden.

## Stored Functions und Cursors

-> Programmieren Sie in PostgreSQL eine stored Function, welche den Median der Anzahl Semester der Studenten berechnet. Verwenden Sie dazu einen zeilenorientierten Cursor.

-> Infos: http://www.postgresql.org/docs/9.4/static/plpgsql.html
