# Exercises S3: SQL Spezialisierung

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3671991_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

Die folgenden Übungen basieren auf der Uni-DB auf einem PostgreSQL-Server

## Metadaten

-> Beschreiben Sie einen Use Case, in dem Metadaten für Sie notwendig sind, und wo Sie dann das Dictionary verwenden können, um Beschreibungen von Tabellen und Spalten zu durchsuchen.

-> Welche Tabelle enthält die Spalte "Fachgebiet"?

```sql
SELECT table_name 
FROM information_schema.columns 
WHERE column_name = 'fachgebiet';
```

### Welche Spalten in der Uni-Datenbank haben den Datentyp Integer?

```sql
SELECT * FROM 
information_schema.columns 
WHERE data_type = 'integer';
```

### Welche Tabelle enthält das Informations-Schema? Schreiben Sie das entsprechende SQL

```sql
SELECT table_name 
FROM information_schema.tables;
```

## Nullwerte

-> Fügen Sie zuerst einen Studenten mit leerer Anzahl Semester ein. Zählen Sie dann mit folgender Query alle Studenten mit immer wahrer Bedingung auf den Semestern:

```sql
INSERT INTO Studenten VALUES (0, 'Precht', NULL);
SELECT 1, COUNT(*) FROM Studenten
WHERE Semester < 13 or semester >= 13
UNION 2, SELECT COUNT(*) FROM Studenten;
```

### Was fällt ihnen auf? Warum ist das Resultat unlogisch? Wie erklärt sich dieser Effekt?

### Wie müssen Sie die Query definieren, damit Sie auch mit Nullwerten ein konsistentes Resultat gibt?

## Existenz

### Was ist der Unterschied zwischen Mengenvergleichen mit "in" und "exists"? Warum kann man etwas nur mit dem exists-Operator abfragen?

-> Machen Sie ein Beispiel in SQL mit der Uni-DB und der Tabelle „prüfen“. Fragen Sie, in einer Abfrage, ohne join, unter Verwendung des „exists“‐Operators. die Prüfungen ab, welche für Studenten mit mehr als 10 Semestern von Professoren mit Rang C4 durchgeführt wurden.

## Fallunterscheidung

Gegeben ist folgende Fallunterscheidung:

```sql
SELECT MatrNr, 
CASE WHEN Note < 1.5 THEN 'sehr gut'
WHEN Note < 2.5 THEN 'gut'
WHEN Note < 3.5 THEN 'befriedigend'
WHEN Note <= 4.0 THEN 'ausreichend'
ELSE 'nicht bestanden' END as bewertung
FROM prüfen
```

### Warum wird hier jeweils nur geprüft, ob der Wert kleiner als die Untergrenze ist, aber nicht, ob er auch grösser als die Obergrenze ist?

## Reskursion

-> Gegeben folgende rekursive SQL-Query auf die Uni-DB
```sql
with recursive r as (
select vg.titel as v, nf.titel as n, 1 as l
from voraussetzen vr join vorlesungen vg
on vg.vorlnr = vr.vorgänger
join vorlesungen nf on nf.vorlnr = vr.nachfolger),
pfad(von,nach,länge,folge) as (
select v,n,1,v || ','|| n from r union all
select p.von, e.n, p.länge+1, p.folge ||','|| e.n
from r e join pfad p on p.nach = e.v )
select * from pfad
```

### Lassen Sie die Query laufen. Was macht dies genau? Wo befindet sich der Rekursionsschritt? Erklären Sie die Funktionsweise dieser Query.

## Windowing

-> Schreiben Sie eine Query, welche pro Professor den Namen, die Anzahl Semesterwochenstunden (SWS) und dazu den SWS-Rang angibt. Der SWS‐Rang gibt an, welcher Professor am meisten Vorlesungsstunden pro Semester gibt (SWS-Rank = 1), welcher am zweitmeisten unterrichtet (SWS-Rank = 2), usw. Professoren, die gleichviel unterrichten, sind auf dem gleichen SWS-Rang. Verwenden Sie dafür eine Window Function.
