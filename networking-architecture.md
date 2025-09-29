---
copyright:
  years: 2025
lastupdated: "2025-09-29"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for networking
{: #networking-architecture}

The following tables summarize the networking architecture decisions for migrating VMware workloads to IBM Cloud OpenShift Virtualization.

| Architecture decision                                                      | Requirement                                                                                                             | Option                                                                             | Decision                               | Rationale                                                                                                                                                              |
|----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enterprise or Cloud connectivity to source VMware datacentre for migration | Provide secure, encrypted connectivity to the enterprise or Cloud source VMware private network for migration purposes. | Direct Link \\n \\n Site to site VPN for VPC                                       | Direct Link                            | Delivers predictable bandwidth and low latency for bulk VM replication and warm production cutover \\n Supports hybrid and cloud source VMware Datacentre connectivity |
| Production and non-production segregation                               | Provide ability for network isolation between production and non-production environments                                                                  | OpenShift Clusters \\n \\n IBM Cloud VPC Subnets, ACLs and security groups | VPC, Subnets, ACLs and Security groups | Allows for segmentation, network isolation and network policies to implement compliance posture security controls                                                      |
| Native connectivity to IBM Cloud services                                  | Provide secure connectivity to IBM Cloud Services                                                                       | Virtual Private Endpoints \\n \\n Public Cloud Service Endpoints                   | Virtual Private Endpoints              |  Virtual Private Endpoint allows to keep the traffic private with no egress charges                                                                                    |
{: caption="Table 1. Architecture decisions for networking when migration VMware workloads to IBM Cloud OpenShift Virtualization" caption-side="bottom"}
