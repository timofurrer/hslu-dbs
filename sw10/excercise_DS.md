# Exercises DS : Datensicherheit

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3706953_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium

### Was heisst Datensicherheit?



### Welche Rolle spielen Sichten für die Datensicherheit?



### Was heisst Grant? Was heisst Grant Option?



### Was ist SQL-Injection? Wie schützt man sich davor?

-> Gegeben ist die Ausgangslage in der Beispieldatenbank Uni auf ihrem lokalen MySQL Server. Die Professoren dürfen jeweils nur die Vorlesungen verändern (update, delete, insert), die von Kollegen mit dem gleichen Rang durchgeführt (gelesenVon) werden. Alle Professoren dürfen die Vorlesungen der Kollegen mit gleichem Rang abfragen (select). Zudem dürfen Professoren mit Rang C4 die Vorlesungen der Kollegen mit Rang C3 abfragen, aber nicht umgekehrt.



### Erstellen Sie pro Professor ein Benutzer mit gleichem Benutzernamen. Wählen Sie als Passwort ‚@‘ plus den Namen.



### Erstellen Sie zwei (änderbare) Sichten (updateable views), zusammen mit den entsprechenden Rechtevergaben, welche diese Anforderungen erfüllen:

* Alle Professoren mit Rang C4 sollen das Recht SELECT, INSERT, UPDATE und DELETE auf die View view_c4 kriegen.
* Zudem sollen Professoren mit Rang C4 das Recht SELECT auf die View view_c3 erhalten.
* Alle Professoren mit Rang C3 sollen das Recht SELECT, INSERT, UPDATE und DELETE auf die View view_c3 kriegen.

## 2. Views und Grants

## 3. SQL Injection

-> Lösen Sie das Level 1 des SQL-Injection Hackits von gehaxelt: http://hackit.gehaxelt.in

Dokumentieren Sie Ihr Vorgehen und ihre Lösung möglichst genau und nachvollziehbar.

### Dokumentation der Lösung
