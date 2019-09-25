# Vereinigung <!-- .element: class="hidden" -->
<!-- .slide: data-background-image="images/strip_1765.jpg" data-background-size="contain" -->

<!-- Note -->
Die Graphik stammt von Ralph Ruthe (https://ruthe.de/), einem begnadetem Witzbildmaler.


<!-- .slide: data-background-image="images/merge-001.png" data-background-size="contain" -->


<!-- .slide: data-background-image="images/merge-002.png" data-background-size="contain" -->
<!-- Note -->


<!-- .slide: data-background-image="images/merge-003.png" data-background-size="contain" -->
<!-- Note -->


<!-- .slide: data-background-image="images/merge-004.png" data-background-size="contain" -->
<!-- Note -->


<!-- .slide: data-background-image="images/merge-005.png" data-background-size="contain" -->
<!-- Note -->


<!-- .slide: data-background-image="images/merge-006.png" data-background-size="contain" -->
<!-- Note -->


<!-- .slide: data-background-image="images/merge-007.png" data-background-size="contain" -->


<!-- .slide: data-background-image="images/merge-008.png" data-background-size="contain" -->

## Detailansichten Nodes <!-- .element: class="hidden" -->
<!-- .slide: data-background-image="images/merged-node-001.png" data-background-size="contain" -->


<!-- .slide: data-background-image="images/merged-node-002.png" data-background-size="contain" -->


## Zurück zum Beispiel <!-- .element: class="hidden" -->
<!-- .slide: data-background-image="images/merge-001.png" data-background-size="contain" -->
<!-- Note -->
* 3 Systeme für Controller von OpenStack
* 3 Systeme für Netzwerk von OpenStack
* 10 Systeme für Ressourcen von OpenStack
* 3 Systeme für Controller von Ceph
* 10 Systeme für Ressourcen von Ceph


<!-- .slide: data-background-image="images/merge-006.png" data-background-size="contain" -->
<!-- Note -->
Jeder Compute Node erhält etwas mehr Arbeitsspeicher und ein paar mehr Cores. Zusätzlich noch
die HDDs, welche ansonsten in den Storage Nodes von Ceph verbaut worden wären.

* Memory wird je System um 64 GByte erweitert
* 10 oder 12 Cores statt 8 Cores je Socket


## Einsparungen

* 19 Bare-metal Systeme weniger und 19 unbelegte Höheneinheiten <!-- .element: class="fragment" -->
* 38 freie PDUs und 38 eingesparte C13 Kabel <!-- .element: class="fragment" -->
* 57 freie 1 GBit Ports und 57 eingesparte CAT 6 Kabel <!-- .element: class="fragment" -->
* 19 freie 10/25/40 GBit Ports und 38 eingesparte Transceiver und 19 LWL Kabel <!-- .element: class="fragment" -->

<!-- Note -->
Neben der deutlichen Reduzierung der Bare-metal Systeme und den draus resultierenden Einsparungen
in Form von Kabeln, Platz im Rack und Transceivern wird auch im Betrieb deutlich gespart. Weniger
Systeme bedeuten weniger Aufwand im Betrieb.


## Was muss man beachten?


<!-- .slide: data-background-image="images/strip_0661.jpg" data-background-size="contain" -->

<!-- Note -->
Für jedes Teilsystem (Ceph + OpenStack) müssen Ressourcen reserviert werden.

Dies muss bei der Beschaffung entsprechend berücksichtigt werden. Sollen z.B. 256 GByte Memory für
virtuelle Systeme in einem System nutzbar sein muss man im System entsprechend mind. 256 GByte + 32 GByte (besser 64 GByte)
Memory verbauen. 64 GByte Memory werden dann für die Nutzung für das Operating System + Ceph reserviert.

Gleiches gilt bei den Cores. Wenn man 2 Sockets mit 8 Cores hat müssen 4 Cores für Operating System + Ceph
vorgesehen werden.

Die Graphik stammt von Ralph Ruthe (https://ruthe.de/), einem begnadetem Witzbildmaler.


<!-- .slide: data-background-image="images/strip_0447.jpg" data-background-size="contain" -->

<!-- Note -->
In bestimmten Situationen kann sich ein Teilsystem (Ceph) auf ein anderes Teilsystem (OpenStack)
auswirken und es kann dann zu leichten Beeinträchtigungen kommen. Dies ist zum Beispiel der Fall wenn
ein System vollständig ausfällt und ausgelöst werden muss. Dann kommt es innerhalb von Ceph zu Umplazierungen
von Objekten, welche viel Last auf CPU, Memory und Netzwerk verursachen. Durch entsprechende Priorisierung
lassen sich die Auswirkungen auf den Endanwender reduzieren.

Die Graphik stammt von Ralph Ruthe (https://ruthe.de/), einem begnadetem Witzbildmaler.
