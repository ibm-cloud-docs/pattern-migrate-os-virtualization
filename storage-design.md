---

copyright:
  years: 2023
lastupdated: "2023-12-26"

subcollection: pattern-sap-on-vpc

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Storage design
{: #storage-design}

A successful deployment of Red Hat OpenShift Virtualization requires careful planning, particularly around storage for virtual machines (VMs). Key requirements include support for live migration, provisioning, expansion, backup, disaster recovery, and scalability—most of which depend on the Container Storage Interface (CSI). Selecting the right storage solution therefore involves evaluating the capabilities of the CSI driver in use.

Below are the main architectural approaches: 
-	**External Storage via Container Storage Interface (CSI) Driver:** This approach uses external SAN or NAS storage, with vendor-specific CSI drivers handling provisioning and lifecycle operations. It provides low latency by directly connecting VMs to storage arrays. However, adoption may be limited by the absence of ReadWriteMany (RWX) support for block volumes or advanced Container Storage Interface (CSI) features (cloning, snapshots, expansion) in some drivers, as well as operational complexity from managing large numbers of volumes at scale.
-	**Internal Storage with Software-defined storage (SDS):**
In this approach, storage resides within the Red Hat OpenShift Virtualization cluster and is managed by Software-defined storage (SDS). Deployments can be hyperconverged (all nodes as storage nodes) or partially converged (only some nodes as storage nodes), with the latter offering more flexible scaling of compute and storage. There are multiple Software-defined storage (SDS) solutions such as IBM Fusion Storage, and Portworx integrate well with Red Hat OpenShift, though they place storage management responsibility on the platform team, adding operational complexity. Mature Software-defined storage (SDS) operators can minimize the operational challenges for platform teams.
-	**Shared-Disk file systems:**
Shared-disk file systems enhance SAN efficiency by creating a single LUN accessible to multiple cluster nodes. Using the Container Storage Interface (CSI) driver in Red Hat OpenShift Virtualization, VM orchestrators can provision disks directly on this file system. VMs then connect straight to the storage without extra software layers, delivering near-native performance. This approach is ideal for medium-sized clusters, with supported solutions including IBM Fusion Access for SAN and Cloud Software Group’s Arctera Operator.

IBM Cloud provides a suite of managed add-ons for Red Hat OpenShift clusters, designed to enhance cluster capabilities, simplify management, and streamline integration with enterprise environments. These add-ons are fully tested, supported, and billed through IBM Cloud, ensuring that enabling an add-on automatically deploys a supported version of the tool, including all required Kubernetes resources, directly within the cluster.

For storage solutions, IBM Cloud offers a comprehensive set of options optimized for Red Hat OpenShift Virtualization and VPC environments:
-	**IBM Storage Operator** – Automates provisioning, configuration, scaling, and lifecycle management of IBM storage resources within OpenShift, integrating seamlessly with Kubernetes-native workflows.
-	**OpenShift Data Foundation (ODF)** – Provides a fully software-defined storage platform supporting block, file, and object storage. Key features include replication, erasure coding, snapshots, and self-healing, delivering persistent storage for both containerized workloads and virtual machines.
-	**Block Storage for VPC** – Delivers high-performance, low-latency block volumes ideal for databases, stateful applications, and VMs. Supports dynamic volume expansion, cross-zone replication, snapshots, and encryption at rest.
-	**File Storage for VPC** – Offers network-attached storage with NFS protocol support, enabling concurrent access across multiple VPC instances. Features include high availability, scalable capacity, snapshots, replication, and fine-grained access control for enterprise workloads.

These managed add-ons enable enterprises to efficiently deploy and manage storage and infrastructure capabilities while leveraging the automation and resilience of OpenShift and IBM Cloud.
