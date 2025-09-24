---
copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Service management design

{: \#service-management-design}

When migrating production critical VMware workloads to IBM Cloud OpenShift Virtualization, required service management process and tooling changes will be driven by the migration program schedule and strategy.

A short-term migration program using lift and shift approach to minimize changes will focus on replacing dependant VMware tooling, such as vCenter APIs, vROps, with IBM Cloud Observability and OpenShift Virtualization APIs to manage VM lifecycle and placement.

A migration program using virtualization platform modernization approach requires a re-coding from ITIL process tooling and imperative scripting to a DevSecOps declarative model built on GitOps workflows and policy-driven automation. Legacy runbooks and ticket based operations are replaced by declarative pipelines ,version-controlled manifests and integrated security gates to align the virtualization platform with cloud-native delivery practices.

## IBM Cloud Log

{: \#log-analysis}

You can use IBM Cloud Log to add log management capabilities to Red Hat OpenShift VPC clusters and provide for the following:

-   Customizable user interface for live streaming of log tailing, real-time troubleshooting issue alerts, and log archiving.
-   Quick integration with the cluster via a script.
-   Aggregated logs across clusters and cloud providers.
-   Historical access to logs.
-   Highly available, scalable, and compliant with industry security standards.
-   Integrated with IBM Cloud IAM for user access management.

## IBM Cloud Monitoring

{: \#ibm-cloud-monitoring}

You can use IBM Cloud Monitoring to monitor the performance and overall system health of Red Hat OpenShift VPC clusters and provide for the following:

-   Customizable user interface for a unified view of cluster metrics, container security, resource usage, alerts, and custom events.
-   Quick integration with the cluster via a script.
-   Aggregated metrics and container monitoring across clusters and cloud providers.
-   Historical access to metrics that is based on the timeline and plan, and the ability to capture and download trace files.
-   Highly available, scalable, and compliant with industry security standards.
-   Integrated with IBM Cloud IAM for user access management.

## Flow Logs for VPC clusters

{: \#flow-logs}

Configure IBM Cloud Flow Logs for VPC to gather information about the traffic entering or leaving VPC cluster worker nodes. Flow logs are stored in an IBM Cloud Object Storage instance and can be used for troubleshooting purposes, adhering to compliance regulations.
