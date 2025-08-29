---
copyright:
  years: 2023
lastupdated: "2023-12-28"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute design

{: \#compute-design}


1.  OpenShift Cluster design points

Define whether environments workloads (PROD, PRE-PROD, UAT, TEST) are run on shared worker nodes using node labeling and taints.

Define if tenant cluster isolation is required for compliance.

Ensure cluster design responds to isolation, availability, scalability and compliance requirements.



1.  Worker Pool

Define if virtualized workloads (VMs) run on dedicated worker pools or shared pools with container workloads. Best practice is to use node labels, taints and tolerations to control VM placement and avoid interference with container workloads.


1.  Worker node profile

Define
