# Exercises DO: Objektrelationales Mapping

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3682738_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium
Lesen Sie im Buch von Meier & Kaufmann (2016) die Kapitel 6.6 und beantworten Sie folgende Fragen:

### Was ist der Unterschied zwischen objektorientierten und objektrelationalen Datenbanken?

Bei einer objektorientierten Datenbank werden ganze Objekte persistiert. Bei einer objekt-relationalen Datenbanken werden Einträge persistiert, die in sich noch aus mehreren anderen Einträgen/Objekten bestehen können. Zwischen den Objekten bestehen dann Beziehungen (Relationen).

### Was ist ein Surrogat?

Ein Surrogat ist ein definierter, eindeutiger Schlüssel - welcher unabhängig von den Daten eines Tupels gesetzt wird. Üblicherweise eine automatisch inkrementierende Zahl.

### Was ist das NF^2 Modell?

NF^2 : Not first normal Form



### Was ist der Zusammenahng von NF^2 mit der Objektorientierung?



### Was heisst objekt-relationales Mapping?



## 3. Fragen

### A. Schauen Sie sich die generierte Datei persistence.xml an. Wie heisst die Persistence Unit, welche bei Ihnen generiert worden ist?

### B. Schauen Sie sich die generierte Datei Professoren.java an. Wie bzw. mit welchen Annotationen wurden die Primär- und Fremdschlüssel spezifiziert?

### C. Schauen Sie die generierte Datei Studenten.java an. Mit welchen Annotationen wurde die many-to‐many-Relationship umgesetzt? Wie sieht es diesbezüglich bei Vorlesungen.java aus?

### D. Wie wurde NOT NULL in JPA-Notation umgesetzt?

## 4. Programmierung

A. Instanzieren Sie einen Entity-Manager mit Variablenname em 
B. Geben Sie für alle Professoren den Namen und seine Vorlesungen aus via System.out. Verwenden Sie dazu die generierte NamedQuery Professoren.findAll mit der Methode em.createNamedQuery. 
C. Selektieren Sie via JPQL die Vorlesungen, welche Sokrates liest, und geben sie Sie via System.out aus. Verwenden sie dazu eine neue JPQL Query mit em.createQuery. 
D. Setzen sie den Raum von Sokrates auf 1234 und persistieren sie dies auf der Datenbank mit em.merge(). Dazu müssen Sie eine Transaktion mit ta=em.getTransaction() instanzieren, diese vor dem merge beginnen mit ta.begin() und nach dem merge committen mit ta.commit(). 
E. Fügen Sie einen neuen Professor mit Namen „Precht“ via JPA hinzu mit em.persist()
F. Fügen Sie eine neue Vorlesung mit Namen "Postmoderne" hinzu, welche Precht liest.

### Main-Methode

```java


```


















