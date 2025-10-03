---
copyright:
  years: 2025
lastupdated: "2025-10-03"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Network Design
{: #network-design}

-   **Maintain workload and management network segmentation:** To preserve existing workload compliance boundaries and management segmentation, the Red Hat OpenShift Virtualization clusters can be deployed into {{site.data.keyword.vpc_short}} that mirror existing production and nonproduction network segmentation. This approach allows for regulatory and operational controls - such that tenant isolation is maintained.

-   **Load balancing and DNS integration across virtual machine and container workloads:** {{site.data.keyword.vpc_short}} application Load Balancers (ALBs) can be used to distribute traffic across both virtual machine and containerized applications, helping ensure high availability and performance for mixed workloads. {{site.data.keyword.dns_full_notm}} can be integrated with custom zones to support dynamic name resolution of migrated virtual machine workload services, while Red Hat OpenShift CoreDNS can be configured with forwarding rules to reuse existing DNS-records. This hybrid DNS strategy avoids duplication and supports service discovery across workload environments.
