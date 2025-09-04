---
copyright:
  years: 2025
lastupdated: "2025-09-04"

keywords: virtualization, VMware, SDN, NSX, OpenShift

subcollection: pattern-migrate-os-virtualization

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

# Migrate VMware Workloads to {{site.data.keyword.Bluemix_notm}} OpenShift Virtualization

{: \#pattern-migrate-os-virtualization} {: toc-content-type="deployment"} {: toc-industry="FinancialSector, Manufacturing, Retail, Industrials, Communications"} {: toc-use-case="virtualization, hypervisor, migration, containers"} {: toc-compliance="ISOIEC27001"} {: toc-version="1.0"}

Lift and shift enterprise grade VMware workloads from on premises or hyperscaler based environments to IBM Cloud to take advantage of the unique benefits of a hybrid cloud strategy and best in class modernization capabilities through Red Hat OpenShift Virtualization. Integrated into the broader IBM Cloud, with several offerings bring to customers a known environment for their business applications while enabling access to new cloud technologies and innovations including IBM Watson for AI and platforms for new cloud native apps.

OpenShift Virtualization, uses Kernel-based Virtual Machine (KVM) the trusted Linux kernel hypervisor, delivering enterprise-grade virtualization, for virtual machines, as native objects within OpenShift. Virtual machines within OpenShift Virtualization benefit from sophisticated scheduling and management capabilities, including host affinity, resource awareness, load balancing, and built-in high availability.

Networking capabilities include connection to the integrated cluster software-defined network (SDN), enabling secure and controlled access to virtual machines through configurable network policies. Red Hat OpenShift, with its integrated OpenShift Virtualization capabilities, offers a unified platform for running both containerized and traditional virtual machine workloads.

## Architecture diagram

{: \#architecture-diagram}

The following diagram shows the high level reference architecture for this pattern:

![High level architecture diagram for the Migrate VMware Workloads to {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift Virtualization](/images/deployable-architecture-ocp-virtualization-cluster.svg){: caption="Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization" caption-side="bottom"}

## Design scope

{: \#design-scope}

Following the [Architecture Design Framework](/docs/architecture-framework?topic=architecture-framework-taxonomy), Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization covers design considerations and architecture decisions for the following aspects and domains:

-   Compute: Virtual servers, Virtualization
-   Storage: Primary, Backup
-   Networking: Enterprise Connectivity, Cloud Native Connectivity, Load Balancing and Domain name system
-   Security: Data, Identity and Access Management,
-   Resiliency: Backup and Restore, High Availability
-   Service Management: Monitoring, Logging, Alerting, Auditing/tracking, Event management and Management/Orchestration

The Architecture Design Framework, described in [Introduction to the Architecture Design Framework](/docs/architecture-framework?topic=architecture-framework-intro), provides a consistent approach to design cloud solutions by addressing requirements across a pre-defined set of aspects and domains, which are technology-agnostic architectural areas that need to be considered for any enterprise solution. It can be used as a guide to make the necessary design and component choices to ensure that you have considered applicable requirements for each aspect and domain. After you have identified the applicable requirements and domains that are in scope, you can evaluate and select the best fit for purpose components for your enterprise cloud solution.

![A screen shot of a computer Description automatically generated](images/heat-map-MV-OCP-V.svg){: caption="Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization design scope" caption-side="bottom"}

## Requirements

{: \#requirements}

Update the following table with requirements for this architecture. Introduce the table with a sentence. For example, "The following table outlines the requirements that are addressed in this architecture."

| Aspect             | Requirements                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute            | Provide a single orchestration platform, for deploying, managing, scaling virtual machines and container instances. \\n Provide for VM migration of live virtual machines between hosting nodes. \\n Provide active compute resource balancing across hosting nodes. \\n Maintain current workload environments segregation, segmentation for compliance. \\n Maintain virtualized workload high availability service level agreement.                                                                                                                                                                                                                                                                 |
| Storage            | Provide storage that meets the application and database performance requirements. \\n Provide policy-based storage management.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Networking         | Deploy workloads in isolated environment and enforce information flow policies. \\n Provide secure, encrypted connectivity to the cloud’s private network for management purposes. \\n Distribute incoming application requests across available compute resources. \\n Provide public and private DNS resolution to support use of hostnames instead of IP addresses.                                                                                                                                                                                                                                                                                                                                 |
| Security           | Ensure all operator actions are executed securely through a bastion host. \\n Protect the boundaries of the application against denial-of-service and application-layer attacks. \\n Encrypt all application data in transit and at rest to protect from unauthorized disclosure. \\n Encrypt all backup data to protect from unauthorized disclosure. \\n Encrypt all security data (operational and audit logs) to protect from unauthorized disclosure. \\n Encrypt all data using customer managed keys to meet regulatory compliance requirements for additional security and customer control. \\n Protect secrets through their entire lifecycle and secure them using access control measures. |
| Resiliency         | Provide highly available compute, storage, network, and other cloud services to handle application load and performance requirements. \\n Backup application data to enable recovery in the event of unplanned outages. \\n Provide highly available storage for security data (logs) and backup data.                                                                                                                                                                                                                                                                                                                                                                                                 |
| Service Management | Monitor system and application health metrics and logs to detect issues that might impact the availability of the application. \\n Generate alerts/notifications about issues that might impact the availability of applications to trigger appropriate responses to minimize down time. \\n Monitor audit logs to track changes and detect potential security problems. \\n Provide a mechanism to identify and send notifications about issues found in audit logs.                                                                                                                                                                                                                                  |

{: caption="Requirements" caption-side="bottom"}

## Components

{: \#components}

Update the following table below with components that are unique to this architecture. Introduce the table with a sentence. For example, "The following table outlines the products or services used in the architecture for each aspect."

| Aspects                                                | Architecture components                                  | How the component is used                                                                                                                                                     |
|--------------------------------------------------------|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute                                                | OpenShift Virtualization Cluster                         | Provides the infrastructure for virtual machines. Virtual machine lifecycle, non-disruptive VM migration and active resource balancing across the cluster of bare metal nodes |
| Storage                                                | IBM Cloud File Storage for VPC                           | File storage providing NFS-based file storage                                                                                                                                 |
|                                                        | Object Storage                                           | Backups, Archiving, logs (application, operational, and audit logs)                                                                                                           |
|                                                        | OpenShift Data Foundation                                | With CSI provider to host VM disks through Persistent Volume and Persistent Volume Claim                                                                                      |
| Networking                                             | VPC Virtual Private Network (VPN)                        | Remote access to manage resources in private network                                                                                                                          |
|                                                        | Virtual Private Gateway & Virtual Private Endpoint (VPE) | For private network access to Cloud Services, e.g., Key Protect, COS, etc.                                                                                                    |
|                                                        | VPC Load Balancers                                       | Application Load Balancing for web servers, app servers, and database servers                                                                                                 |
|                                                        | Public Gateway                                           | For web server access to the internet                                                                                                                                         |
| Security                                               | IAM                                                      | IBM Cloud Identity & Access Management                                                                                                                                        |
|                                                        | BYO Bastion Host on VPC VSI                              | Remote access with Privileged Access Management                                                                                                                               |
|                                                        | Key protect                                              | Key Management Service                                                                                                                                                        |
|                                                        | Secrets Manager                                          | Certificate and Secrets Management                                                                                                                                            |
| Resiliency                                             | Live migration                                           | Physical servers with VM and Storage anti-affinity policy                                                                                                                     |
| Service Management                                     | IBM Cloud Monitoring                                     | Apps and operational monitoring                                                                                                                                               |
|                                                        | IBM Log Analysis                                         | Apps and operational logs                                                                                                                                                     |
|                                                        | Activity Tracker Event Routing                           | Audit logs                                                                                                                                                                    |
| Other use if there is additional aspect(s) Name Aspect | Cell content                                             | Cell content                                                                                                                                                                  |

{: caption="Components" caption-side="bottom"}

## Compliance

{: \#compliance}

*Optional section.* Feedback from users implies that architects want only the high-level compliance items and links off to control details that team members can review. Include the list of control profiles or compliance audits that this architecture meets. For controls, provide "learn more" links to the control library that is published in the IBM Cloud Docs. For audits, provide information about the compliance item.

## Next steps

{: \#next-steps}

*Optional section.* Include links to your deployment guide or next steps to get started with the architecture.

:exclamation: **Important:** Rename this file `<architecture-name>.md`. For deployable architectures, `<architecture-name>` is the same as the deployable architecture name.
