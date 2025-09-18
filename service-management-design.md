---
copyright:
  years: 2025
lastupdated: "2025-09-18"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Service management design

{: #service-management-design}

A successful migration from VMware to IBM Cloud OpenShift Virtualization should consider the existing compliance boundaries, availability service level agreements, current workload density, and cpu oversubscription ratios.

-	**Maintain observability:** To preserve existing compliance boundaries and workload segmentation, VMware production clusters can be mapped to IBM Cloud OpenShift Virtualization clusters. This approach allows for regulatory and operational controls - such as tenant isolation are maintained. Additionaly, existing VMware cluster vLans and vSphere folder structures can be mapped to OpenShift projects, namespaces and network policies to maintain auditability and compliance posture.
