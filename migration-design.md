---
copyright:
  years: 2025
lastupdated: "2025-09-30"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Migrate VMWare workloads to IBM Cloud OpenShift Planning
{: #migration-design}

## Phased Migration Approach
{: #phased-migration}

The migration of VMware workloads to {{site.data.keyword.Bluemix_notm}} OpenShift Virtualization is proposed in a 6 phase program approach.

![Migrate VMWare to Openshift Virtualization Phases](images/gmv1.svg){: caption="Migrate VMWare workloads to Openshift Virtualization phased approach" caption-side="bottom"}

The phases and their key processes are described below:

**Phase 1 Discovery and Insights**
{: \#discovery}

-   Data is collected across the distributed landscape, VMware Clusters, operations and service management processes. IBM AI powered discovery and assessment tooling can automate application to infrastructure resource mapping and affiinity, and right-size the target landing zones.

-   Full VMware platform inventory and compute resource allocation is completed typically using RVTools.

-   IBM AI-driven tooling provides insights to right size the target landing zones and propose TCO optimization on the OpenShift Virtualization platform.

-   The proof of concept (POC) use case is defined with success criteria such as performance and availablity validation.

-   The proof of concept (POC) is built and completed.

**Phase 2 Design and Pilot**
{: \#design}

-   Delivery of design workshop with key infrastructure, operations, workload stakeholders.

-   The target platform design with performance, scalability, availability, security, regulatory and compliance considerations is completed.

-   Disaster recovery planning based on RTO / RPO requirements is completed.

-   A migration strategy, program planning and detailed design solution, with low-risk migration and warm production cutover is completed.

-   Design, build and execute of Pilot.

**Phase 3 Build and Code**
{: \#build}

-   Build target IBM Cloud OpenShift Virtualization environment (compute, network, storage).

-   Connectivity linkage between the source VMware platoform and the target OpenShift Virtualization clusters.

-   Coding of pre-migration and post migration playbooks.

-   Coding of day 2 service management playbooks.

**Phase 4 Migrate and Manage**
{: \#migration}

-   Initial wave migrations for testing and development enviornments.

-   Validation of workload performance, placement policies and the operational model is completed.

**Phase 5 Scale and Decommission**
{: \#scale}

-   Complex wave migrations, including UAT environments validating orchestration, integrations under production-like conditions.

-   Decommision VMware unused infrastructure, ensure secure data disposition, audit traceability and compliance with retention policies.

**Phase 6 Production Cutover and Decommission**
{: \#cutover}

-   Ensure production cutover readiness including business continuity and rollback processes.

-   Perform final cutover during agreed maintenance windows using warm migrate method.

-   Retire residual VMWare assets.
