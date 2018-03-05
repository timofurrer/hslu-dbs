# Exercises RS: Relationale Schemas

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3618336_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## Selbststudium
Lesen Sie im Buch von Meier & Kaufmann (2016) die Kapitel 1.2.1, 2.3.1 und 2.3.2

### Wie wird der Begriff der Redundanz definiert?

Redundanz bedeutet, dass gewisse Daten mehrfach vorhanden sind. Wenn eine Redundanz vorhanden ist, koennen die *redundanten*  Daten ohne Informationsverlust weggelassen werden.

### Wozu werden die Normalformen eingesetzt, und aus welchem Grund?

* Greater overall database organization.
* Reduction of redundant data.
* Data consistency within the database.
* A much more flexible database design.
* A better handle on database security.

### Was ist eine Löschanomalie? Erklären Sie dies anhand eines konkreten Beispiels.

Eine Loeschanomalie tritt auf, wenn man in einer nicht-normalisierten Datenbank durch das Loeschen gewisser Datensaetze auch Informationen verliert, die nicht haetten verloren gehen sollen. Bsp:

| M# | Name | B# | Bezeichnung
|-:|-:|-:|-:|
| M1 | David | B1 | Chef |
| M2 | Domi | B2 | Leiter |
| M1 | David | B3 | Koenner |

Wuerde man *Domi* aus dieser Tabelle entfernen, wuerden die Bezeichnungen *B1* und *B3* auch verloren gehen, obwohl man dies nicht explizit gewollt hat.
 
### Was ist eine funktionale Abhängigkeit?

Jeder Wert von A bestimmt eindeutig den Wert von B. 

### Was ist eine volle funktionale Abhängigkeit?

Wenn A ein zusammengesetzter Schluessel ist: Volle Funktionale Abhaenhigkeit heisst, dass B nur von A, aber nicht von Untermengen von A (Teilschluessel) abhaengig ist.

### Was ist eine transitive Abhängigkeit?

Wenn C von B und B von A abhaengt. Aber nicht in die andere Richtung.

### Welchen Bezug haben diese Abhängigkeiten zu den Normalformen 1 – 3?

#### Normalform 1

Es wird ueberprueft, ob alle Merkmale funktional abhaengig zueinander sind.

#### Normalform 2

Es wird ueberprueft, ob alle Merkmale voll funktional abhaengig zueinander sind.

#### Normalform 3

Die Tabelle wird zusaetzlich zu *1* und *2* noch auf transitive Abhaengigkeiten geprueft.

### Was ist der unterschied zwischen einer Tabelle und einer Relation?

Eine Relation beschreibt tabellarisch die Beziehungen zwischen zwei Tabellen.

### Welches sind die zwei wichtigen Schlüsseleigenschaften?

* Eindeutigkeit
* Minimalitaet

### Warum braucht es für einfach-komplexe und einfach-einfache Beziehungsmengen keine Bezeiehungstabelle?

Die Ausgangstabelle speichert den PK der ausgelagerten Tabelle direkt als FK in einer Spalte.

### Wozu braucht es die siebte Regel? 

**Regel 7**: Aggregation

Die Entitaetsmenge und die Beziehungsmenge muessen als eigenstaendige Tabelle definitiert sein.

## Normalformen
Analysieren Sie folgende Tabelle hinsichtlich der Abhängigkeiten.

|Spiel|Entwickler|User|Geschlecht|Alter|Kategorie|Erstregistrierung|Bezeichnung|
|----:|---------:|---:|---------:|----:|--------:|----------------:|----------:|
|World of Warcraft|Blizzard|Chack|M|55|50+|19.03.00|Rollenspiel|
|Rift|Trion|Angela|F|55|50+|22.05.01|Rollenspiel|
|Guildwars|NcSoft|Burack|M|49|30|-|49|17.04.01|Rollenspiel|
|Star Wars Online|Electronic Arts|Chack|M|55|50+|08.08.05|SciFi|
|Rift|Trion|Burack|M|49|30|-|49|17.05.02|Rollenspiel|
|World of|Warcraft|Blizzard|Angela|F|55|50+|28.08.08|Rollenspiel|
|Star Wars Online|Electronic|Arts|Burack|M|49|30|-|49|17.11.11|SciFi|

### In welcher Normalform ist diese Tabelle? Begründen Sie ihre Antwort ganz genau aufgrund ihrer Analyse.

