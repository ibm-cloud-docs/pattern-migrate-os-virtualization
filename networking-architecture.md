---
copyright:
  years: 2025
lastupdated: "2025-09-11"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Architecture decisions for networking

{: \#networking-architecture}

The following tables summarize the networking architecture decisions for migrating VMware workloads to IBM Cloud OpenShift Virtualization.

| Architecture decision                                                      | Requirement                                                                                                             | Option                                                                                                                                           | Decision                                                                                          | Rationale                                                                                                                                                              |
|----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enterprise or Cloud connectivity to source VMware datacentre for migration | Provide secure, encrypted connectivity to the enterprise or Cloud source VMware private network for migration purposes. | Direct Link \\n \\n Site to site VPN for VPC                                                                                                     | Direct Link                                                                                       | Delivers predictable bandwidth and low latency for bulk VM replication and warm production cutover \\n Supports hybrid and cloud source VMware Datacentre connectivity |
| IBM Cloud network segmentation and isolation                               | Provide ability for network isolation across workloads                                                                  | OpenShift Clusters \\n \\n IBM Cloud VPC \\n \\n Subnets, ACLs and security groups                                                               | VPC, Subnets, ACLs and Security groups                                                            | Allows for segmentation, network isolation and network policies to implement compliance posture security controls                                                      |
| Native connectivity to IBM Cloud services                                  | Provide secure connectivity to IBM Cloud Services                                                                       | Virtual Private Endpoints \\n \\n Public Cloud Service Endpoints                                                                                 | Virtual Private Endpoints                                                                         | Private Path service uses Virtual Private Endpoint gateways to provide connectivity                                                                                    |
| Provide that application network changes are not required (BYOIP)          | Provide capability for BYOIP                                                                                            | NAT mapping via Transit Gateway \\n \\n extend existing network using BGP over Direct link \\n \\n register prefixes via IBM Cloud BYOIP service | Register ip prefixes with IBM Cloud BYOIP service and assign into VPC public gateways or VPC ALBs | Preserves existing IP addresses. Eliminates NAT/translation complexity                                                                                                 |

{: caption="Table 1. Architecture decisions for networking when migration VMware workloads to IBM Cloud OpenShift Virtualization" caption-side="bottom"}
