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

## IBM Cloud Observability

{: \#Observability}

**IBM Cloud Monitoring**

You can use IBM Cloud Log to add log management capabilities to Red Hat OpenShift VPC clusters and provide for the following:

-   Customizable user interface for live streaming of log tailing, real-time troubleshooting issue alerts, and log archiving.
-   Aggregated logs across clusters and cloud providers.
-   Highly available, scalable, and compliant with industry security standards.

Integrated with IBM Cloud IAM for user access management.

**IBM Cloud Log**

You can use IBM Cloud Log to add log management capabilities to Red Hat OpenShift VPC clusters and provide for the following:

-   Customizable user interface for live streaming of log tailing, real-time troubleshooting issue alerts, and log archiving.
-   Aggregated logs across clusters.
-   Highly available, scalable, and compliant with industry security standards.
-   Integrated with IBM Cloud IAM for user access management.

## OpenShift Declarative Pipelines

{: \#OpenShift-declarative-pipelines}

You can use IBM Cloud OpenShift Virtualization, declarative pipelines to enable GitOps automation, VM lifecycle orchestration, and policy driven governance using the following:

**Openshift GitOps (Argo CD)**

-   Can manage the desired state of virtual machine and infrastructure as code.
-   Enables automated reconciliation of virtual machine configuration from Git repository.

**Openshift Pipelines**

-   Allows execution of CI/CD workflows for virtual machine provisioning, configuration, and testing.
-   Integrates with secrets, config maps, and custom tasks for virtual machine deployment automation.
