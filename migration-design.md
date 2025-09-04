---
copyright:
  years: 2025
lastupdated: "2025-09-04"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Migrate VMWare workloads to IBM Cloud OpenShift Planning
{: #migration-design}

## Phased Migration Approach
{: #phased-migration}

The migration of VMware workloads to {{site.data.keyword.Bluemix_notm}} OpenShift Virtualization is proposed in a 4 phase migration program approach.

![Migrate VMWare to Openshift Virtualization Phases](images/migvmwocpvibmcloud.svg){: caption="Migrate VMWare workloads to Openshift Virtualization Phased approach" caption-side="bottom"}

1.  Phase 1 Discovery and Assess

Data is collected across platform, operations and application teams to understand the as-is VMware operating processes, automation and IT integration with the workload applications.

Extract and document VMware platform inventory and ressource allocation, typically using RVTools.

Identify priorities such as slow responses to business needs, complexity of accelerating application modernization programs.

Identify and document current infrastructure, applications, relationships, and dependencies including drift from the expected business required state.

Identify use case for proof of concept (POC).

Document day 2 operation requirements including, automation, configuration management, observability, disaster recovery.

Document security and compliance requirements.

Document licensing requirements.
