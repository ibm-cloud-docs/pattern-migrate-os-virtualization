---
copyright:
  years: 2025
lastupdated: "2025-09-29"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Service management design
{: #service-management-design}

When migrating production critical VMware workloads to IBM Cloud OpenShift Virtualization, required service management process and tooling changes will be driven by the migration program schedule and strategy.

A short-term migration program using lift and shift approach to minimize changes will focus on replacing dependant VMware tooling, such as vCenter APIs, vROps, with IBM Cloud Observability and OpenShift Virtualization APIs to manage VM lifecycle and placement.

A migration program using virtualization platform modernization approach requires a re-coding from ITIL process tooling and imperative scripting to a DevSecOps declarative model built on GitOps workflows and policy-driven automation. Legacy runbooks and ticket based operations are replaced by declarative pipelines ,version-controlled manifests and integrated security gates to align the virtualization platform with cloud-native DevSecOps practices.

## IBM Cloud Observability
{: #Observability}

### IBM Cloud Monitoring
{: #monitoring}

You can use IBM Cloud Monitoring to monitor the performance and overall system health of Red Hat OpenShift Virtualization clusters, worker pools and worker nodes providing for the following:

-   Customizable user interface for a unified view of cluster metrics, virtual machine and container security, resource usage, alerts, and custom events.
-   Aggregated metrics and monitoring across OpenShift Virtualization clusters.
-   Highly available, scalable, and compliant with industry security standards.
-   Integrated with IBM Cloud IAM for user access management.

### IBM Cloud Logs
{: #logging}

You can use {{site.data.keyword.logs_full_notm}} to add log management capabilities to Red Hat OpenShift VPC clusters and provide for the following:

-   Customizable user interface for live streaming of log tailing, real-time troubleshooting issue alerts, and log archiving.
-   Aggregated logs across clusters.
-   Highly available, scalable, and compliant with industry security standards.
-   Integrated with IBM Cloud IAM for user access management.

### {{site.data.keyword.fl_full}}
{: #flow-logs}

You can configure {{site.data.keyword.fl_full}} to gather information about the traffic entering or leaving the OpenShift Virtualization cluster worker nodes. Flow logs are stored in an {{site.data.keyword.cos_full_notm}} instance and can be used for troubleshooting purposes, adhering to compliance regulations

## OpenShift Declarative Pipelines
{: #OpenShift-declarative-pipelines}

You can use IBM Cloud OpenShift Virtualization, declarative pipelines to enable GitOps automation, VM lifecycle orchestration, and policy driven governance using the following:

**Openshift GitOps (Argo CD)**
{: #argocd}

-   Can manage the desired state of virtual machine and infrastructure as code.
-   Enables automated reconciliation of virtual machine configuration from Git repository.

**Openshift Pipelines**
{: #os-pipelines}

-   Allows execution of CI/CD workflows for virtual machine provisioning, configuration, and testing.
-   Integrates with secrets, config maps, and custom tasks for virtual machine deployment automation.
