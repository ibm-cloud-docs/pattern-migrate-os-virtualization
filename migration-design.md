---
copyright:
  years: 2023
lastupdated: "2023-12-26"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Migrate VMWare workloads to IBM Cloud OpenShift Planning

{: \#migration-design}

**Phased Migration Approach**

The migration of VMware workloads to {{site.data.keyword.Bluemix_notm}} OpenShift Virtualization is proposed in a 4 phase migration program approach.

![Migrate VMWare to Openshift Virtualization Phases](images/migvmwocpvibmcloud.svg){: caption="Migrate VMWare workloads to Openshift Virtualization Phased approach" caption-side="bottom"}

* Discovery Assess Phase 1:
Discovery: Data is collected across platform, operations and application teams to understand the as-is VMware operating processes, automation and IT integration with the workload applications. Identify priorities such as slow responses to business needs, complexity of accelerating application modernization programs. Identify and document current infrastructure, applications, relationships, and dependencies including drift from the expected business required state. The key to data collection for the VMware on-premises or colocated platform is to an extraction tool such as RVtools.
