# Exercises S3: SQL Spezialisierung

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3671991_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

Die folgenden Übungen basieren auf der Uni-DB auf einem PostgreSQL-Server

## Metadaten

### Beschreiben Sie einen Use Case, in dem Metadaten für Sie notwendig sind, und wo Sie dann das Dictionary verwenden können, um Beschreibungen von Tabellen und Spalten zu durchsuchen.

Wenn man eine fremde Datenbank analysieren moechte. Man bekommt ueber die Metadaten einen guten Ueberblick ueber die vorhandenen Tabellen und deren Schema.

### Welche Tabelle enthält die Spalte "Fachgebiet"?

```sql
SELECT table_name 
FROM information_schema.columns 
WHERE column_name = 'fachgebiet';
```

### Welche Spalten in der Uni-Datenbank haben den Datentyp Integer?

```sql
SELECT column_name
FROM information_schema.columns 
WHERE data_type = 'integer';
```

### Welche Tabelle enthält das Informations-Schema? Schreiben Sie das entsprechende SQL

```sql
SELECT table_name 
FROM information_schema.tables;
```

## Nullwerte

### Fügen Sie zuerst einen Studenten mit leerer Anzahl Semester ein. Zählen Sie dann mit folgender Query alle Studenten mit immer wahrer Bedingung auf den Semestern:

```sql
INSERT INTO Studenten 
VALUES (0, 'Precht', NULL);

SELECT 1, COUNT(*) 
FROM Studenten
WHERE Semester < 13 
   OR semester >= 13
UNION SELECT 2, COUNT(*) 
      FROM Studenten;
```

### Was fällt ihnen auf? Warum ist das Resultat unlogisch? Wie erklärt sich dieser Effekt?

Beim ersten `SELECT` wird der Student nicht mitgezaehlt, weil ein Semester den Wert `NULL` hat und somit weder kleiner noch groesser gleich 13 ist.
Beim `*` wird dieser `NULL` Wert ebenfalls mitgezaehlt.

### Wie müssen Sie die Query definieren, damit Sie auch mit Nullwerten ein konsistentes Resultat gibt?

```sql
SELECT COUNT(*) 
FROM studenten 
WHERE semester IS NULL 
   OR semester < 13 
   OR semester >= 13;
```

## Existenz

### Was ist der Unterschied zwischen Mengenvergleichen mit "in" und "exists"? Warum kann man etwas nur mit dem exists-Operator abfragen?

* Bei `IN` wird immer das gesamte Subquery durchgefuehrt. 
* Bei `EXISTS` wird das Subquery beim ersten Match abgebrochen - wodurch es vorallem bei grossen Datenmengen schneller ist.
* Bei kleinen Datenmengen ist `IN` performanter.
* `EXISTS` kann `NULL`-Vergleiche durchfuehren - `IN` kann das nicht.

### Machen Sie ein Beispiel in SQL mit der Uni-DB und der Tabelle „prüfen“. Fragen Sie, in einer Abfrage, ohne join, unter Verwendung des „exists“‐Operators. die Prüfungen ab, welche für Studenten mit mehr als 10 Semestern von Professoren mit Rang C4 durchgeführt wurden.

```sql
SELECT * 
FROM pruefen 
WHERE EXISTS (
  SELECT * 
  FROM studenten 
  WHERE studenten.matrnr = pruefen.matrnr 
    AND studenten.semester > 10
) AND EXISTS (
  SELECT * 
  FROM professoren 
  WHERE professoren.persnr = pruefen.persnr 
    AND professoren.rang = 'C4'
);
```

## Fallunterscheidung

Gegeben ist folgende Fallunterscheidung:

```sql
SELECT MatrNr, 
CASE WHEN Note < 1.5 THEN 'sehr gut'
     WHEN Note < 2.5 THEN 'gut'
     WHEN Note < 3.5 THEN 'befriedigend'
     WHEN Note <= 4.0 THEN 'ausreichend'
     ELSE 'nicht bestanden' END AS bewertung
FROM prüfen;
```

