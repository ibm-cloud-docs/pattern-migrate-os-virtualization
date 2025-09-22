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

| Architecture decision                                         | Requirement                                                                                              | Option                                           | Decision             | Rationale                                                                                                                                                                     |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|--------------------------------------------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operational monitoring of OpenShift Clusters and Worker Nodes | Monitor system health to detect issues that might impact the availability of the system and application. | - IBM Cloud Monitoring \\n - BYO Monitoring Tool | IBM Cloud Monitoring | IBM Cloud Monitoring collects and monitors operational metrics for cloud infrastructure as well as the cloud platform and services and provides a single view for all metrics |

{: caption="Table 1. Architecture decisions for service management" caption-side="bottom"}
