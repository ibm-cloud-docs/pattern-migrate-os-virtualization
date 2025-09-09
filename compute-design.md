---
copyright:
  years: 2025
lastupdated: "2025-09-09"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute design
{: #compute-design}

A successful migration from VMware to IBM Cloud OpenShift Virtualization should consider the existing compliance boundaries, availability service level agreements, current workload density, and cpu oversubscription ratios.

-	**Maintain virtualized workload segmentation for compliance:** To preserve existing compliance boundaries and workload segmentation, VMware production clusters can be mapped to IBM Cloud OpenShift Virtualization clusters. This approach allows for regulatory and operational controls - such as tenant isolation are maintained. Additionaly, existing VMware cluster vLans and vSphere folder structures can be mapped to OpenShift projects, namespaces and network policies to maintain auditability and compliance posture.

-	**High availability and resiliency of virtualized workloads:** To meet existing workload availability service level agreements the OpenShift Virtualization clusters should be sized to tolerate node failures. Features such as Node health check and fence agent remiation operators can detect node failures or hung nodes. To tolorate zone level outages, you can use soft eviction thresholds set below the service level agreement defined, to trigger live migrations avoiding workload downtime.

-	**Optimize compute ressource utilisation in worker node pools:** To preserve compute efficiency, maximise virtual instance density and  reduce stranded resources, the worker node pools should be sized and grouped based on workload caracteristics. Node labels and selectors can be used to create logical pools for high-memory, GPU or latency sensitive applications. Oversubscription stategies can be applied with observability tools and descheduler policies to maintain balenced CPU usage.
