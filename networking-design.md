---

copyright:
  years: 2025
lastupdated: "2025-07-22"

keywords: virtualization, VMware, SDN, NSX, OpenShift

subcollection: pattern-migrate-vmware-workloads-redhat-openshift-virtualization

authors:
  - name: Esteban Arias
    url: https://linkedin.com/in/eariasn01

version: 1.0

deployment-url: url

use-case: virtualization, hypervisor, migration, containers
industry: FinancialSector, Manufacturing, Retail, Industrials, Communications
compliance: 
content-type: deployment

production: false

---

{{site.data.keyword.attribute-definition-list}}

# Network design
{: #network-design}


Networking functionality includes integration with the cluster's native software-defined networking (SDN) stack, enabling secure and policy-driven connectivity to virtual machines via programmable network policies. This supports granular control over VM ingress and egress traffic, aligning with enterprise-grade security and compliance requirements. Additionally, the platform provides support for traditional networking mechanisms, including Open vSwitch (OVS) for VM attachment to VLAN-backed and other overlay or underlay networks, SR-IOV for high-performance network interfaces, and OpenShift’s user-defined networking (UDN) as a flexible, evolving alternative for custom network topologies.
