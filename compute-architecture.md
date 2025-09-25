---

copyright:
  years: 2025
lastupdated: "2025-09-25"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for compute
{: #compute-decisions}



| Architecture decision| Requirement| Options |Decision| Rationale|
|-|-|-|-|-|
|Virtualized instances platform| Provide a single orchestration platform for deploying, managing, and scaling both virtual machines and container instances | Cloud IaaS virtual instances \n IBM Cloud OpenShift Virtualization | IBM Cloud OpenShift Virtualization | Unified control plane eliminating seperate hypervisor and toolchains. \n Consistent DevOps workflows by sharing OpenShift CI/CD, image registry and GitOps pipelines for both virtual machines and container images. \n Dynamic scaling using live migration and auto-scaling|
|Workload isolation compliance| Maintain current production environment operational isolation and compliance boundaries | Seperate production worker node pool \n Seperation OpenShift Cluster for production | Seperate OpenShift Cluster for production | Full plane isolation for dedicated control plane, etcd and audit streams. \n Network segmentation with production VPC using subnets and security groups to mirror VMware vlans   |
|Virtualization| text | text | text | text |
|Containers| text | text | text | text |
|Serverless| text | text | text | text |
{: caption="Table 1. Architecture decisions for compute" caption-side="bottom"}
