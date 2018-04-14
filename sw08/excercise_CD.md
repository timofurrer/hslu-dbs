# Exercises CD: Cloud Datenbank

[ILIAS Dokument](https://elearning.hslu.ch/ilias/goto.php?target=file_3692411_download)

Gruppe 04 - Timo Furrer, David Staub, Dominik Waldispühl

## 1. Aufgaben

### Was macht Cloud Datenbanken so attraktiv?
* Schnell deployed
* Pay per useage
* Keine Installation & Maintenance kosten
* Aufrüsten auf neue Technologien wird vom Vendor übernommen.
* Einfach Skalierbar
* User Acces von überall


### Welche Typen von Cloud Services werden angeboten und wie unterscheiden sich diese?
* SaaS (Software as a Service)
    * Wird in der Regel auf einer PaaS-Cloud-Lösung aufgesetzt, unabhängig davon, ob diese Plattform öffentlich verfügbar ist oder nicht, und bietet Software für Endbenutzer. Es ist ein relativ restriktives Modell, bei dem Kunden vordefinierte Services nutzen, anstatt eigene zu implementieren.
* PaaS (Platform as a Service)
    * Ermöglicht dem Client, Anwendungen zu erstellen und zu verwalten, während der Anbieter die Hardware und Software auf seiner eigenen Infrastrukturden Hosted. Zusätzlich zu der Hardware, die in IaaS-Bereitstellungen enthalten ist, enthält PaaS Entwicklungswerkzeuge, Managementsysteme, Middleware und alle anderen Tools, die für den Aufbau erforderlich sind.
* IaaS (Infrastructure as a Service)
    * Ermöglicht dem Client das installieren und managen von Datenbanken und Anwendungen auf virtuellen Servern, Speicherplatz und Hardware des Rechenzentrums des Anbieters. Der Kern in diesem Szenario ist die Hardwarevirtualisierung, die die Bereitstellung von Gastbetriebssystemen und Anwendungen auf Remote-Geräten ermöglicht, die zu skalierbaren, verteilten Lösungen führen. Darüber hinaus bietet sie On-Demand-Services für Kunden mit einer gemeinsamen Plattformarchitektur und bietet erhöhte Flexibilität.

### Was sind Container Services?

Container as a Service (CaaS) ist ein Cloud-Dienst, mit dem Softwareentwickler Container starten, stoppen, organisieren, scalen und managen können. Wie bei den meisten Cloud-Diensten zahlen Benutzer nur für die von ihnen verwendeten CaaS-Ressourcen wie Recheninstanzen, Lastausgleichs- und Planungsfunktionen. Typische Anbiter sind Google mit Google Container Engine, Microsoft mit Azure Container Service und Amazon mit Amazon ECS Container Agent.

### Was ist der Unterschied zwischen File und Block Storage?

#### File Storage
Diese Speichertechnologie wird am häufigsten für Speichersysteme verwendet, die in Festplatten, NAS-Systemen usw. enthalten sind. In dieser Speicherart wird die Festplatte mit einem Protokoll wie NFS oder SMB / CIFS konfiguriert, und die Dateien werden hirarchisch gespeichert.

#### Block Storage
Diese Speichertechnologie werden "rohe" Speicher-Volumen angeboten. Jeder Block kann einzeln verwalter und als einzelen Festplatte gemanaged werden. Die Blocks werden von einem Server verwaltet.

### Gibt es Ansätze AI-Lösungen als Cloud Service anzubieten?

Ja, gibt es. [Googles CLOUD AI](https://cloud.google.com/products/machine-learning/) ist ein Beispiel.

## 2. Hands-on

Siehe [Ionic CRUD ShoppingList with Firebase](https://github.com/timofurrer/hslu-dbs/tree/master/sw08/crud-app/IonicShoppingList)
