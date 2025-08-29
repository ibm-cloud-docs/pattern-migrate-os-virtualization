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
Assess:  Data that is collected in the discovery phase is used to assess the migration to cloud viability to and choosing the right target platform solution. Prioritize the lift and shift migration of the VMWare SDDC to {{site.data.keyword.Bluemix_notm}} for VMware Cloud Foundation so that current VMware ISV support, VMWare processes, and automation are maintained. Avoid adding repackaging (applications) or refactor to microservices patterns to decouple the modernize from move to {{site.data.keyword.Bluemix_notm}} program. Assess the supply-chain of workload validating the utilization and usage of VMware components. Right-size the target VCF landing zones consolidating VMware clusters using higher core density servers. Assess the software supply chain and data for the required encryption level and business key integration. The outcome of the assessment phase is a high-level architecture of the cloud environments with an associated bill of materials.
* Minimum Viable Product (MVP) - Phase 3: Provides the confidence in the viability of the proposed solution. It is important to clearly define and articulate upfront the success criteria of the MVP as well as to identify the approving stakeholders. The successful MVP builds trust and confidence in the solution and provides the go ahead for the migration of the production workload. The MVP familiarizes the operating team with the cloud platform and guides toward a smooth adoption.
* Migration - Phase 4: Execution of workload environment migration. The duration of the migration to {{site.data.keyword.Bluemix_notm}} phase depends on the complexity and criticality of the production environment. IBM Technology Expert Labs includes accelerator services to migrate workloads to {{site.data.keyword.Bluemix_notm}}.
* Operate (run) - Phase 5: Refers to tasks and processes to maintain the workload operational after the workload has been migrated to the target {{site.data.keyword.Bluemix_notm}} VMware platform. Key processes include backup, observability, and maintaining compliance.




1.  Discovery workshops with outcomes

Analysis of existing virtual infrastructure investments and gather requirements for future target platform.

Identify use case(s) for pilot phase.

Document day 2 operation requirements including, automation, configuration management, observability, disaster recovery.

Document security and compliance requirements.

Document licensing requirements.

1.  Identify Workloads with outcomes

Define integrations such as storage, network and clustering requirements.

Map workload’s storage, network and operations to requirements

1.  Define a high-level solution with outcomes

    High level Openshift Virtualization target landing zones design

    Migration program timeline and milestones
