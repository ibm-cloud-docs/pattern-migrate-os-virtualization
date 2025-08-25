---
copyright:
  years: 2025
lastupdated: "2025-08-25"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Overview
{: #overview}

The objective of this pattern is to provide an {{site.data.keyword.IBM_notm}} solution design and deployment guide for the usage of OpenShift Virtualization to migrate existing VMware virtual machine workloads into IBM Cloud OpenShift Virtualization.

Red Hat® OpenShift® provides a modern, enterprise-ready infrastructure platform for running virtual machines and container-based applications. Powered by containers, Kubernetes, and DevSecOps capabilities, Red Hat OpenShift is a foundation for rapidly building, deploying, running, and managing both existing and new applications at scale and with security across hybrid, multicloud, and edge environments.

Red Hat OpenShift virtualization is Kernel-based Virtual Machine (KVM) and KuberVirt based and supports migration of Linux and Microsoft Window virtual machines allowing customers to unify into a single application platform.

Migrating VMware workloads to IBM Cloud OpenShift Virtualization provides the following benefits:

* Single pane of glass Enterprise level supported platform.
* Application modernization capabilities.
* Hybrid cloud support across providers.
* Self service provisioning for consumers.
* CI/CD integrations with OpenShift pipelines.
* Unparallel booting performance.
* In-guest software integration for Windows and Linux.
* Container like non root security model.
* Live migration support.
* Broad range of backup options through the Red Hat certified partner ecosystem.
* Autoscaling and health check capabilities.

This pattern is intended to:

*	Accelerate and simplify solution design by providing a standard IBM Cloud deployment architecture reference following the [IBM Architecture Framework].(https://cloud.ibm.com/docs/architecture-framework)
*	Provide a prescriptive, end-2-end enterprise-class solution design, with diagrams, component architecture decisions along with rationale for cloud component selection to meet enterprise requirements.
*	Ensure requirements can be met from a performance, system availability and security perspective.

The Architecture Framework provides a consistent approach to design cloud solutions by addressing requirements across a set of aspects and domains, which are technology-agnostic architectural areas that need to be considered for any enterprise solution. For more details, see [Introduction to the Architecture Design Framework](https://test.cloud.ibm.com/docs/architecture-framework).
