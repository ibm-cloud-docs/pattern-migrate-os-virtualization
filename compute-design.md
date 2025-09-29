---
copyright:
  years: 2025
lastupdated: "2025-09-29"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Compute design
{: #compute-design}

A successful migration from VMware to IBM Cloud OpenShift Virtualization should consider the existing workload compliance requirements, platform availability service level agreements, current workload density and compute resource oversubscription ratios.

-   **Maintain virtualized workload segmentation for compliance:** To preserve existing compliance boundaries and workload segmentation, VMware production cluster can be mapped to IBM Cloud OpenShift Virtualization cluster in separate {{site.data.keyword.vpc_short}}. This approach allows for regulatory and operational control - such as tenant isolation is maintained. Additionally, existing VMware vSphere folder structures can be mapped to OpenShift projects and OpenShift namespaces to maintain auditability and compliance posture.
-   **High availability and resiliency of virtualized workloads:** To meet existing workload availability service level agreements the OpenShift Virtualization clusters should be sized to tolerate node failures. Features such as Node health check and fence agent remediation operators can detect node failures or hung nodes. Additionally, you can use soft eviction thresholds set below the defined service level agreement, to trigger live migrations and avoid workload downtime.
-   **Optimize compute resource utilisation in worker node pools:** To preserve compute efficiency and reduce stranded resources, the worker node pools should be sized and grouped based on workload characteristics. Node labels and selectors can be used to create logical pools for high-memory, GPU or latency sensitive applications. CPU and RAM resource oversubscription strategies can be applied, with observability tools, and the descheduler operator policies to optimize compute resource usage.
-   **Virtualization cost efficiency:** Virtualization licensing models for solutions such as VMware VCF or Red Hat OpenShift Virtualization, directly impact compute cost optimization strategies. Broadcom VMware VCF is licensed per physical core, making the compute consolidation and right-sizing critical to reduce the virtualization cost overhead. Red Hat OpenShift Virtualization has a socket-based licensing on bare-metal, allowing higher VM density per node to lower per-VM cost. Additionally, OpenShift Virtualization includes Red Hat Enterprise Linux (RHEL) and CoreOS entitlements, removing the need for Linux guest OS licensing, and further reducing operational costs.
