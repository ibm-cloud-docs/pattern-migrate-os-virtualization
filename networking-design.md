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
