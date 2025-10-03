---
copyright:
  years: 2025
lastupdated: "2025-10-03"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for compute
{: #compute-decisions}

The following table summarizes the compute architecture decisions for the Migrate VMware to IBM Cloud Red Hat OpenShift Virtualization deployment guide.

| Architecture decision                   | Requirement                                                                                                                | Options                                                                                                    | Decision                                   | Rationale                                                                                                                                                                                                                                                                                                     |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Virtualization         | Provide a single orchestration platform for deploying, managing, and scaling both virtual machines and container instances | IBM Cloud IaaS virtual instances with Red Hat OpenShift for containers \\n IBM Cloud Red Hat OpenShift Virtualization      | IBM Cloud Red Hat OpenShift Virtualization         | Unified control plane, which eliminates separate workload orchestration and scheduling \\n Consistent DevSecOps workflows for both virtual machines and containers, by sharing Red Hat OpenShift CI/CD, image registry and GitOps pipelines. \\n Dynamic resource balancing by using live migration to optimize compute utilization |
| Compliant production workload isolation | Maintain current VMware production operational isolation and compliance boundaries                                         | Separate production worker node pool \\n Separate Red Hat OpenShift Cluster for production \\n Red Hat OpenShift Projects  | Separate Red Hat OpenShift Cluster for production  | Full control plane isolation with dedicated etcd and audit streams.                                                                                                                                                                                                                                           |
| Virtual machine density                 | Optimize virtualization operational costs                                                                                  | {{site.data.keyword.vpc_short}} bare metal worker node flavors                                                                 | High cores (+36c) and high memory (+512 GB) physical flavor | Optimize per VM costs.                                                                                                                                                                                                                                                                                        |
| Worker pool                             | Optimize worker pool                                                                                                       | Mix container and virtual machines \\n Separate container and virtual machine worker pools                 | Separate worker pools for virtual machines | Containers and virtual machines have distinct resource profiles. Containers require fast scaling and lightweight scaling. Virtual machines require stable cpu and memory allocation. Allows for placement of workload to tuned worker pool.                                                                   |
{: caption="Table 1. Architecture decisions for compute" caption-side="bottom"}
