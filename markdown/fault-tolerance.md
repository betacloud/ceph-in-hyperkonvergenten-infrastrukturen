# Warum diese Aufteilung?
<!-- Note -->
Bei Ausfall von einem ganzen System oder einer einzelnen Festplatte soll der Endanwender nichts davon merken.

Die Aufteilung auf viele kleine Systeme bei kleinen Umgebungen ergibt sich durch die Vielzahl der möglichen
Fehlerfälle aus den einzelnen Bereichen, welche möglichst alle abdeckt werden sollen.

Das ergibt sich am besten bei einem Blick auf die Funktionsweise von Ceph. Bei OpenStack verhält es sich dann
analog, nur dass hier virtuelle Systeme auf Compute Nodes verteilt werden und keine Objekte.


# Am Beispiel von Ceph


<!-- .slide: data-background-image="images/ceph-placement-001.png" data-background-size="contain" -->


<!-- .slide: data-background-image="images/ceph-placement-002.png" data-background-size="contain" -->
<!-- Note -->
* eine Datei wird in Objekte zerlegt


<!-- .slide: data-background-image="images/ceph-placement-003.png" data-background-size="contain" -->
<!-- Note -->
* jedes Objekt ist eindeutig einer Placement Group zugeordnet


<!-- .slide: data-background-image="images/ceph-placement-004.png" data-background-size="contain" -->
<!-- Note -->
* jede PG ist einer entsprechenden Anzahl von OSDs zugeordnet
* die OSDs werden nach Failure Domains gruppiert
* einer PG wird aus einer Failure Domain immer nur eine OSD zugeordnet


## Failure Domains
<!-- Note -->
Die Fehlertoleranz einer Umgebung wird durch die Berücksichtigung einzelner Failure Domains erreicht.

Bei Ceph ist die Umsetzung der Fehlertoleranz (Replikate) direkt enthalten und für den Endanwender transparent.

Bei OpenStack werden nur die Möglichkeiten zur Fehlertoleranz (Antiaffinität, Router HA, ..) zur Verfügung gestellt.
Realisiert werden muss die Fehlertoleranz bei OpenStack aber letztlich durch den Endanwender selbst.


* unterschiedliche Hardware
  * Daten sollten auf mehreren Festplatten und Systemen abgelegt werden <!-- .element: class="fragment" -->
  * virtuelle Systeme sollen auf unterschiedlichen Systemen laufen <!-- .element: class="fragment" -->


* unterschiedliche Standorte
  * Verteilung auf mehrere Racks und Räume innerhalb von einem RZ
* unterschiedliche Phasen und USVs <!-- .element: class="fragment" -->
* unterschiedliche Switches <!-- .element: class="fragment" -->


## Betrieb
<!-- Note -->
Die Fehlertoleranz einer Umgebung ist nicht nur bei Ausfällen wichtig. Ein Betrieb einer Umgebung wird erst durch eine gewisse Fehlertoleranz ermöglicht.

Wartungsarbeiten können zu Ausfällen oder notwendingen Restarts führen.

Wartungsarbeiten sind an Software sowie an Hardware erforderlich und zum Teil hat man keinen Einfluss auf deren Durchführung.


### Software

* Update vom BIOS <!-- .element: class="fragment" -->
* Update einer Firmware <!-- .element: class="fragment" -->
* Update von einem Kernel ohne Kernel Live Patching <!-- .element: class="fragment" -->
* Update von Systemdiensten wie Docker <!-- .element: class="fragment" -->


### Hardware

* Austausch von nicht Hot Plug/Swap fähigen Komponenten <!-- .element: class="fragment" -->
* Umzug von Bare-metal Systemen innerhalb vom RZ <!-- .element: class="fragment" -->
* Wartungsarbeiten im RZ <!-- .element: class="fragment" -->
* Ausfall von Infrastruktur  <!-- .element: class="fragment" -->
* Ausfall von RZ Infrastruktur <!-- .element: class="fragment" -->
  * Klimatisierung
  * Router
  * Strom


### Tests

* Wie verhält sich ein neuer Microcode? <!-- .element: class="fragment" -->
* Wie verhält sich eine neue Firmware? <!-- .element: class="fragment" -->
* Was passiert nach Änderung von einem Konfigurationsparameter? <!-- .element: class="fragment" -->
* Bringt die Platte X mehr Durchsatz als die Platte Y? <!-- .element: class="fragment" -->

<!-- Note -->
Viele Änderungen haben einen direkten oder indirekten Einfluss auf die Performance der Ressourcen.
Daher bietet es sich oft an eine Änderung zunächst auf einer Teilmenge der Systeme durchzuführen um
Auswirkungen auf die Performacne identifizieren zu können.


### Menschliches Versagen <!-- .element: class="hidden" -->

<!-- .slide: data-background-image="images/strip_0079.jpg" data-background-size="contain" -->

<!-- Note -->
Menschliches versagen führt ebenfalls zu Ausfällen. Falschen Knopf gedrückt, falsches Kabel umgesteckt, ...
Ein schönes Beispiel ist hier die Reinigungskraft, welche sich halt eine Steckdose für den Staubsauger freimachen muss.

Die Graphik stammt von Ralph Ruthe (https://ruthe.de/), einem begnadetem Witzbildmaler.


### Murphys Gesetz <!-- .element: class="hidden" -->

<!-- .slide: data-background-image="images/Murphys-law.jpg" data-background-size="contain" -->

<!-- Note -->
Wenn irgendwas ausfällt dann fällt noch irgendwas anderes direkt mit oder kurze Zeit später auch aus. Garantiert. Immer.


## Darum diese Aufteilung! <!-- .element: class="hidden" -->

<!-- .slide: data-background-image="images/strip_0025.jpg" data-background-size="contain" -->

<!-- Note -->
In kleinen Umgebungen führen wenige Systeme mit vielen Ressourcen direkt zum Totalausfall der Umgebung.
Zumindest führen sie direkt zu sehr starken und vom Endanwender spürbaren Beeinträchtigungen.
Ein Betrieb solcher Umgebungen ist oft umständlich und oft nur in Abstimmung mit dem Endanwender möglich.

Daher bietet es sich an bei kleinen Umgebung die Ressourcen auf viele Systeme zu verteilen. Dadurch wirkt
sich der Ausfall von einem System nicht so stark auf die Umgebung aus.

Wenn man bei Ceph z.B. nur drei Systeme mit Ressourcen hat man 3 Replikate benötigt hat man beim
Ausfall von nur einem System bereits ein Problem. Bei Ausfall von einem System sind dann bereits 33.3% der
Umgebung nicht mehr verfügbar.

Die Graphik stammt von Ralph Ruthe (https://ruthe.de/), einem begnadetem Witzbildmaler.
