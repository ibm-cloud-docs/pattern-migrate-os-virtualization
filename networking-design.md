---

copyright:
  years: 2025
lastupdated: "2025-08-28"

keywords: virtualization, VMware, SDN, NSX, OpenShift

subcollection: pattern-migrate-vmware-workloads-redhat-openshift-virtualization

authors:
  - name: Esteban Arias
    url: https://linkedin.com/in/eariasn01

version: 1.0

deployment-url: url

use-case: virtualization, hypervisor, migration, containers
industry: FinancialSector, Manufacturing, Retail, Industrials, Communications
compliance: 
content-type: deployment

production: false

---

{{site.data.keyword.attribute-definition-list}}

# Network design
{: #network-design}

The underlying architecture utilizes an existing deployment of a Red Hat OpenShift cluster with bare metal worker nodes on IBM Cloud, within a Virtual Private Cloud (VPC) environment. The VPC is configured within a specific region and organized under a designated resource group. OpenShift is deployed within the VPC and spread across a zone, hosting multiple Bare Metal Worker Nodes.

Networking functionality includes integration with the cluster's native software-defined networking (SDN) stack, enabling secure and policy-driven connectivity to virtual machines via programmable network policies. This supports granular control over VM ingress and egress traffic, aligning with enterprise-grade security and compliance requirements. Additionally, the platform provides support for traditional networking mechanisms, including Open vSwitch (OVS) for VM attachment to VLAN-backed and other overlay or underlay networks, SR-IOV for high-performance network interfaces, and OpenShift’s user-defined networking (UDN) as a flexible, evolving alternative for custom network topologies.

More specifically virtual machines have many options for network connectivity:
- OVN-Kubernetes (default)
- Service mesh when deployed.
- Linux bridge / Open vSwitch direct external connectivity.
- SR-IOV and DPDK adapter based connectivity.

In Migration Toolkit for Virtualization (MTV), virtual machine migrations are orchestrated via a migration plan which is a declarative configuration that enumerates the source VMs and defines explicit mappings between vSphere constructs (networks and datastores) and their OpenShift Virtualization counterparts (networks and StorageClasses). These mappings are mandatory because the MTV controller lacks the contextual awareness to infer appropriate target resources, necessitating manual specification to ensure fidelity and compatibility during migration.

Red Hat OpenShift implements a distinct networking model centered around a dedicated pod network, which isolates microservices within the cluster. Application traffic is managed through software-defined abstractions known as Services, which act as internal load balancers. These Services are discoverable within the cluster and can be externally exposed via Routes, which bind DNS names to ingress traffic. This architecture decouples service identity from underlying network topology, rendering static IP addresses irrelevant. Instead, OpenShift dynamically manages service-to-pod relationships, ensuring high availability and scalability through its integrated SDN and routing mechanisms

# Virtual machine configuration
{: #virtual-machine-configuration}

Red Hat Enterprise Linux (RHEL), leveraging the udev device manager and the underlying Linux kernel, assigns network interface names based on a set of deterministic rules derived from hardware topology and driver characteristics. For instance, on a RHEL 9 system running within a VMware environment, a NIC utilizing the VMXNET driver may be enumerated as ens192, reflecting predictable naming conventions introduced by systemd and udev to replace legacy ethX identifiers.

When migrating to OpenShift Virtualization using the Migration Toolkit for Virtualization (MTV), the same server may transition from using the VMXNET driver under VMware to the VirtIO driver within the KVM-based OpenShift environment. As a result, the network interface may be enumerated differently—such as enp1s0—reflecting the PCI bus topology and naming conventions applied by udev.

## Update methods
{: #NetworkManager}
1. Network Manager cloning: Using this method system administrators create a clone of the existing virtual machine networking interface (ens192 for VMware) to the corresponding name in OpenShift Virtualization (enp1s0) and then proceed to migrate, this method assumes that IP address and MAC are the same before and after the migration.
2. Kernel boot parameters: Customizing network interface naming in Red Hat Enterprise Linux requires modifying kernel boot parameters to define a specific prefix for the NIC name. As detailed in the Red Hat Knowledgebase, it's critical to avoid using prefixes that conflict with udev's predictable naming conventions—such as eth, ens, em, or eno—to prevent naming collisions and ensure consistent interface enumeration across reboots. An example would be:  #grubby --update-kernel=ALL --args="net.ifnames.prefix=nic_net", then you can clone the pre-migration network connection (ens192) to the new configuration nic_net0. The final step would be to modify the active network connection to be nic_net0 to be active and reboot the virtual machine.
