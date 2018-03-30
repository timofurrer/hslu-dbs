# Exercises DO: Objektrelationales Mapping

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3682738_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium
Lesen Sie im Buch von Meier & Kaufmann (2016) die Kapitel 6.6 und beantworten Sie folgende Fragen:

### Was ist der Unterschied zwischen objektorientierten und objektrelationalen Datenbanken?

Bei einer objektorientierten Datenbank werden ganze Objekte persistiert. Bei einer objekt-relationalen Datenbanken werden Einträge persistiert, die in sich noch aus mehreren anderen Einträgen/Objekten bestehen können. Zwischen den Objekten bestehen dann Beziehungen (Relationen).

### Was ist ein Surrogat?

Ein Surrogat ist ein definierter, eindeutiger Identifikations-Schlüssel eines Tupels - welcher unabhängig von den Daten eines Tupels gesetzt wird. Üblicherweise eine automatisch inkrementierende Zahl.

### Was ist das NF^2 Modell?

NF^2 : Not first normal Form

Das NFNF ist ein Modell, welches auf einer unnormalisierten Datenbank basiert. Die Daten sind in diesem Modell (noch) nicht objekt-relational, sondern objekt-orientiert.

### Was ist der Zusammenahng von NF^2 mit der Objektorientierung?

Eine unnormalisierte Datenbank nach dem NF^2 Modell ist objektorientiert, da die Datenbakn nicht normalisiert ist. Somit können in einem Feld eines Tupels auch noch mehrere Werte drin sein - respektive gibt es keine direkten Abhängigkeiten zu anderen Objekten.

### Was heisst objekt-relationales Mapping?

Beim objekt-relationalen Mapping handelt es sich um die Verknüpfung von Objekten einer objekt-orientierten Programmiersprache, mit Objekten in einem relationalen Datenbanksystem.

## 3. Fragen

### A. Schauen Sie sich die generierte Datei persistence.xml an. Wie heisst die Persistence Unit, welche bei Ihnen generiert worden ist?

Die Persistence-Unit heisst : ObjektrelationalesMappingPU

```xml
<persistence version="2.1" xmlns="http://xmlns.jcp.org/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd">
  <persistence-unit name="ObjektrationalesMappingPU" transaction-type="RESOURCE_LOCAL">
    ..................
  </persistence-unit>
</persistence>

```

### B. Schauen Sie sich die generierte Datei Professoren.java an. Wie bzw. mit welchen Annotationen wurden die Primär- und Fremdschlüssel spezifiziert?

Die Personal-Nummer wurde als nicht optional und als ID spezifiziert.

```java
@Id
@Basic(optional = false)
@Column(name = "PersNr")
private Integer persNr;
```

Der Gelesen-Von Fremdschlüssel wurde als eine OneToMany Beziehung spezifiziert.

```java
@OneToMany(mappedBy = "gelesenVon")
private Collection<Vorlesungen> vorlesungenCollection;
```

### C. Schauen Sie die generierte Datei Studenten.java an. Mit welchen Annotationen wurde die many-to‐many-Relationship umgesetzt? Wie sieht es diesbezüglich bei Vorlesungen.java aus?

```java
@ManyToMany(mappedBy = "vorlesungenCollection")
private Collection<Studenten> studentenCollection;
```

### D. Wie wurde NOT NULL in JPA-Notation umgesetzt?

Dies wird über das Basic-Tag gesetzt:

```java
@Basic(optional = false)
@Column(name = "VorlNr")
private Integer vorlNr;
```

## 4. Programmierung

* A. Instanzieren Sie einen Entity-Manager mit Variablenname em 
* B. Geben Sie für alle Professoren den Namen und seine Vorlesungen aus via System.out. Verwenden Sie dazu die generierte NamedQuery Professoren.findAll mit der Methode em.createNamedQuery. 
* C. Selektieren Sie via JPQL die Vorlesungen, welche Sokrates liest, und geben sie Sie via System.out aus. Verwenden sie dazu eine neue JPQL Query mit em.createQuery. 
* D. Setzen sie den Raum von Sokrates auf 1234 und persistieren sie dies auf der Datenbank mit em.merge(). Dazu müssen Sie eine Transaktion mit ta=em.getTransaction() instanzieren, diese vor dem merge beginnen mit ta.begin() und nach dem merge committen mit ta.commit(). 
* E. Fügen Sie einen neuen Professor mit Namen „Precht“ via JPA hinzu mit em.persist()
* F. Fügen Sie eine neue Vorlesung mit Namen "Postmoderne" hinzu, welche Precht liest.

### Main-Methode

```java
public static void main(String[] args) {
        
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("ObjektrationalesMappingPU");
        EntityManager em = emf.createEntityManager();
        
        Query q1 = em.createNamedQuery("Professoren.findAll");
        List results = q1.getResultList();
        
        for (Object temp : results)
        {
            Professoren prof = (Professoren)temp;
            System.out.println(prof.getName());
            prof.getVorlesungenCollection().forEach((vorl) -> {
                System.out.println(vorl.getTitel());
            });       
            System.out.println("------------------");
        }
        
        q1 = em.createQuery("SELECT v FROM Vorlesungen v");
        results = q1.getResultList();
        for (Object temp : results) {
            Vorlesungen vorl = (Vorlesungen)temp;
            if (vorl.getGelesenVon().getName().equals("Sokrates")) {
                System.out.println(vorl.getTitel());
            }            
        }
        
        Professoren sokrates = new Professoren();
        EntityTransaction transaction = em.getTransaction();
        transaction.begin();
        q1 = em.createNamedQuery("Professoren.findAll");
        results = q1.getResultList();
        for (Object temp : results) {
            Professoren prof = (Professoren)temp;
            if (prof.getName().equals("Sokrates")) {
                sokrates = prof;
                sokrates.setRaum(1234);
            }
        }
        em.merge(sokrates);
        transaction.commit();
        
        Professoren prof = new Professoren(2200, "Precht");
        prof.setRang("C4");
        prof.setRaum(1212);
        em.persist(prof);
        
        Vorlesungen vorl = new Vorlesungen();
        vorl.setGelesenVon(prof);
        em.persist(vorl);
    }

```
