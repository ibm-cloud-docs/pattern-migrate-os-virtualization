---
copyright:
  years: 2025
lastupdated: "2025-09-25"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Migrate VMWare workloads to IBM Cloud OpenShift Planning

{: \#migration-design}

## Phased Migration Approach

{: \#phased-migration}

The migration of VMware workloads to {{site.data.keyword.Bluemix_notm}} OpenShift Virtualization is proposed in a 6 phase program approach.

![Migrate VMWare to Openshift Virtualization Phases](images/gmv1.svg){: caption="Migrate VMWare workloads to Openshift Virtualization phased approach" caption-side="bottom"}

**Discovery and Insights**

Data is collected across the distributed landscape, VMware Clusters, operations and service management processes. IBM AI powered discovery and assessment tooling (such as CAST, IC4CT) can automate application to infrastructure resource mapping and affiinity, and right-size the target landing zones.

The extract of the VMware platform inventory and compute resource allocation typically uses RVTools.

IBM Turbonomics and Apptio AI-driven tooling can provide insights to right size target landing zones and propose TCO optimization on the OpenShift Virtualization platform.

Identify use case and run proof of concept (POC).

**Design and Pilot**

Design workshop with key infrastructure, operations, workload stakeholders.

Target platform design with performance, scalability, availability, security, regulatory and compliance considerations.

Disaster recovery planning based on RTO / RPO requirements.

Migration strategy and program planning with low-risk migration and warm production cutover.

Design, build and execute Pilot.

**Build and Code**

Build target IBM Cloud OpenShift Virtualization environment (compute, network, storage).

Connectivity linkage between VMware and target OpenShift Virtualization clusters.

Code pre-migration and post migration playbooks.

Code day 2 service management playbooks and declarative .

**Migrate and Manage**

Initial wave migrations.

**Scale and Decommission**

**Production Cutover and Decommission**
