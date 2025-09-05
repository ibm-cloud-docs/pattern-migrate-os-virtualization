---

copyright:
  years: 2025
lastupdated: "2025-09-05"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for compute
{: #compute-decisions}



| Architecture decision| Requirement| Options |Decision| Rationale|
|-|-|-|-|-|
|Virtualized instances platform| Provide a single orchestration platform for deploying, managing, and scaling both virtual machines and container instances | 1. Cloud IaaS virtual instances \n 2. IBM Cloud Cloud Virtualization | IBM Cloud OpenShift Virtualization | Unified control plane eliminating seperate hypervisor and toolchains. \n Consistent DevOps workflows by sharing OpenShift CI/CD, image registry and GitOps pipelines for both virtual machines and container images. \n Dynamic scaling using live migration and auto-scaling|
|Virtual servers| text | text | text | text |
|Virtualization| text | text | text | text |
|Containers| text | text | text | text |
|Serverless| text | text | text | text |
{: caption="Table 1. Architecture decisions for compute" caption-side="bottom"}