### Warum wird hier jeweils nur geprüft, ob der Wert kleiner als die Untergrenze ist, aber nicht, ob er auch grösser als die Obergrenze ist?

Weil jeweils nur ein `THEN` pro `CASE` ausgefuehrt wird -> First Match. :tada:

## Reskursion

### Gegeben folgende rekursive SQL-Query auf die Uni-DB

```sql
WITH RECURSIVE r AS (
  SELECT vg.titel AS v, nf.titel AS n, 1 AS l
  FROM voraussetzen vr 
  JOIN vorlesungen vg
    ON vg.vorlnr = vr.vorgaenger
  JOIN vorlesungen nf 
    ON nf.vorlnr = vr.nachfolger),
pfad(von,nach,länge,folge) AS (
  SELECT v,n,1,v || ','|| n 
  FROM r 
  UNION ALL
  SELECT p.von, e.n, p.länge+1, p.folge ||','|| e.n
  FROM r e 
  JOIN pfad p 
    ON p.nach = e.v )
SELECT * 
FROM pfad;
```

### Lassen Sie die Query laufen. Was macht dies genau? Wo befindet sich der Rekursionsschritt? Erklären Sie die Funktionsweise dieser Query.

Zum verstehen des Statements werden die Aliase aussagekräftiger definiert:

```sql
WITH RECURSIVE recursion AS (
  SELECT vorgängerVorlesung.titel AS Voraussetzung, nachfolgerVorlesung.titel AS Ermöglicht, 1 AS pfadLänge
  FROM voraussetzen
  JOIN vorlesungen vorgängerVorlesung
    ON vorgängerVorlesung.vorlnr = voraussetzen.vorgaenger
  JOIN vorlesungen nachfolgerVorlesung 
    ON nachfolgerVorlesung.vorlnr = voraussetzen.nachfolger),
pfad(von,nach,länge,folge) AS (
  SELECT Voraussetzung, Ermöglicht, 1, Voraussetzung || ','|| Ermöglicht 
  FROM recursion
  UNION ALL
  SELECT pfad.von, rec.Ermöglicht, pfad.länge+1, pfad.folge ||','|| rec.Ermöglicht
  FROM recursion rec
  JOIN pfad
    ON pfad.nach = rec.Voraussetzung )
SELECT * 
FROM pfad;
```

Das Query retourniert eine Tabelle, aus der man erkennen kann, welche Vorlesungen man nacheinander Besuchen kann bezw. welche Vorlesungen man zuvor besuchen muss.
<br>
Für dies wird in der `recursion` eine Ansicht generiert. Diese zeigt die Titel der Vorlesungen welche eine andere andere Vorlesung als Voraussetzung haben. zudem wird auch der Titel der Vorlesung welche Vorausgesetzt wird angezeigt. Die Pfadlänge wird generell auf 1 gesetzt, da in dieser Ansicht jede Ermöglichte Vorlesung eine Vorlesung als Voraussetzung hat.

```sql
SELECT vorgängerVorlesung.titel AS Voraussetzung, nachfolgerVorlesung.titel AS Ermöglicht, 1 AS pfadLänge
  FROM voraussetzen
  JOIN vorlesungen vorgängerVorlesung
    ON vorgängerVorlesung.vorlnr = voraussetzen.vorgaenger
  JOIN vorlesungen nachfolgerVorlesung 
    ON nachfolgerVorlesung.vorlnr = voraussetzen.nachfolger;
```
Dies ist das Ergebnis:
|voraussetzung       |ermöglicht          |pfadlänge|
|-------------------:|-------------------:|--------:|
|Grundzuege          |Ethik               |1        |
|Grundzuege          |Erkenntnistheorie   |1        |
|Grundzuege          |Maeeutik            |1        |
|Erkenntnistheorie   |Wissenschaftstheorie|1        |
|Ethik               |Wissenschaftstheorie|1        |
|Ethik               |Bioethik            |1        |
|Wissenschaftstheorie|Der Wiener Kreis    |1        |




