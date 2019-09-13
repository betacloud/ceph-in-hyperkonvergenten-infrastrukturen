# Hyperkonvergente Infrastruktur

<!-- Note -->
Kurze Einführung in das Thema hyperkonvergente Infrastruktur


<blockquote cite="https://en.wikipedia.org/wiki/Hyper-converged_infrastructure">
Hyper-converged infrastructure (<span class="fragment highlight-current-red">HCI</span>) is a
<span class="fragment highlight-current-red">software-defined IT infrastructure</span> that
<span class="fragment highlight-current-red">virtualizes all of the elements of conventional
"hardware-defined" systems</span>.
</blockquote>

<!-- Note -->
* die Abkürzung von "hyper-converged infrastructure" ist HCI
* HCI ist eine durch Software definierte IT Infrastruktur
* Virtualisierung von in traditionellen Umgebungen durch Hardware bereitgestellten Komponenten

Diese Definition stammt von https://en.wikipedia.org/wiki/Hyper-converged_infrastructure.


<blockquote cite="https://en.wikipedia.org/wiki/Hyper-converged_infrastructure">
HCI includes, at a minimum, <span class="fragment highlight-current-red">virtualized computing (a hypervisor)</span>, a <span class="fragment highlight-current-red">virtualised SAN (software-defined storage)</span> and <span class="fragment highlight-current-red">virtualized networking (software-defined networking)</span>.
</blockquote>

<!-- Note -->
* Virtualisierung von Systemen z.B. durch KVM, Xen, Hyper-V, VMware
* Software Defined Storage (SDS)
* Software Defined Networking (SDN)

Diese Definition stammt von https://en.wikipedia.org/wiki/Hyper-converged_infrastructure.


## Software Defined Storage <!-- .element: class="hidden" -->

<img src="images/Ceph_Logo_Standard_RGB_120411_fa.png" style="width: 60%" class="plain"/>

<!-- Note -->
Als Software Defined Storage wird im Zusammenspiel mit OpenStack häufig auf Ceph gesetzt.


## Software Defined Networking <!-- .element: class="hidden" -->

<img src="images/Open_vSwitch_Logo.svg" style="width: 30%" class="plain" />

<!-- Note -->
Als Software Defined Networking wird im Zusammenspiel mit OpenStack gewöhnlich auf Open vSwitch gesetzt.


## Virtualisierung <!-- .element: class="hidden" -->

<img src="images/Kvmbanner-logo2_1.png" style="width: 40%" class="plain" />

<!-- Note -->
Für die Virtualisierung auf Linux wird KVM genutzt. Für die Ansteuerung von KVM wird Libvirt verwendet.


## OpenStack <!-- .element: class="hidden" -->

<img src="images/OpenStack-Logo-Horizontal.SVG" style="width: 50%" class="plain" />


<!-- .slide: data-background-image="images/openstack-overview.svg" data-background-size="contain" -->

<!-- Note -->
OpenStack wird als Layer über Ceph, Open vSwitch und KVM für die Ansteuerung genutzt. Dadurch entsteht
eine Infrastructure as a Service (IaaS) Umgebung. Darüber kann über standardisierte APIs eine Ansteuerung
der unterliegenden Ressourcen erfolgen.

Die Graphik wird von der OpenStack Foundation zur Verfügung gestellt und ist unter https://www.openstack.org/software/
verfügbar.


<!-- .slide: data-background-image="images/openstack-map-v20190601.svg" data-background-size="contain" -->

<!-- Note -->
OpenStack stellt nicht nur IaaS Dienste zur Verfügung.

Die Graphik wird von der OpenStack Foundation zur Verfügung gestellt und ist unter https://www.openstack.org/software/
verfügbar.

Die zugrundeliegenden Daten der Graphik sind unter https://github.com/openstack/openstack-map abgelegt.
