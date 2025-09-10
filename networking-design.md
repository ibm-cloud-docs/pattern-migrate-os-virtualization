---
copyright:
  years: 2025
lastupdated: "2025-09-10"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Network Design
{: #network-design}

## Key Networking Design Considerations for Migrating VMware Workloads to OpenShift Virtualization
### 1. Network Segmentation and Traffic Separation
- Use **VLANs** to isolate management, storage, and VM data traffic for enhanced security and performance.
- Configure **dedicated network interfaces or bridges** for VM traffic to avoid interference with cluster operations.
- Leverage **NodeNetworkConfigurationPolicy** with **OVS bridges** for granular control over VM networking.

---

### 2. MTU Configuration and Link Aggregation
- Ensure consistent **MTU settings** across all interfaces to prevent packet fragmentation.
- Implement **Link Aggregation Control Protocol (LACP)** to boost bandwidth and provide redundancy.
- Test MTU compatibility between OpenShift nodes and external systems before migration.

---

### 3. VLAN Trunking and Overlay Networking
- Use **VLAN trunking** to enable VMs to connect to multiple networks.
- Choose between **overlay networking** (for isolated environments) and **localnet topology** (for direct access to physical networks) based on workload requirements.
- Align OpenShift networking models with existing VMware configurations to ensure seamless integration.

---

### 4. NIC and CNI Plugin Selection
- Prefer **VirtIO NICs** for performance and compatibility with OpenShift Virtualization.
- Use **OVN-Kubernetes CNI** for advanced networking features like policy enforcement and multi-network support.

---

### 5. IP Address Management and DNS Integration
- Plan for **IPAM** (IP Address Management) to avoid conflicts and ensure scalability.
- Optionally use **DHCP** (standard network protocol used to automate the process of assigning IP addresses and other configuration details to devices within a network)
- Integrate with existing **DNS infrastructure** to maintain name resolution consistency across platforms.


<<<<<<< HEAD
=======
The underlying architecture utilizes an existing deployment of a Red Hat OpenShift cluster with bare metal worker nodes on IBM Cloud, within a Virtual Private Cloud (VPC) environment. The VPC is configured within a specific region and organized under a designated resource group. OpenShift is deployed within the VPC and spread across a zone, hosting multiple Bare Metal Worker Nodes.

Networking functionality includes integration with the cluster's native software-defined networking (SDN) stack, enabling secure and policy-driven connectivity to virtual machines via programmable network policies. This supports granular control over VM ingress and egress traffic, aligning with enterprise-grade security and compliance requirements. Additionally, the platform provides support for traditional networking mechanisms, including Open vSwitch (OVS) for VM attachment to VLAN-backed and other overlay or underlay networks, SR-IOV for high-performance network interfaces, and OpenShift’s user-defined networking (UDN) as a flexible, evolving alternative for custom network topologies.

More specifically virtual machines have many options for network connectivity:
- OVN-Kubernetes (default)
- Service mesh when deployed.
- Linux bridge / Open vSwitch direct external connectivity.
- SR-IOV and DPDK adapter based connectivity.

In Migration Toolkit for Virtualization (MTV), virtual machine migrations are orchestrated via a migration plan which is a declarative configuration that enumerates the source VMs and defines explicit mappings between vSphere constructs (networks and datastores) and their OpenShift Virtualization counterparts (networks and StorageClasses). These mappings are mandatory because the MTV controller lacks the contextual awareness to infer appropriate target resources, necessitating manual specification to ensure fidelity and compatibility during migration.

Red Hat OpenShift implements a distinct networking model centered around a dedicated pod network, which isolates microservices within the cluster. Application traffic is managed through software-defined abstractions known as Services, which act as internal load balancers. These Services are discoverable within the cluster and can be externally exposed via Routes, which bind DNS names to ingress traffic. This architecture decouples service identity from underlying network topology, rendering static IP addresses irrelevant. Instead, OpenShift dynamically manages service-to-pod relationships, ensuring high availability and scalability through its integrated SDN and routing mechanisms

>>>>>>> b43aa38f0f3542b4e292e3e681824acc54f9ca9d
