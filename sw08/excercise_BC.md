# Exercises BC: Blockchain

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3692473_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium
Lesen Sie folgende Publikation: https://eprint.iacr.org/2017/375.pdf

### Macht der Einsatz einer Blockchain Lösung immer Sinn?

Nein.

### Erachten Sie Blockchain-Lösungen mit einer zentralen Autorität, welche die Blockchain verwaltet als sinngemäss? Schauen Sie sich als Referenz die Lösung von Ripple an.

Dies kommt stark auf die Nutzeranzahl darauf an, welche prinzipiell schon einmal limitiert ist wenn der Zugriff auf die Blockchain limitiert wird. Wenn zu wenige Nutzer wirklich "mitrechnen", macht es definitiv kein Sinn, da Manipulationen einfach möglich wären. Hingegen wenn trotzdem noch sehr viele Nutzer aktiv die Blockchain nutzen, ist die Sicherheit trotzdem zu einem gewissen Mass gegeben und es kann Sinn machen die Vorteile einer Blockchain zu nutzen.

### Welche Blockchain-Type gibt es?

**1. Typ Permissionless Blockchain**: Jeder darf als Reader oder Writer auf die Blockchain zugreifen, es gibt keine zentrale Einheit welche gewisse Benutzer vom System blocken könnten. Bitcon und Ehtereum sind Beispiele für permissionless Blockchains.

**2. Typ : Permissioned Blockchain**: Nur gewisse Benutzer dürfen als Reader oder Writer auf die Blockchain zugreifen, es gibt eine zentrale Einheit welche gewisse Benutzer vom System blocken oder ausschliessen könnten. Hyperledger Fabric and R3 Corda sind Beispiele für permissioned Blockchains.

### Für welche Anwendungsfälle ist die Blockchain primär geeignet?

Für die Speicherung von Daten, welche nicht mehr verändert werden dürfen und auch nicht sollen.

### Überlegen Sie sich einen möglichen Anwendungsfall und beschreiben Sie diesen kurz mit einem passenden Use Case

Ein von der Polizei/Gericht geführtes Strafregister, bei dem alle Zwischenfälle zu einer Person gespeichert werden. Durch die Blockchain kann man so im Nachhinein keine früheren Einträge editieren, weil sonst die ganze Blockchain nicht mehr valid wäre. Hier will man das Verändern der Vergangenheit verhindern, weil etwas passiertes nicht ungeschehen gemacht werden kann. Durch eine Blockchain wäre diese Anforderung out-of-the-Box gegeben.

## 2. Gruppenarbeit

### Welche Unterschiede und Gemeinsamkeiten bestehen zwischen einer relationalen Datenbank und einer Blockchain-basierten Datenbank wie Bitcoin? Erstellen Sie dazu ein Vergleichsraster

|                    |Relationale DB      |Blockchain          |
|:-------------------|:-------------------|:-------------------|
| Performance | Hoch | Tief |
| Skalierbarkeit | Mittel | Hoch |
| Datenkonsistenz | Möglich, aber nicht immer gegeben | Immer gegeben |
| Form | Im Normalfall zentral | Dezentral |
| Create | X | X |
| Read | X | X |
| Update | X |  |
| Delete | X |  |

### Wie würden Sie eine Blockchain Datenbank in das Universum von realtionalen und NoSQLDatenbanken einordnen? Erstellen Sie dazu eine kleine Grafik und beschrieben Sie die Differenzierung.



### Sind Blockchain Datenbanken kompatibel mit CRUD?

Nein, man kann zwar CREATE und READ auf der Blockchain ausführen, ein UPDATE oder DELETE funktioniert jedoch nicht.

### Fassen Sie auf einer ¼ Seite die Einsatzmöglichkeiten und Fuktionen von BigChainDB (https://www.bigchaindb.com/) zusammen.

