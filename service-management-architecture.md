---
copyright:
  years: 2023
lastupdated: "2023-12-18"

subcollection: pattern-migrate-os-virtualization

keywords:

---

# Architecture decisions for service management

{: \#service}

The following sections summarize the architecture decisions for service management for the migrating VMware workloads to IBM Cloud OpenShift pattern.

| Architecture decision | Requirement                                                                                                                                                                         | Option                                                              | Decision             | Rationale                                                                                                                                                                     |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Monitoring            | Monitor Openshift Virtualization Clusters, Worker Nodes, Virtual instances and Containers health to detect issues that might impact the availability and compliance of the workload | - IBM Cloud Monitoring \\n – Promotheus and Grafana (self managed)l | IBM Cloud Monitoring | IBM Cloud Monitoring collects and monitors operational metrics for cloud infrastructure as well as the cloud platform and services and provides a single view for all metrics |

{: caption="Table 1. Architecture decisions for service management" caption-side="bottom"}
