# Konfiguration

* CPU Pinning <!-- .element: class="fragment" -->
* NUMA Node Pinning <!-- .element: class="fragment" -->
* Memory Limits für Dienste <!-- .element: class="fragment" -->
* Reservierung von CPU und Memory <!-- .element: class="fragment" -->
* Anpassung der CPU Allocation Ratio <!-- .element: class="fragment" -->

<!-- Note -->
In ceph-ansible gibt es mittlerweile spezielle Konfigurationsparameter für HCI:

```yaml
is_hci: true
hci_safety_factor: 0.2
non_hci_safety_factor: 0.7
```

Dadurch wird der ``osd memory target`` Parameter in Abhängigkeit des zur Verfügung stehenden Memorys berechnet.

In ceph-ansible können CPU/Memory Limits sowie CPU/NUMA Node Pinning über spezielle Konfigurationsparameter gestzt werden:

```yaml
ceph_osd_docker_memory_limit: "8192m"
ceph_osd_docker_cpu_limit: 1
ceph_osd_docker_cpuset_cpus: "0,2,4,6,8,10,12,14,16"
ceph_osd_docker_cpuset_mems: "0"
```

In Ceph sollten noch diverse Paremter angepasst werden um bei Recovery/Backfill Operationen die Last zu reduzieren.

```
osd recovery op priority: 3  1
osd_recovery_max_active: 3  2
osd_max_backfills: 1  3
```

Auf einem Nova Compute Node können vCPUs an bestimmte CPUs gepinnt werden und CPU/Memory reserviert werden. Reservierung heisst sie werden
beim Reporting der verfügbaren Ressourcen von der Gesamtmenge abgezogen.

```ini
[DEFAULT]
vcpu_pin_set=1,3,5,...
reserved_host_memory_mb=32768
reserved_host_cpus=4
````

Unabhängig von der Reservierung ganzer Cores kann auch die CPU Allocation Ration auf Nova Compute Nodes in Abhängigheit
der erwarteten Beanspruchung durch Instanzen gesetzt werden.

Dazu findet sich die nachfolgende Formel in einer Dokumentation
(https://access.redhat.com/documentation/en-us/red_hat_openstack_platform/13/html-single/hyper-converged_infrastructure_guide/index#appendix-upstream-cpuram)
von RedHat. Dort ist auch direkt ein Skript für die Berechnung vorhanden.

```
cores_per_OSD = 1.0
average_guest_util = 0.1 # 10%
nonceph_cores = cores - (cores_per_OSD * osds)
guest_vCPUs = nonceph_cores / average_guest_util
cpu_allocation_ratio = guest_vCPUs / cores
```