In der Methode `pfad()` wird darauf eine Mengenvereinigung mit `UNION ALL` gemacht. Das erste `SELECT` listet dabei alle einfachen Vorgänger & Nachfolger (Tabelle oben). 
<br>
Das zweite `SELECT` macht ein `JOIN` mit der `pfad()` Methode selber (:tada: Rekursion!). Mit `ON pfad.nach = rec.Voraussetzung` wird geschaut ob eine Vorlesung, die in diesem Schritt als Voraussetzung gelistet ist, selber auch noch eine Voraussetzung besitzt, also in der `recursion` als Ermöglicht gelistet ist. Dies trifft z.B. für Erkenntnistheorie zu:

|voraussetzung       |ermöglicht          |pfadlänge|
|-------------------:|-------------------:|--------:|
|Grundzuege          |`Erkenntnistheorie` |1        |
|`Erkenntnistheorie` |Wissenschaftstheorie|1        |


Ist dies der Fall werden sie durch das erste Statement vor dem `UNION` zurückgegeben zudem wird durch `pfad.länge+1, pfad.folge ||','|| rec.Ermöglicht` die länge des pfades inkrementiert und die folge um eine Voraussetzung erweitert.
<br>
Der  Nach dem dem `UNION` wird dan wiederum nach einer möglichen Voraussetzung gesucht was dann wieder in die `pfad()` Methode führt.
<br>
Das Ergebnis des ganzen sieht dann am Ende so aus:

|von                 |nach                |länge|folge                                                              |
|-------------------:|-------------------:|----:|------------------------------------------------------------------:|
|Grundzuege          |Ethik               |   1 | Grundzuege,Ethik                                                  |
|Grundzuege          |Erkenntnistheorie   |   1 | Grundzuege,Erkenntnistheorie                                      |
|Grundzuege          |Maeeutik            |   1 | Grundzuege,Maeeutik                                               |
|Erkenntnistheorie   |Wissenschaftstheorie|   1 | Erkenntnistheorie,Wissenschaftstheorie                            |
|Ethik               |Wissenschaftstheorie|   1 | Ethik,Wissenschaftstheorie                                        |
|Ethik               |Bioethik            |   1 | Ethik,Bioethik                                                    |
|Wissenschaftstheorie|Der Wiener Kreis    |   1 | Wissenschaftstheorie,Der Wiener Kreis                             |
|Grundzuege          |Wissenschaftstheorie|   2 | Grundzuege,Erkenntnistheorie,Wissenschaftstheorie                 |
|Grundzuege          |Wissenschaftstheorie|   2 | Grundzuege,Ethik,Wissenschaftstheorie                             |
|Grundzuege          |Bioethik            |   2 | Grundzuege,Ethik,Bioethik                                         |
|Erkenntnistheorie   |Der Wiener Kreis    |   2 | Erkenntnistheorie,Wissenschaftstheorie,Der Wiener Kreis           |
|Ethik               |Der Wiener Kreis    |   2 | Ethik,Wissenschaftstheorie,Der Wiener Kreis                       |
|Grundzuege          |Der Wiener Kreis    |   3 | Grundzuege,Erkenntnistheorie,Wissenschaftstheorie,Der Wiener Kreis|
|Grundzuege          |Der Wiener Kreis    |   3 | Grundzuege,Ethik,Wissenschaftstheorie,Der Wiener Kreis            |

## Windowing

### Schreiben Sie eine Query, welche pro Professor den Namen, die Anzahl Semesterwochenstunden (SWS) und dazu den SWS-Rang angibt. Der SWS‐Rang gibt an, welcher Professor am meisten Vorlesungsstunden pro Semester gibt (SWS-Rank = 1), welcher am zweitmeisten unterrichtet (SWS-Rank = 2), usw. Professoren, die gleichviel unterrichten, sind auf dem gleichen SWS-Rang. Verwenden Sie dafür eine Window Function.

```sql
SELECT p.name, SUM(v.sws) AS "SWS", 
   DENSE_RANK() OVER(ORDER BY SUM(sws) DESC) AS "SWS-Rang" 
FROM professoren AS p 
INNER JOIN vorlesungen AS v 
   ON v.gelesenvon = p.persnr 
GROUP BY p.name;
```
