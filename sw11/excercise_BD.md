# Exercises BD: Big Data Management

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3706937_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium

### Wie hat sich die potenzielle Informationsmenge weltweit entwickelt?

Exponentiell: <br>
1986 - 2.6 EB <br>
1993 - 15.8 EB <br>
2000 - 54.5 EB <br>
2007 - 295 EB <br>
 <br>
 EB -> Exabyte  =  1  x  10^18  Bytes


### Wieviel Speicherkapazität wurde fürs Jahr 2007 geschätzt?

ca. 264 EB (nicht  normalisiert  für  die  Kompression)  
ca. 276 EB (optimal  komprimierte)

### Wenn dieser Trend so weitergeht, wo stehen wir im Jahr 2017? Und wieviele Daten, weltweit und pro Kopf, werden wir im Jahr 2030 haben?

Die CARG (Compound Annual Growth Rate) wurde auf 23% berechnet.

276 * 1.23^10 = 2'187 EB fürs Jahr 2017

276 * 1.23^23 = 32'264 EB fürs Jahr 2030 -> verteilt auf 8.5 Mia Menschen [1] -> 3.8 TB pro Kopf

[1] Quelle:https://www.un.org/sustainabledevelopment/blog/2015/07/un-projects-world-population-to-reach-8-5-billion-by-2030-driven-by-growth-in-developing-countries/


### Was bedeutet dies für unsere Gesellschaft, für Organisationen und für Individuen?

Da es immer mehr Daten geben wird, wird es immer wichtiger zu unterscheiden zwischen nützlichen Informationen und nicht relevanten Daten. Dass  Datenverarbeitung effizient und zielführend gemacht wird wird immer essenzieller werden. Da die Datenverarbeitung selbst auch wieder neue Daten generiert, wird wahrscheinlich in Zukunft mehr Wert darauf gelegt Datenströme möglichst früh zu filtern. 

## 2. Fallstudie

-> Studieren Sie den Vortrag von Scitility AG (Herbst 2015, gekürzte Fassung) und die Fallstudie mit der Speicherung von Kassenbons mit Big Data Technologien.

-> Vergleichen Sie diesen Case mit dem theoretischen Modell BDMcube aus den Folien (Seite 35).

### Datafication

#### Real world signals: Um welche Signale der realen Welt geht es in der Fallstudie?

Es handelt sich um Kassendaten, die in Form von Kassenbons gesetzteswegen gespeichert werden muessen.

#### Sensors and Input Devices: Wie werden diese Signale zu Daten (Datafizierung)?

Die Kassonbons werden an POS (Point of Sale) generiert und via Bulk Loads in ein RDBMS gespeichert.

### Integration

#### Source Data: Welches sind die Quelldaten und wo sind sie gespeichert?

Es handelt sich hierbei um folgende Daten eines Kassenbons:

* Kunde Id
* Product Family bestehend aus TRX und Wert.

#### Integrated Data Base: Wie und wo werden die Daten in einer Datenbasis integriert?

Sie werden in HBase / Hadoop gespeichert.

### Analysis

#### Analytic Processes: Welche analytischen Geschäftsvorgänge verwenden diese Daten (oder könnten dieses Daten verwenden)?

* Vorhersagen was ein Kunde kauft
* Auswertung was, wie oft gekauft wurde
* Auswerten welche Kunden an welchen Produkten interessiert sind
* Auswerten welche Produkte zusammen gekauft werden

Mit diesen Auswertungen kann man Aktionen planen und die Produkte entsprechend im Verkaufsstandort praesentieren bzw. im allgemeinen gezielteres Marketing betreiben

#### Analytic Software: Mit welcher analytischen Software und mit welchen Algorithmen werden die Daten analysiert (oder könnten damit analysiert werden?)

Mit den bestehenden Frontend-Services.
In der Fallstudie wird nichts spezifisches erwaehnt. Es gibt aber eine Menge Machine Learning Algorithmen die man brauchen koennte:

* Basket Analysis mit apriori
* Logistic Classification -> Was ein Kunde kaufen wird.

### Interaction

#### Applying Processes: Wie interagieren die Daten mit anwendenen Prozessen?

Es geht vorallem darum Lizenz- und Lohnkoesten zu sparen.
Sonst kann nichts aus der Fallstudie gelesen werden.

#### User & Machine Interfaces: Mit welche Mensch / Maschinen Schnittstellen bestehen für die Interation mit Daten

Es gibt eine Mobile und Web Applikation, die die Daten in HBase ueber eine REST-API abfragen und verarbeiten koennen.

### Effectuation

#### Value Creation: Wie entsteht durch Big Data Management Wert für das Unternehmen?

Es geht vorallem darum Lizenz- und Lohnkoesten zu sparen.
Auch die bestehenden Frontends koennen weiterhin verwendet werden.
Zudem koennen die Daten gespeichert werden, was von gesetzteswegen erforderlich ist.
