# Beispiel


## Anforderung <!-- .element: class="hidden" -->

* Bereitgestellte Ressourcen
  * 2 TByte Memory
  * 100 TByte Storage
  * 500 vCPUs
* Redundante Controller <!-- .element: class="fragment" -->
* Redundantes Netzwerk <!-- .element: class="fragment" -->
* Redundante Ressourcen <!-- .element: class="fragment" -->

<!-- Note -->
Skizze von einer üblichen Kundenanforderung für die Bereitstellung von einer Infrastructure as a Service Umgebung


## Umsetzung <!-- .element: class="hidden" -->

* 3 Systeme für Controller von OpenStack
* 3 Systeme für Netzwerk von OpenStack <!-- .element: class="fragment" -->
* 3 Systeme für Controller von Ceph <!-- .element: class="fragment" -->

<!-- Note -->
Skizze von einer vollausgebauten Umgebung mit unabhänagigen Teilsystemen zur vorherigen Kundenanforderung


* 10 Systeme für Ressourcen von OpenStack
  * 256 GByte Memory + 2 Sockets mit je 8 Cores
  * insgesamt 2560 GByte Memory und 160 Cores (ohne Hyperthreading)
* 10 Systeme für Ressourcen von Ceph <!-- .element: class="fragment" -->
  * 8 HDDs mit je 4 TByte
  * insgesamt 320 TByte Storage (ohne Beachtung der Redundanz)


* 29 Bare-metal Systeme
  * 29 belegte Höheneinheiten
* 58 belegte PDUs <!-- .element: class="fragment" -->
  * 58 C13 Kabel
* 29 (OOB) + 58 (Management) = 87 belegte 1 GBit Ports <!-- .element: class="fragment" -->
  * 87 Cat.6 Kabel
* 58 belegte 10/25/40 GBit Ports <!-- .element: class="fragment" -->
  * 116 Transceiver und 58 LWL Kabel
  * oder 58 DAC Kabel
