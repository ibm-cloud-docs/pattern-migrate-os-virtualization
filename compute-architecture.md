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

| Architecture decision                   | Requirement                                                                                                                | Options                                                                                                    | Decision                                   | Rationale                                                                                                                                                                                                                                                                                                     |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute Virtualization Platform         | Provide a single orchestration platform for deploying, managing, and scaling both virtual machines and container instances | IBM Cloud IaaS virtual instances with OpenShift for containers \\n IBM Cloud OpenShift Virtualization      | IBM Cloud OpenShift Virtualization         | Unified control plane eliminating separate workload orchestration and scheduling \\n Consistent DevSecOps workflows by sharing OpenShift CI/CD, image registry and GitOps pipelines for both virtual machines and container images. \\n Dynamic resource balancing using live migration, descheduler operator |
| Compliant production workload isolation | Maintain current VMware production operational isolation and compliance boundaries                                         | Separate production worker node pool \\n Seperate OpenShift Cluster for production \\n OpenShift Projects  | Separate OpenShift Cluster for production  | Full control plane isolation with dedicated Etcd and audit streams.                                                                                                                                                                                                                                           |
| Virtual machine density                 | Optimize virtualization operational costs                                                                                  | IBM Cloud VPC physical worker node flavors                                                                 | High cores (+96) and high memory (+768 GB) | Optimize per VM costs.                                                                                                                                                                                                                                                                                        |
| Worker pool                             | Optimize worker pool                                                                                                       | Mix container and virtual machines \\n separate container and virtual machine worker pools                 | Separate worker pools for virtual machines | Containers and virtual machines have distinct resource profiles. Containers require fast scaling and lightweight scaling. Virtual machines require stable cpu and memory allocation. Allows for placement of workload to tuned worker pool.                                                                   |
{: caption="Table 1. Architecture decisions for compute" caption-side="bottom"}
