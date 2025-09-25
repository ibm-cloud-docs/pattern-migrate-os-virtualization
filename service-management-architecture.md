---
copyright:
  years: 2023
lastupdated: "2023-12-18"

subcollection: pattern-migrate-os-virtualization

keywords:

---

# Architecture decisions for service management

{: \#service}

The following sections summarize the architecture decisions for service management, when migrating VMware workloads to IBM Cloud OpenShift Virtualization clusters using a virtualization platform modernization strategy and adopting DevSecOps work practices.

| Architecture decision | Requirement                                                                                                                                                                         | Option                                                          | Decision                      | Rationale                                                                                                                                                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Monitoring            | Monitor Openshift Virtualization Clusters, Worker Nodes, Virtual instances and Containers health to detect issues that might impact the availability and compliance of the workload | IBM Cloud Monitoring \\n Promotheus and Grafana (self managed)l | IBM Cloud Monitoring          | IBM Cloud Monitoring collects and monitors operational metrics for cloud infrastructure as well as the cloud platform and services and provides a single view for all metrics.                                    |
| Logging               | Provide observability services for IBM Cloud resources to view, analyze, and alert on activity tracking events and logging activity.                                                | IBM Cloud Logs \\n ELK self-managed \\n Fluentd self-managed    | IBM Cloud Logs                | Provides centralized log aggregation of event logs, audit logs for virtual machines, virtualization.clusters.                                                                                                     |
| Network logging       | Provide network traffic logging on the OpenShift Virtualization clusters and worker nodes.                                                                                          | IBM Cloud VPC Flow Logs \\n 3rd party network telemetry tool    | IBM Cloud VPC flow logs       | Enables granular network telemetry at the VPC level, capturing source / destination IP, ports and protocols. Integrates with IBM Cloud Logs and Monitoring.                                                       |
| Event notification    |                                                                                                                                                                                     | IBM Cloud Event notification \\n OpenShift alert manager        | IBM Cloud Event Notifications | Acts as the orchestration layer for compliance alerts, audit events and incident reporting. Enables routing to external SIEM systems (PagerDuty, Service Now, other) with policy-based filtering and escalation.  |
|                       |                                                                                                                                                                                     |                                                                 |                               |                                                                                                                                                                                                                   |
|                       |                                                                                                                                                                                     |                                                                 |                               |                                                                                                                                                                                                                   |

{: caption="Table 1. Architecture decisions for service management" caption-side="bottom"}
