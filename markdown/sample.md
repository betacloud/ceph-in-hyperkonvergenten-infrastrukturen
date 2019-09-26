# Beispiel


## Ressourcen

* 2 TByte Memory <!-- .element: class="fragment" -->
* 100 TByte Storage <!-- .element: class="fragment" -->
* 500 vCPUs <!-- .element: class="fragment" -->
<!-- Note -->
Skizze von einer üblichen Kundenanforderung für die Bereitstellung von einer kleinen Infrastructure as a Service Umgebung.


## Redundanz

* Redundante Ressourcen <!-- .element: class="fragment" -->
* Redundante Controller <!-- .element: class="fragment" -->
* Redundantes Netzwerk <!-- .element: class="fragment" -->


## Umsetzung <!-- .element: class="hidden" -->

<!-- .slide: data-background-image="images/merge-overview-001.png" data-background-size="contain" -->


<!-- .slide: data-background-image="images/merge-overview-002.png" data-background-size="contain" -->
<!-- Note -->
* 10 Systeme für Ressourcen von OpenStack
  * 256 GByte Memory + 2 Sockets mit je 8 Cores
  * insgesamt 2560 GByte Memory und 160 Cores (ohne Hyperthreading)


<!-- .slide: data-background-image="images/merge-overview-003.png" data-background-size="contain" -->
<!-- Note -->
* 3 Systeme für Netzwerk von OpenStack


<!-- .slide: data-background-image="images/merge-overview-004.png" data-background-size="contain" -->
<!-- Note -->
* 3 Systeme für Controller von OpenStack


<!-- .slide: data-background-image="images/merge-overview-005.png" data-background-size="contain" -->
<!-- Note -->
* 10 Systeme für Ressourcen von Ceph
  * 8 HDDs mit je 4 TByte
  * insgesamt 320 TByte Storage (ohne Beachtung der Redundanz)


<!-- .slide: data-background-image="images/merge-overview-006.png" data-background-size="contain" -->


## Material- und Platzbedarf

* 29 Bare-metal Systeme <!-- .element: class="fragment" -->
  * 29 belegte Höheneinheiten
* 58 belegte PDUs <!-- .element: class="fragment" -->
  * 58 C13 Kabel
* 29 (OOB) + 58 (Management) = 87 belegte 1 GBit Ports <!-- .element: class="fragment" -->
  * 87 Cat.6 Kabel
* 58 belegte 10/25/40 GBit Ports <!-- .element: class="fragment" -->
  * 116 Transceiver und 58 LWL Kabel
  * oder 58 DAC Kabel
