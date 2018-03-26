# Exercises DI: Datenintegrität

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3682729_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium
Lesen Sie im Buch von Meier & Kaufmann (2016) die Kapitel 2.3.3 und 3.7 und beantworten Sie folgende Fragen:
### Welche 3 Arten von strukturellen Integritätsbedingungen gibt es?
**Eindeutigkeitsbedingung:** Jede Tabelle besitzt einen Identifikationsschlüssel (Merkmaloder Merkmalskombination), der jedes Tupel in der Tabelle auf eindeutige Art bestimmt.
<br>
**Wertebereichsbedingung:** Die Merkmale einer Tabelle können nur Datenwerte aus einem vordefinierten Wertebereich annehmen.
<br>
**Referenzielle Integritätsbedingung:** Jeder Wert eines Fremdschlüssels muss effektiv als Schlüsselwert in der referenzierten Tabelle existieren.

### Wie lautet die Definition für den Begriff „Referenzielle Integrität“?
Bei der referenziellen Integrität können Datensätze die einen Fremdschlüssel aufweisen nur dann gespeichert werden, wenn der Wert des Fremdschlüssels einmalig in der referenzierten Tabelle existiert. Im Falle, dass ein referenzierter Wert nicht vorhanden ist, kann der Datensatz nicht gespeichert werden.

### Welche 8 verschiedenen Arten von deklarativen Integritätsbedingungen gibt es? Zählen sie die 8 Begriffe auf.
**Primärschlüsseldefinition:** Mit `PRIMARY KEY` wird ein eindeutiger Primärschlüssel für eine Tabelle definiert. Ein Primärschlüssel darf definitionsgemäss nie Nullwerte enthalten.
**Fremdschlüsseldefinition:** Mit `FOREIGN KEY` kann ein Fremdschlüssel spezifiziert werden, der durch die Angabe `REFERENCES` auf die zugehörige Tabelle verweist.
**Eindeutigkeit:** Die Eindeutigkeit eines Attributes kann durch die Angabe `UNIQUE` festgehalten werden. Im Gegensatz zu Primärschlüsseln können eindeutige Attributwerte auch Nullwerte enthalten.
**Keine Nullwerte:** Mit der Angabe `NOT NULL` wird verhindert, dass ein Attribut Nullwerte besitzen kann.
**Prüfregel:** Eine solche Regel kann durch den `CHECK`-Befehl deklariert werden. Jedes Tupel in der Tabelle muss die Prüfregel erfüllen.
**Ändern oder Löschen mit Nullsetzen:** Mit der Angabe `ON UPDATE SET NULL` beziehungsweise `ON DELETE SET NULL` wird bei einer abhängigen Tabelle deklariert, dass beim ändern respektive Löschen des Tupels aus der Referenztabelle der Fremdschlüsselwert beim abhängigen Tupel auf Null gesetzt wird.
**Restriktives ändern oder Löschen:** Mit `ON UPDATE RESTRICT` bzw. `ON DELETE RESTRICT` können Referenztupel nicht geändert respektive gelöscht werden, solange sie noch abhängige Tupel besitzen.
**Fortgesetztesändern oder Löschen:** Mit der Angabe `ON UPDATE CASCADE` bzw. `ON DELETE CASCADE` kann die änderung respektive die Löschung eines Referenztupels auf die abhängigen Tupel ausgeweitet werden.

### Können Sie diese 8 deklariativen Integritätsbedingungen aus Kap. 3.7 zu den 3 strukturellen Integritätsbedingungen aus Kap. 2.3.3 zuordnen?

## 2. Referenzielle Integrität in SQL
Informieren Sie sich auf der PostgreSQL-Webseite, wie sie bei bestehenden Tabellen referenzielle Integritätsbedingungen einfügen können (ALTER TABLE ...)
<br><br>
http://www.postgresql.org/docs/9.4/static/sql­altertable.html
<br><br>
Definieren Sie alle referentiellen Constraints als Primär­ und Fremdschlüssel für die bestehende Uni­Datenbank auf PostgreSQL. Sorgen Sie zudem dafür, dass bei Änderung der Primärschlüssel alle Fremdschlüssel entsprechend aktualisiert werden: Bei Löschen falls möglich auf Null setzen, sonst löschen; bei Veränderung übernehmen.

## 3. Statische Integrity Constraints in SQL
Setzen Sie folgende Integritätsbedingungen in SQL auf der bestehenden Uni­Datenbank auf PostgreSQL mit ALTER TABLE um:

 * Professoren können nur die Ränge ‚C3’ und ‚C4’ haben.
 * Professoren haben Einzelbüros.
 * Die Noten dürfen nur zwischen 1.0 und 5.0 sein.
 * Die Namen der Studenten, Professoren und Assistenten dürfen nicht leer sein.

## 4. Trigger (1)
Professoren sollen immer nur einen Rang höher kommen, aber nie degradiert werden. Der Rang eines Professors ist dabei immer C3 oder C4. Implementieren Sie dazu in der Postgresql den folgenden Trigger:
```sql
CREATE OR REPLACE FUNCTION checkDegradierung () 
RETURNS TRIGGER AS $$ 
    BEGIN
        IF OLD.Rang IS NULL 
        OR NEW.Rang = 'C3' 
        AND OLD.RANG <> 'C4' 
        OR NEW.Rang  = 'C4' 
        THEN RETURN NEW;
        ELSE RAISE EXCEPTION 
            'Degradierender Rang --> %', NEW.rang;
        RETURN OLD; END IF;
    END; $$ LANGUAGE 'plpgsql';

CREATE TRIGGER keineDegradierung 
BEFORE UPDATE ON professoren
FOR EACH ROW EXECUTE PROCEDURE checkDegradierung();
```

Testen Sie den Trigger: Schreiben Sie ein Update Statement, welches alle Professoren die im Rang C4 sind, auf C3 degradiert, und schauen Sie sich die Response des Datenbankservers an.

## 5. Trigger (2)

Informieren Sie sich auf der Webseite von Postegresql, wie bzw. mit welcher Syntax Trigger­-Programme implementiert werden können.
<br>
Schreiben Sie einen Trigger in PostgreSQL, der prüft, ob Studenten für die Prüfungen alle Vorbedingungen erfüllen, d.h. ob sie alle Vorgänger der zu prüfenden Vorlesung mit genügender Note absolviert haben (<= 3.0).