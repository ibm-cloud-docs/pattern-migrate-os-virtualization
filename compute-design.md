---
copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute design

{: \#compute-design}

A successful migration from VMware to IBM Cloud OpenShift Virtualization should consider the existing workload compliance requirements, platform availability service level agreements, current workload density with resource oversubscription ratios and virtual instances lifecycle.

-   **Maintain virtualized workload segmentation for compliance:** To preserve existing compliance boundaries and workload segmentation, VMware production cluster can be mapped to IBM Cloud OpenShift Virtualization cluster in separate IBM Cloud VPC . This approach allows for regulatory and operational control - such as tenant isolation is maintained. Additionally, existing VMware vSphere folder structures can be mapped to OpenShift projects and OpenShift namespaces to maintain auditability and compliance posture.
-   **High availability and resiliency of virtualized workloads:** To meet existing workload availability service level agreements the OpenShift Virtualization clusters should be sized to tolerate node failures. Features such as Node health check and fence agent remediation operators can detect node failures or hung nodes. Additionally, you can use soft eviction thresholds set below the defined service level agreement, to trigger live migrations and avoid workload downtime.
-   **Optimize compute resource utilisation in worker node pools:** To preserve compute efficiency, maximise virtual instance density and reduce stranded resources, the worker node pools should be sized and grouped based on workload characteristics. Node labels and selectors can be used to create logical pools for high-memory, GPU or latency sensitive applications. CPU and RAM resource oversubscription strategies can be applied, with observability tools, and descheduler operator policies to optimize compute resource usage.