Die Tabelle ist in der ersten Normalform.
Es gibt nur eine einzige Tabelle und es sind keine Schluessel vorhanden.

### Wie würde diese Tabelle in der dritten Normalform aussehen? 

Mehrere Tabellen:
* Spiel
* User
* Bezeichnung

### In welcher Normalform ist die folgende Tabelle?

|Kunde: KNr, Name, Ort|Buch (inkl. Preis)|Verkaufsdatum|Sachgebiet|Verkaufspersonal: PNr, Name, Stellung|
|--------------------:|-----------------:|------------:|---------:|------------------------------------:|
|1, Blatter, Fribourg|The Stand, 30.- / Tiptopf, 25.-|04.11.2014 / 09.11.2014|Roman / Kochen|1, Spahni, Filialleiter / 1. Spahni, Filialleiter|
|2, Tobler, Bern|Ehrenschuld, 45.- / Flugzeuge der Welt, 55.- / Die Jury, 65.-|09.11.2014 / 25.11.2014 / 30.11.2014|Roman / Sachbuch / Thriller|1, Spahni, Filialleiter / 3, Bieri, Lehrtochter / 2, Schaller, Verkäufer|
|3, Brunner, Fribourg|The Stand, 31.- / Die Jury, 55.-|04.11.2014 / 30.11.2014|Roman / Thriller|2, Schaller, Verkäufer / 3, Bieri, Lehrtochter|
|4, Salis, Bern|Das Rad der Zeit, 16.- / Gartenbau, 19.-|04.11.2014 / 25.11.2014|Fantasy / Natur|3, Bieri, Lehrtochter / 1, Spahni, Filialleiter|
|5, Walter, Biel|Gartenbau, 19.- / Alaskafieber, 26.- / Stiller, 12.-|25.11.2014 / 01.11.2014 / 09.11.2014|Natur / Reisen / Roman|1, Spahni, Filialleiter / 2, Schaller, Verkäufer / 3, Bieri, Lehrtochter|
|6, Zurfluh, Basel|Stiller, 17.- / Sturmhöhe, 25.-|14.11.2014 / 14.11.2014|Roman / Roman|2, Schaller, Verkäufer / 2, Schaller, Verkäufer|
|7, Marty, Basel|Mietrecht, 23.- / Stiller, 11.- / Alaskafieber, 17.-|16.11.2014 / 17.11.2014 / 17.11.2014|Recht / Roman / Reisen|3, Bieri, Lehrtochter / 2, Schaller, Verkäufer / 1, Spahni, Filialleiter|

Die Tabelle ist unnormalisiert.

### Wie würde diese Tabelle in der dritten Normalform aussehen?

Mehrere Tabellen:
* Kunde
* Adresse
* Buch
* Verkaufspersonal
* Sachgebiet
* Verkauf
* Stellung

## Umsetzung eines ER-Diagramms in ein relationales Schema

