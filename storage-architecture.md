---

copyright:
  years: 2025
lastupdated: "2025-09-29"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for storage
{: #storage-decisions}



| Architecture decision| Requirement| Option | Decision| Rationale|
|-|-|-|-|-|
| Primary Storage for worker nodes | The set of disk resources required for a worker node’s core functionality, encompassing the boot volume, operating system installation, and local container runtime file systems. | Local disk | Local disk | Provision worker nodes on VPC bare-metal servers with enough local storage for the operating system, and configure disks in RAID 1 for redundancy and performance |
| Storage for virtual machines on Red Hat OpenShift Virtualization on IBM Cloud | It is advisable to provision a highly available, performance-optimized storage infrastructure to ensure consistent reliability, fault tolerance, and optimal throughput for hosting diverse virtual machine workloads. | [Block Storage for VPC](https://test.cloud.ibm.com/docs/vpc?topic=vpc-storage-overview) \n [File Storage for VPC](https://cloud.ibm.com/docs/vpc?topic=vpc-file-storage-vpc-about) | Read-Write-Once (RWO): \n Block Storage for VPC \n Read-Write-Many (RWM): \n File Storage  | Provision block storage with appropriate IOPS for workloads requiring Read-Write-Many (RWM) operations, and utilize file storage for workloads with Read-Write-Once (RWO) access. This ensures optimal performance, cost efficiency, and alignment with workload access patterns. \n ROKS provides persistent storage options to support virtual machine (VM) workloads. Administrators must provision block storage volumes for VM disks to ensure reliable performance and data persistence. These volumes can be dynamically resized, managed, and attached to VM instances in accordance with OpenShift Virtualization and IBM Cloud storage best practices. |
|Storage for virutal machines with zone-level resilience to ensure high availability and fault tolerance for virtual machine workloads. | Integrates compute and storage on the same nodes, providing persistent, high-availability storage for VMs and containers. Leverages software-defined storage for scalability, performance, fault tolerance, and seamless OpenShift integration, simplifying management and dynamic resource provisioning for virtualized workloads. | Converged Storage for OpenShift Virtualization | Red Hat OpenShift Data Foundation (ODF) | Converged storage in OpenShift Virtualization integrates compute and storage resources to provide a unified platform for managing virtual machine workloads. It leverages software-defined storage solutions to deliver persistent storage directly on cluster nodes, supporting VM boot volumes, data disks, and container storage needs. This approach simplifies infrastructure management, enhances performance, and ensures high availability, while maintaining compatibility with OpenShift’s storage classes and policies. |
{: caption="Architecture decisions for storage" caption-side="bottom"}
