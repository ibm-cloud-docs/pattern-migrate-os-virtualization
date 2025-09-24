---
copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Network Design

{: \#network-design}

-   **Maintain workload and management network segregation:** To preserve existing workload compliance boundaries and management segmentation, the Openshift Virtualization worker pools can be deployed into IBM Cloud VPCs that mirror existing segmentation. This approach allows for regulatory and operational controls - such that tenant isolation is maintained. Existing VMware cluster workload vLans can be mapped to VPC subnets. Additional VPC Subnets can be created for segregating management, storage and live migration network traffic. Security groups and ACLs within the VPC can be used to implement network security compliance policies, ensuring access controls allign with the organisation standards.
-   **Load balancing and DNS integration across VMs and continer workloads** IBM Cloud VPC application Load Balancers (ALBs) can be used to distribute traffic across both virtual instances services and containerized applications, ensuring high availability and performance for mixed workloads. IBM Cloud DNS can be integrated with custom zones to support dynamic name resolution of migrated VM services, while OpenShift CoreDNS can be configured with forwarding rules to reuse existing DNS-records. This hybrid DNS strategy avoids duplication and supports service discovery across workload environments.
