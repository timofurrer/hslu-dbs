# Exercises DS : Datensicherheit

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3706953_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Selbststudium

### Was heisst Datensicherheit?

> Als Datensicherheit oder globaler noch Informationssicherheit bezeichnet man die Eigenschaften von IT-Systemen die die Vertraulichkeit, Verfügbarkeit und die Integrität der Informationen sicherstellen. Die Informationen werden dabei eingeschränkt (Vertraulichkeit) überprüfbar gemacht (Integrität) und mehrfach abgespeichert (Verfügbarkeit).

Quelle : https://www.mastertools.ch/blog/posts/2013/september/datensicherheit-vs-datenschutz/

### Welche Rolle spielen Sichten für die Datensicherheit?

Über die Sichten (engl. "Views") können für Verschiedene Nutzergruppen, respektive Nutzer, seperate Zugriffsberechtigungen auf die Daten gegeben werden. Ein Datenanalyst benötigt zum Beispiel lediglich nicht-personenbezogene Daten, somit kann die Tabelle mit den sensitiven Daten ausgeblendet werden in der View. Für einen Buchhalter sind aber genau diese Informationen am wichtigstens, deswegen kann ihm eine andere View zugeteilt werden, mit unterschiedlichen Rechten.

### Was heisst Grant? Was heisst Grant Option?

"Grant", zu Deutsch "gewähren", ist ein Keyword, mit welchem man Nutzern gewisse Berechtigungen auf eine Tabelle oder View zuweisen oder entfernen kann.

Wenn dem Keyword "Grant" noch das Keyword "Option" hinzugefügt wird, kann man die Rechtevergabe für das spezifische Privleg weiterreichen. Somit kann der neu gewährte User ebenfalls dieses Privileg an weitere Nutzer gewähren.

### Was ist SQL-Injection? Wie schützt man sich davor?

Bei SQL-Injection handelt es sich um eine gewollte Injektion von Code/Scripts bei Eingabemasken, um Daten zu verändern/löschen/erstellen. Typischerweise wird hier gewollt der Text der Eingabemaske "beendet" um danach SQL Statements zu schreiben, welche dann Daten herausholen, auf der Datenbank löschen oder verändert werden.

Da der Eingabetext potenziell immer ausführbaren SQL-Code enthalten könnte, sollte man die SQL-Statement-Generierung bewusst im Vorhinein kompilieren, und dann den Eingabetext als Parameter einfügen. Dies geht auf der Client-Seite mit "Prepared Statements" und auf der DB-Server-Seite mit "Stored Procedures".

## 2. Views und Grants

-> Gegeben ist die Ausgangslage in der Beispieldatenbank Uni auf ihrem lokalen MySQL Server. Die Professoren dürfen jeweils nur die Vorlesungen verändern (update, delete, insert), die von Kollegen mit dem gleichen Rang durchgeführt (gelesenVon) werden. Alle Professoren dürfen die Vorlesungen der Kollegen mit gleichem Rang abfragen (select). Zudem dürfen Professoren mit Rang C4 die Vorlesungen der Kollegen mit Rang C3 abfragen, aber nicht umgekehrt.



### Erstellen Sie pro Professor ein Benutzer mit gleichem Benutzernamen. Wählen Sie als Passwort ‚@‘ plus den Namen.



### Erstellen Sie zwei (änderbare) Sichten (updateable views), zusammen mit den entsprechenden Rechtevergaben, welche diese Anforderungen erfüllen:

* Alle Professoren mit Rang C4 sollen das Recht SELECT, INSERT, UPDATE und DELETE auf die View view_c4 kriegen.
* Zudem sollen Professoren mit Rang C4 das Recht SELECT auf die View view_c3 erhalten.
* Alle Professoren mit Rang C3 sollen das Recht SELECT, INSERT, UPDATE und DELETE auf die View view_c3 kriegen.

## 3. SQL Injection

-> Lösen Sie das Level 1 des SQL-Injection Hackits von gehaxelt: http://hackit.gehaxelt.in

Dokumentieren Sie Ihr Vorgehen und ihre Lösung möglichst genau und nachvollziehbar.

### Dokumentation der Lösung
