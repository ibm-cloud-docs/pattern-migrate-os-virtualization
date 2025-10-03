---
copyright:
  years: 2025
lastupdated: "2025-10-03"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Migrate VMWare workloads to IBM Cloud Red Hat OpenShift Planning
{: #migration-design}

## Phased Migration Approach
{: #phased-migration}

The migration of VMware workloads to {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift Virtualization is proposed in a phased approach.

![Migrate VMWare to Red Hat OpenShift Virtualization Phases](images/gmv1.svg){: caption="Migrate VMWare workloads to Openshift Virtualization phased approach" caption-side="bottom"}

The phases and their key processes are:

### Phase 1: Discovery and insights
{: #discovery}

-   Data is collected across the distributed landscape, VMware Clusters, operations, and service management processes. IBM AI-powered discovery and assessment tools can automate application to infrastructure resource mapping and affinity, and right-size the target landing zones.

-   Full VMware platform inventory and compute resource allocation is typically completed by using RVTools.

-   IBM AI-driven tools provides insights to right size the target landing zones and propose TCO optimization on the Red Hat OpenShift Virtualization platform.

-   The proof of concept (POC) use case is defined with success criteria such as performance and availability validation.

-   The proof of concept (POC) is built and completed.

### Phase 2: Design and pilot
{: #design}

-   Delivery of design workshop with key infrastructure, operations, workload stakeholders.

-   The target platform design with performance, scalability, availability, security, regulatory, and compliance considerations is completed.

-   Disaster recovery planning based on RTO and RPO requirements is completed.

-   A migration strategy, program planning and detailed design solution, with low-risk migration and warm production cutover is completed.

-   Design, build, and run the pilot.

### Phase 3: Build and code
{: #build}

-   Build target IBM Cloud Red Hat OpenShift Virtualization environment (compute, network, storage).

-   Connectivity linkage between the source VMware platform and the target Red Hat OpenShift Virtualization clusters.

-   Coding of pre-migration and post migration playbooks.

-   Coding of Day 2 service management playbooks.

### Phase 4 Migrate and manage
{: #migration}

-   Initial wave migrations for testing and development environments.

-   Validation of workload performance, placement policies, and the operational model is completed.

### Phase 5: Scale and decommission
{: #scale}

-   Complex wave migrations, including UAT environments that validate orchestration, integrations under production-like conditions.

-   Decommission VMware unused infrastructure, ensure the disposition of secure data, audit traceability, and compliance with retention policies.

### Phase 6: Production cutover and decommission
{: #cutover}

-   Help ensure production cutover readiness, including business continuity and rollback processes.

-   Perform final cutover during agreed maintenance windows by using warm migrate method.

-   Retire residual VMWare assets.
