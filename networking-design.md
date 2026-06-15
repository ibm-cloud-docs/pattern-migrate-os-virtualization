---
copyright:
  years: 2025
lastupdated: "2026-06-15"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Network Design
{: #network-design}

-   **Maintain workload and management network segmentation:** To preserve existing workload compliance boundaries and management segmentation, the Red Hat OpenShift Virtualization clusters can be deployed into {{site.data.keyword.vpc_short}} that mirror existing production and nonproduction network segmentation. This approach allows for regulatory and operational controls - such that tenant isolation is maintained.

-   **Load balancing and DNS integration across virtual machine and container workloads:** {{site.data.keyword.vpc_short}} application Load Balancers (ALBs) can be used to distribute traffic across both virtual machine and containerized applications, helping ensure high availability and performance for mixed workloads. {{site.data.keyword.dns_full_notm}} can be integrated with custom zones to support dynamic name resolution of migrated virtual machine workload services, while Red Hat OpenShift CoreDNS can be configured with forwarding rules to reuse existing DNS-records. This hybrid DNS strategy avoids duplication and supports service discovery across workload environments.

## OpenShift Network topology options
{: #openshift-network-topology}

The following cluster infrastructure network design options are enabling the migration of VMware-based workloads to OpenShift Virtualization while preserving existing workload IP addressing (Bring Your Own IP – BYOIP). The solutions support continuity of network identity and minimize changes to existing application configurations and dependencies.

### Layer 2 Secondary Network with Localnet Breakout
{: #layer2-secondary-localnet}

Layer 2 Secondary Network with Localnet Breakout provides the following capabilities:

- VMs are deployed on Layer 2 Secondary (overlay) segments
- Multiple Layer 2 Secondary interfaces can be attached to a single VM
- Layer 2 Secondary segment supports Static IP assignment, administrators or automation tools must explicitly configure IPs inside the VM guest OS
- Enables reuse of existing IP subnets from on-prem or VMware environments
- Can span namespaces when configured as a CUDN
- External connectivity is provided through a VNF (virtual firewall/router)
- The VNF connects to a Localnet network for access to external VLAN/VPC networks

![CUDN Layer 2 secondary with VNF](images/layer2sec.svg "Architecture diagram showing CUDN Layer 2 secondary network with VNF connecting to Localnet for external connectivity"){: caption="Figure 1. CUDN Layer 2 secondary with VNF" caption-side="bottom"}

The Layer 2 Secondary with Localnet breakout architecture provides a balanced and enterprise-aligned solution for VMware workload migration to OpenShift Virtualization. It ensures IP address preservation, network isolation, and controlled external connectivity, while aligning closely with existing operational practices and minimizing migration risk.

### Localnet (Direct VLAN Passthrough)
{: #localnet-vlan-passthrough}

Localnet is used selectively for workloads requiring direct Layer 2 access to existing VLANs. It provides direct integration with existing Layer 2 networks and is functionally equivalent to a VLAN-backed port group (standard or distributed) in VMware environments without NSX overlay.

![CUDN Localnet](images/localnet.svg "Architecture diagram showing CUDN Localnet with direct VLAN passthrough"){: caption="Figure 2. CUDN Localnet" caption-side="bottom"}

Key characteristics:

- Traffic bypasses the OVN software-defined networking (SDN) layer
- No OpenShift-native networking services are available (e.g., load balancing, network policy enforcement, or cluster DNS)
- IP address management is externalized; IP addresses are assigned using VPC VNIs
- Configuration is scoped per availability zone
- Multiple Localnet interfaces can be attached to a single VM

### VPE to access IBM Cloud services
{: #vpe-ibm-cloud-services}

Both OpenShift Network topology options are adopting Virtual Private Endpoints (VPE) with VPC-native connectivity as the standard approach for accessing {{site.data.keyword.cloud_notm}} services to expose {{site.data.keyword.cloud_notm}} services into the VPC address space and route traffic internally via the {{site.data.keyword.cloud_notm}} private backbone network.

Virtual Private Endpoints provide direct, private access to {{site.data.keyword.cloud_notm}} services from within a VPC by assigning private IP addresses from the VPC subnet.

Key characteristics:

- Traffic never traverses the public internet
- Services are accessed using private IP addresses within the VPC CIDR range
- Integrated with VPC routing, security groups, and ACLs
- Supports fine-grained access control and segmentation

This model enables workloads running in OpenShift Virtualization to consume {{site.data.keyword.cloud_notm}} platform services as if they were native resources within the same network domain.

## Production and nonproduction segmentation
{: #prod-nonprod-segmentation}

Production and nonproduction segmentation is provided by a Hybrid Segmentation Model combining cluster-level and network-level isolation.

Separate OpenShift clusters for Production and Non-Production environments are deployed. Within each cluster, use:

- Layer 2 Secondary networks for workload segmentation
- Namespace-based isolation (CUDN where applicable)
- Network policies and VNFs for traffic control

The selected hybrid approach provides defense-in-depth segmentation, ensuring both hard isolation at the infrastructure level and fine-grained control within each environment.

### Cluster-Level Segmentation (Primary Isolation Boundary)
{: #cluster-level-segmentation}

Using dedicated clusters per environment ensures:

- Complete isolation of control planes and infrastructure components
- Separation of administrative access and operational processes
- Independent lifecycle and upgrade management
- Reduced blast radius in case of failure or security incidents

This aligns with enterprise best practices where production systems must be isolated from development and testing activities.

### Network-Level Segmentation (Secondary Isolation Layer)
{: #network-level-segmentation}

Within each cluster, segmentation is enforced using multiple mechanisms:

Layer 2 Secondary Networks
:   Provide isolated Layer 2 segments per application or environment tier. Support static IP addressing, aligning with VM workload requirements. Enable separation of application, management, and storage traffic.

Namespace Isolation and CUDN
:   Logical separation of workloads across teams and applications. Ability to span controlled network segments across namespaces.

Virtual Network Functions (VNF)
:   Enforce traffic inspection, routing, and firewall policies. Control east-west and north-south traffic flows. Provide enterprise-grade security controls.

### Segmentation Principles Applied
{: #segmentation-principles}

Environment Isolation
:   No direct connectivity between Prod and Non-Prod by default.

Least Privilege Networking
:   Only explicitly allowed communication paths are permitted.

Policy Enforcement
:   Centralized governance using network policies and VNFs.

Separation of Duties
:   Administrative and operational boundaries per environment.
