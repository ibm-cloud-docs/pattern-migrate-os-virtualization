---
copyright:
  years: 2025
lastupdated: "2025-09-22"

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

Lift and shift enterprise grade VMware workloads from on premises or hyperscaler VMware based environments to IBM Cloud OpenShift Virtualization to take advantage of the unique benefits of a hybrid cloud strategy and best in class cloud native platform capabilities through Red Hat OpenShift Virtualization. Integrated into the broader IBM Cloud, with several offerings bring to customers a known environment for their business applications while enabling access to new cloud technologies and innovations including IBM Watson for AI and platforms for new cloud native apps.

## Architecture diagram

{: \#architecture-diagram}

The following diagram shows the high level reference architecture for this pattern:

![High level architecture diagram for the Migrate VMware Workloads to {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift Virtualization](/images/overallarchitecture.svg){: caption="Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization" caption-side="bottom"}

## Design scope

{: \#design-scope}

Following the [Architecture Design Framework](/docs/architecture-framework?topic=architecture-framework-taxonomy), Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization covers design considerations and architecture decisions for the following aspects and domains:

-   Compute: Virtual servers, Virtualization and Migration
-   Storage: Primary, Backup
-   Networking: Enterprise Connectivity, Cloud Native Connectivity, and Domain name system
-   Security: Data, Identity and Access Management,
-   Resiliency: Backup and Restore, High Availability
-   Service Management: Monitoring, Logging, Alerting, Auditing

![A screen shot of a computer Description automatically generated](images/heat-map-MV-OCP-V.svg){: caption="Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization design scope" caption-side="bottom"}

## Requirements

{: \#requirements}

Update the following table with requirements for this architecture. Introduce the table with a sentence. For example, "The following table outlines the requirements that are addressed in this architecture."

| Aspect             | Requirements                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute            | Provide a single orchestration platform, for deploying, managing, scaling virtual machines and container instances. \\n Provide for live migration of virtual machines between hosting nodes. \\n Provide for dynamic optimized resource utilisation across worker pools. \\n Maintain current workload environments isolation and segmentation for compliance. \\n Maintain virtualized workload high availability service level agreement. \\n Provide warm migration capability for production workloads from VMware to OpenShift Virtualization                                                                                                                                                    |
| Storage            | Provide storage that meets the application and database performance requirements. \\n Provide policy-based storage management.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Networking         | Maintain existing VMware network segregation \\n Provide DNS resolution across virtual and container instances \\n Provide load balancing across virtual instances and containers \\n Provide that application network changes are not required (BYOIP) \\n Provide network connectivity for migrating VMware workloads \\n Provide private connectivity to IBM Cloud services                                                                                                                                                                                                                                                                                                                         |
| Security           | Ensure all operator actions are executed securely through a bastion host. \\n Protect the boundaries of the application against denial-of-service and application-layer attacks. \\n Encrypt all application data in transit and at rest to protect from unauthorized disclosure. \\n Encrypt all backup data to protect from unauthorized disclosure. \\n Encrypt all security data (operational and audit logs) to protect from unauthorized disclosure. \\n Encrypt all data using customer managed keys to meet regulatory compliance requirements for additional security and customer control. \\n Protect secrets through their entire lifecycle and secure them using access control measures. |
| Resiliency         | Provide highly available compute, storage, network, and other cloud services to handle application load and performance requirements. \\n Backup application data to enable recovery in the event of unplanned outages. \\n Provide highly available storage for security data (logs) and backup data.                                                                                                                                                                                                                                                                                                                                                                                                 |
| Service Management | Monitor system and application health metrics and logs to detect issues that might impact the availability of the workload. \\n Generate alerts/notifications about issues that might impact the availability of workload to trigger appropriate responses to minimize down time. \\n Monitor audit logs to track changes and detect potential security problems. \\n Provide a mechanism to identify and send notifications about issues found in audit logs.                                                                                                                                                                                                                                         |

{: caption="Requirements" caption-side="bottom"}

## Components

{: \#components}

Update the following table below with components that are unique to this architecture. Introduce the table with a sentence. For example, "The following table outlines the products or services used in the architecture for each aspect."

| Aspects                    | Architecture components                                  | How the component is used                                                                                                                                                                            |
|----------------------------|----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute                    | OpenShift Virtualization                                 | Provides the infrastructure for virtual machines. Virtual machine lifecycle, non-disruptive VM migration and active resource balancing across the cluster of bare metal nodes                        |
|                            | Migration Toolkit for virtualization                     | Provides virtual machine cold and warm migration.                                                                                                                                                    |
| Storage                    | IBM Cloud File Storage for VPC                           | File storage providing NFS-based file storage                                                                                                                                                        |
|                            | Object Storage                                           | Backups, Archiving, logs (application, operational, and audit logs)                                                                                                                                  |
|                            | OpenShift Data Foundation                                | With CSI provider to host VM disks through Persistent Volume and Persistent Volume Claim                                                                                                             |
| Networking                 | VPC Virtual Private Cloud                                | Virtual private cloud for workload isolation subnets                                                                                                                                                 |
|                            | Virtual Private Gateway & Virtual Private Endpoint (VPE) | For private network access to Cloud Services, e.g., Key Protect, COS, etc.                                                                                                                           |
|                            | Direct Link                                              | Enterprise or Cloud connectivity to source VMware datacenter                                                                                                                                         |
|                            | Transit Gateway                                          | Connectivity between workload, management and cloud services VPCs                                                                                                                                    |
|                            | VPC application load balancer                            | Provides for routing traffic to both Virtual instances pods and container pods                                                                                                                       |
|                            | IBM Cloud DNS                                            | Provides Domain Name Resolution                                                                                                                                                                      |
| Security                   | IAM                                                      | IBM Cloud Identity & Access Management                                                                                                                                                               |
|                            | Key protect                                              | Key Management Service                                                                                                                                                                               |
|                            | Secrets Manager                                          | Certificate and Secrets Management                                                                                                                                                                   |
| Dynamic Resource Balancing | Live migration and Descheduler Operator                  | Descheduler Operator used with live migration to balance resource utilisation across the worker pool                                                                                                 |
| Service Management         | IBM Cloud Monitoring                                     | IBM Cloud Monitoring collects and monitors metrics from the VPC and OpenShift resources                                                                                                              |
|                            | IBM Cloud Logs                                           | IBM Cloud Logs provides observability services for IBM Cloud so you can view, analyze, and alert on activity tracking events and logging activity.                                                   |
|                            | IBM Cloud Event Notification                             | IBM Cloud Event Notifications is a routing service providing information about critical events occurring in the VPC resources or OpenShift Cluster – triggering automated actions by using webhooks. |

{: caption="Components" caption-side="bottom"}
