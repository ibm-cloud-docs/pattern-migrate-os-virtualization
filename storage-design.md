---

copyright:
  years: 2025
lastupdated: "2025-10-03"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Storage design
{: #storage-design}

A successful deployment of Red Hat OpenShift Virtualization requires careful planning, particularly around storage for virtual machines (VMs). Key requirements include support for live migration, provisioning, expansion, backup, disaster recovery, and scalability, most of which depend on the Container Storage Interface (CSI). Selecting the right storage solution, therefore, involves evaluating the capabilities of the CSI driver in use.

These are the main architectural approaches:

-	**External Storage using Container Storage Interface (CSI) Driver:** This approach uses external SAN or NAS storage, with vendor-specific CSI drivers that handle provisioning and lifecycle operations. It provides low latency by directly connecting VMs to storage arrays. However, adoption might be limited by the absence of ReadWriteMany (RWX) support for block volumes or advanced Container Storage Interface (CSI) features (cloning, snapshots, expansion) in some drivers, as well as operational complexity from managing large numbers of volumes at scale.

-	**Internal Storage with Software-defined storage (SDS):** In this approach, storage that resides within the Red Hat OpenShift Virtualization cluster and is managed by Software-defined storage (SDS). Deployments can be hyperconverged (all nodes as storage nodes) or partially converged (only some nodes as storage nodes), with the latter offering more flexible scaling of compute and storage. Multiple software-defined storage (SDS) solutions such as IBM Fusion Storage are available. Portworx also integrates well with Red Hat OpenShift, though they place storage management responsibility on the platform team, adding operational complexity. Mature Software-defined storage (SDS) operators can minimize the operational challenges for platform teams.

IBM Cloud provides a suite of managed add-ons for Red Hat OpenShift clusters, which are designed to enhance cluster capabilities, simplify management, and streamline integration with enterprise environments. These add-ons are fully tested, supported, and billed through IBM Cloud, helping ensure that enabling an add-on automatically deploys a supported version of the tool, including all required Kubernetes resources, directly within the cluster.

For storage solutions, IBM Cloud offers a comprehensive set of options optimized for Red Hat OpenShift Virtualization and VPC environments:

**Key IBM Cloud Managed Storage Add-Ons:**
{: #ibm-cloud-managed-add-ons}

| **Add-Ons** | **Description** | **Key Features** |
| -------------- | -------------- | -------------- |
| **IBM Storage Operator** | Automates storage provisioning and lifecycle management within Red Hat OpenShift | Kubernetes-native workflows, scaling, configuration, automation |
| **Block Storage for VPC** | High-performance block volumes for databases, stateful apps, and VMs | Dynamic expansion, cross-zone replication, snapshots, encryption at rest |
| **File Storage for VPC** | Network-attached storage with NFS support, enabling concurrent access across multiple VPC instances | High availability, scalable capacity, snapshots, replication, access control |
| **Red Hat OpenShift Data Foundation (ODF)** | Software-defined storage, which supports block, file, and object storage | Replication, erasure coding, snapshots, self-healing, persistent storage for containers and VMs |
{: caption="IBM Cloud Managed Storage Add-Ons" caption-side="bottom"}

These managed add-ons enable enterprises to efficiently deploy and manage storage and infrastructure capabilities, while using the automation and resilience of Red Hat OpenShift and IBM Cloud.

**References:**
{: #references}

[Enable or Disable the IBM managed Storage Add-Ons](/docs/openshift?topic=openshift-storage-operator&interface=ui)

[IBM Cloud Block Storage for VPC Cluster](/docs/openshift?group=setting-up-block-storage-for-vpc)

[IBM Cloud File Storage for VPC Cluster](/docs/openshift?group=setting-up-file-storage-for-vpc)

[Red Hat OpenShift Data Foundation for VPC Cluster](/docs/openshift?group=setting-up-openshift-data-foundation)