### Generated SQL file
```
-- MySQL Script generated by MySQL Workbench
-- 03/05/18 15:38:40
-- Model: New Model    Version: 1.0
-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL,ALLOW_INVALID_DATES';

-- -----------------------------------------------------
-- Schema mydb
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Table `Büro`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Büro` (
  `idBüro` INT NOT NULL,
  `Bezeichnng` VARCHAR(45) NULL,
  PRIMARY KEY (`idBüro`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Arbeitsplatz`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Arbeitsplatz` (
  `idArbeitsplatz` INT NOT NULL,
  `Arbeitsplatzcol` VARCHAR(45) NULL,
  `Büro_idBüro` INT NOT NULL,
  PRIMARY KEY (`idArbeitsplatz`),
  CONSTRAINT `fk_Arbeitsplatz_Büro`
    FOREIGN KEY (`Büro_idBüro`)
    REFERENCES `Büro` (`idBüro`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Arbeitsplatz_Büro_idx` ON `Arbeitsplatz` (`Büro_idBüro` ASC);


-- -----------------------------------------------------
-- Table `Mitarbeiter`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Mitarbeiter` (
  `idMitarbeiter` INT NOT NULL,
  `Arbeitsplatz_idArbeitsplatz` INT NOT NULL,
  PRIMARY KEY (`idMitarbeiter`),
  CONSTRAINT `fk_Mitarbeiter_Arbeitsplatz1`
    FOREIGN KEY (`Arbeitsplatz_idArbeitsplatz`)
    REFERENCES `Arbeitsplatz` (`idArbeitsplatz`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Mitarbeiter_Arbeitsplatz1_idx` ON `Mitarbeiter` (`Arbeitsplatz_idArbeitsplatz` ASC);


-- -----------------------------------------------------
-- Table `Aktionär`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Aktionär` (
  `idAktionär` INT NOT NULL,
  `Mitarbeiter_idMitarbeiter` INT NOT NULL,
  PRIMARY KEY (`idAktionär`),
  CONSTRAINT `fk_Aktionär_Mitarbeiter1`
    FOREIGN KEY (`Mitarbeiter_idMitarbeiter`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Aktionär_Mitarbeiter1_idx` ON `Aktionär` (`Mitarbeiter_idMitarbeiter` ASC);


-- -----------------------------------------------------
-- Table `Aktie`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Aktie` (
  `idAktie` INT NOT NULL,
  `Aktionär_idAktionär` INT NOT NULL,
  PRIMARY KEY (`idAktie`),
  CONSTRAINT `fk_Aktie_Aktionär1`
    FOREIGN KEY (`Aktionär_idAktionär`)
    REFERENCES `Aktionär` (`idAktionär`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Aktie_Aktionär1_idx` ON `Aktie` (`Aktionär_idAktionär` ASC);


-- -----------------------------------------------------
-- Table `Firma`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Firma` (
  `idFirma` INT NOT NULL,
  `Ansprechspartner` INT NOT NULL,
  PRIMARY KEY (`idFirma`),
  CONSTRAINT `fk_Firma_Mitarbeiter1`
    FOREIGN KEY (`Ansprechspartner`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Firma_Mitarbeiter1_idx` ON `Firma` (`Ansprechspartner` ASC);


-- -----------------------------------------------------
-- Table `Projekt`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Projekt` (
  `idProjekt` INT NOT NULL,
  `Bezeichnung` VARCHAR(45) NULL,
  `KundenId` INT NOT NULL,
  `ProjektleiterId` INT NOT NULL,
  PRIMARY KEY (`idProjekt`),
  CONSTRAINT `fk_Projekt_Firma1`
    FOREIGN KEY (`KundenId`)
    REFERENCES `Firma` (`idFirma`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Projekt_Mitarbeiter1`
    FOREIGN KEY (`ProjektleiterId`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Projekt_Firma1_idx` ON `Projekt` (`KundenId` ASC);

CREATE INDEX `fk_Projekt_Mitarbeiter1_idx` ON `Projekt` (`ProjektleiterId` ASC);


-- -----------------------------------------------------
-- Table `Programmierer`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Programmierer` (
  `idAnalyst` INT NOT NULL,
  `Mitarbeiter_idMitarbeiter` INT NOT NULL,
  `Projekt_idProjekt` INT NOT NULL,
  PRIMARY KEY (`idAnalyst`),
  CONSTRAINT `fk_Programmierer_Mitarbeiter1`
    FOREIGN KEY (`Mitarbeiter_idMitarbeiter`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Programmierer_Projekt1`
    FOREIGN KEY (`Projekt_idProjekt`)
    REFERENCES `Projekt` (`idProjekt`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Programmierer_Mitarbeiter1_idx` ON `Programmierer` (`Mitarbeiter_idMitarbeiter` ASC);

CREATE INDEX `fk_Programmierer_Projekt1_idx` ON `Programmierer` (`Projekt_idProjekt` ASC);


-- -----------------------------------------------------
-- Table `Analyst`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Analyst` (
  `idAnalyst` INT NOT NULL,
  `Mitarbeiter_idMitarbeiter` INT NOT NULL,
  `Projekt_idProjekt` INT NOT NULL,
  PRIMARY KEY (`idAnalyst`),
  CONSTRAINT `fk_Analyst_Mitarbeiter1`
    FOREIGN KEY (`Mitarbeiter_idMitarbeiter`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Analyst_Projekt1`
    FOREIGN KEY (`Projekt_idProjekt`)
    REFERENCES `Projekt` (`idProjekt`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Analyst_Mitarbeiter1_idx` ON `Analyst` (`Mitarbeiter_idMitarbeiter` ASC);

CREATE INDEX `fk_Analyst_Projekt1_idx` ON `Analyst` (`Projekt_idProjekt` ASC);


-- -----------------------------------------------------
-- Table `Adresse`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Adresse` (
  `idAdresse` INT NOT NULL,
  `PLZ` VARCHAR(45) NULL,
  `Ort` VARCHAR(45) NULL,
  `Strasse` VARCHAR(45) NULL,
  PRIMARY KEY (`idAdresse`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Kunde`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Kunde` (
  `idKunde` INT NOT NULL,
  `Firma_idFirma` INT NOT NULL,
  `Adresse_idAdresse` INT NOT NULL,
  PRIMARY KEY (`idKunde`),
  CONSTRAINT `fk_Kunde_Firma1`
    FOREIGN KEY (`Firma_idFirma`)
    REFERENCES `Firma` (`idFirma`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Kunde_Adresse1`
    FOREIGN KEY (`Adresse_idAdresse`)
    REFERENCES `Adresse` (`idAdresse`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Kunde_Firma1_idx` ON `Kunde` (`Firma_idFirma` ASC);

CREATE INDEX `fk_Kunde_Adresse1_idx` ON `Kunde` (`Adresse_idAdresse` ASC);


-- -----------------------------------------------------
-- Table `Dokumente`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Dokumente` (
  `idDokumente` INT NOT NULL,
  `Projekt_idProjekt` INT NOT NULL,
  PRIMARY KEY (`idDokumente`),
  CONSTRAINT `fk_Dokumente_Projekt1`
    FOREIGN KEY (`Projekt_idProjekt`)
    REFERENCES `Projekt` (`idProjekt`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Dokumente_Projekt1_idx` ON `Dokumente` (`Projekt_idProjekt` ASC);


-- -----------------------------------------------------
-- Table `Autor`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Autor` (
  `Mitarbeiter_idMitarbeiter` INT NOT NULL,
  `Dokumente_idDokumente` INT NOT NULL,
  CONSTRAINT `fk_Autor_Mitarbeiter1`
    FOREIGN KEY (`Mitarbeiter_idMitarbeiter`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Autor_Dokumente1`
    FOREIGN KEY (`Dokumente_idDokumente`)
    REFERENCES `Dokumente` (`idDokumente`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Autor_Mitarbeiter1_idx` ON `Autor` (`Mitarbeiter_idMitarbeiter` ASC);

CREATE INDEX `fk_Autor_Dokumente1_idx` ON `Autor` (`Dokumente_idDokumente` ASC);


-- -----------------------------------------------------
-- Table `JuristischePerson`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `JuristischePerson` (
  `idJuristischePerson` INT NOT NULL,
  `Firma_idFirma` INT NOT NULL,
  PRIMARY KEY (`idJuristischePerson`),
  CONSTRAINT `fk_JuristischePerson_Firma1`
    FOREIGN KEY (`Firma_idFirma`)
    REFERENCES `Firma` (`idFirma`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_JuristischePerson_Firma1_idx` ON `JuristischePerson` (`Firma_idFirma` ASC);


-- -----------------------------------------------------
-- Table `Ansprechpartner`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Ansprechpartner` (
  `idAnsprechpartner` INT NOT NULL,
  `Kunde_idKunde` INT NOT NULL,
  `Mitarbeiter_idMitarbeiter` INT NOT NULL,
  `JuristischePerson_idJuristischePerson` INT NOT NULL,
  `KontaktInformation` VARCHAR(45) NULL,
  CONSTRAINT `fk_Ansprechpartner_Kunde1`
    FOREIGN KEY (`Kunde_idKunde`)
    REFERENCES `Kunde` (`idKunde`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Ansprechpartner_Mitarbeiter1`
    FOREIGN KEY (`Mitarbeiter_idMitarbeiter`)
    REFERENCES `Mitarbeiter` (`idMitarbeiter`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Ansprechpartner_JuristischePerson1`
    FOREIGN KEY (`JuristischePerson_idJuristischePerson`)
    REFERENCES `JuristischePerson` (`idJuristischePerson`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

CREATE INDEX `fk_Ansprechpartner_Kunde1_idx` ON `Ansprechpartner` (`Kunde_idKunde` ASC);

CREATE INDEX `fk_Ansprechpartner_Mitarbeiter1_idx` ON `Ansprechpartner` (`Mitarbeiter_idMitarbeiter` ASC);

CREATE INDEX `fk_Ansprechpartner_JuristischePerson1_idx` ON `Ansprechpartner` (`JuristischePerson_idJuristischePerson` ASC);


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
```
