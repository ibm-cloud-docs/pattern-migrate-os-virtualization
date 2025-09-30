---
copyright:
  years: 2025
lastupdated: "2025-09-30"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for networking
{: #networking-architecture}

The following tables summarizes the networking architecture decisions for migrating VMware workloads to IBM Cloud OpenShift Virtualization.

| Architecture decision                                                      | Requirement                                                                                                             | Option                                                                             | Decision                               | Rationale                                                                                                                                                              |
|----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enterprise or Cloud connectivity to source VMware datacentre for migration | Provide secure, encrypted connectivity to the enterprise or Cloud source VMware private network for migration purposes. | Direct Link \\n \\n Site to site {{site.data.keyword.vpn_vpc_short}}                                       | Direct Link                            | Delivers predictable bandwidth and low latency for bulk VM replication and warm production cutover \\n Supports hybrid and cloud source VMware Datacentre connectivity |
| Production and non-production segregation                               | Provide ability for network isolation between production and non-production environments                                                                  | OpenShift Clusters \\n \\n IBM Cloud VPC Subnets, ACLs and security groups | VPC, Subnets, ACLs and Security groups | Allows for segmentation, network isolation and network policies to implement compliance posture security controls                                                      |
| Native connectivity to IBM Cloud services                                  | Provide secure connectivity to IBM Cloud Services                                                                       | {{site.data.keyword.vpe_full}} \\n \\n Public Cloud Service Endpoints                   | {{site.data.keyword.vpe_full}}              |  {{site.data.keyword.vpe_full}} allows to keep the traffic private with no egress charges                                                                                    |
{: caption="Table 1. Architecture decisions for networking when migration VMware workloads to IBM Cloud OpenShift Virtualization" caption-side="bottom"}
