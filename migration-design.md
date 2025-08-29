---
copyright:
  years: 2023
lastupdated: "2023-12-26"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Virtual Infrastructure Migration Planning

{: \#migration-design}

**Migration Assessment**

The move of a business critical x86 VMware production platform to {{site.data.keyword.Bluemix_notm}} is supported by the migration program, which we propose to divide into 5 phases: Discovery, Assessment, Minimum Viable Product (MVP), Migration, and Operate.

![Migrate VMWare to IBM Cloud Openshift Virtualization Phases](images/migvmwocpvibmcloud.svg){: caption="Migrate VMWare workloads to IBM Cloud Openshift Virtualization Phased approach" caption-side="bottom"}

* Discovery - Phase 1: Data is collected across technical, sales, and business teams to understand the motivation and internal factors driving the move to cloud. Identify priorities such as scalability, solving functional issues, lack of in-house skills, reducing infrastructure, and IT expenses. Identify and document current infrastructure, applications, relationships, and dependencies including drift from the expected business required state. The key to data collection for the VMware on-premises or colocated platform is to an extraction tool such as RVtools.
* Assessment - Phase 2: Data that is collected in the discovery phase is used to assess the migration to cloud viability to and choosing the right target platform solution. Prioritize the lift and shift migration of the VMWare SDDC to {{site.data.keyword.Bluemix_notm}} for VMware Cloud Foundation so that current VMware ISV support, VMWare processes, and automation are maintained. Avoid adding repackaging (applications) or refactor to microservices patterns to decouple the modernize from move to {{site.data.keyword.Bluemix_notm}} program. Assess the supply-chain of workload validating the utilization and usage of VMware components. Right-size the target VCF landing zones consolidating VMware clusters using higher core density servers. Assess the software supply chain and data for the required encryption level and business key integration. The outcome of the assessment phase is a high-level architecture of the cloud environments with an associated bill of materials.
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
