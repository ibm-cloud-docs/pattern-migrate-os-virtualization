---
copyright:
  years: 2025
lastupdated: "2026-06-15"

keywords: virtualization, VMware, SDN, NSX, OpenShift

subcollection: pattern-migrate-os-virtualization

Keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Migrate VMware Workloads to {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift Virtualization
{: #openshift-virt-arch}

Migrate enterprise production grade VMware workloads from on premises or hyperscaler VMware based environments to IBM Cloud Red Hat OpenShift Virtualization to take advantage of the unique benefits of a hybrid cloud strategy and best in class cloud native platform capabilities through Red Hat OpenShift Virtualization. This solution is integrated into the broader IBM Cloud, with several offerings to bring to customers a known environment for their business applications, which enables access to new cloud technologies and innovations, including IBM Watson for AI and platforms for new cloud native apps.

## Architecture diagram
{: #architecture-diagram}

The following diagram shows the high-level reference architecture for this pattern:

![High-level architecture diagram for the Migrate VMware Workloads to {{site.data.keyword.Bluemix_notm}} Red Hat OpenShift Virtualization](/images/architecture-overview.svg){: caption="Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization" caption-side="bottom"}

## Design scope
{: #design-scope}

Following the [Architecture Design Framework](/docs/architecture-framework?topic=architecture-framework-taxonomy), Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization covers design considerations and architecture decisions for the following aspects and domains:

-   Compute: Virtual servers, Virtualization, and Migration
-   Storage: Primary, Backup
-   Networking: Enterprise Connectivity, Cloud Native Connectivity, and Domain name system
-   Security: Data, Identity and Access Management
-   Resiliency: Back up and Restore, High Availability
-   Service Management: Monitoring, Logging, Alerting, Auditing

![A screen capture of a computer Description automatically generated](images/heat-map-MV-OCP-V.svg){: caption="Migrate VMware Workloads to IBM Cloud Red Hat OpenShift Virtualization design scope" caption-side="bottom"}

## Requirements
{: #requirements}

Update the following table with requirements for this architecture. Introduce the table with a sentence. For example, "The following table outlines the requirements that are addressed in this architecture."

| Aspect             | Requirements                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute            | Provide a single orchestration platform, for deploying, managing, scaling virtual machines and container instances. \\n Provide for live migration of virtual machines between hosting nodes. \\n Provide for dynamic optimized resource utilization across worker pools. \\n Maintain current workload environments isolation and segmentation for compliance. \\n Maintain virtualized workload high availability service level agreement. \\n Provide warm migration capability for production workloads from VMware to Red Hat OpenShift Virtualization.                                                                                                                                                   |
| Storage            | Provide storage that meets the application and database performance requirements. \\n Provide policy-based storage management.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Networking         | Maintain existing production and nonprod regulatory compliance network segmentation. \\n Provide DNS resolution across virtual and container instances. \\n Provide load balancing across virtual instances and containers. \\n Maintain existing workload ip addresses. \\n Provide private connectivity to IBM Cloud services.                                                                                                                                                                                                                                                                                                                                                                                          |
| Security           | Ensure that all operator actions are run securely through a bastion host. \\n Protect the boundaries of the application against denial-of-service and application-layer attacks. \\n Encrypt all application data in transit and at rest to protect it from unauthorized disclosure. \\n Encrypt all backup data to protect from unauthorized disclosure. \\n Encrypt all security data (operational and audit logs) to protect from unauthorized disclosure. \\n Encrypt all data by using customer-managed keys to meet regulatory compliance requirements for extra security and customer control. \\n Protect secrets through their entire lifecycle and secure them using access control measures. |
| Resiliency         | Provide highly available compute, storage, network, and other cloud services to handle application load and performance requirements. \\n Backup application data to enable recovery if there are unplanned outages. \\n Provide highly available storage for security data (logs) and backup data.                                                                                                                                                                                                                                                                                                                                                                                                 |
| Service Management | Monitor systems health metrics and logs to detect issues that might impact the availability of the workload. \\n Generate alerts and notifications about issues that might impact the availability of workload to trigger appropriate responses to minimize downtime. \\n Monitor audit logs to track changes and detect potential security problems. \\n Provide a mechanism to identify and send notifications about issues that are found in audit logs. \\n Ability to diagnose issues and exceptions and identify error source. Get insight into the performance of workloads.                                                                                                                            |
{: caption="Requirements" caption-side="bottom"}

## Components
{: #components}

Update the following table with components that are unique to this architecture. Introduce the table with a sentence. For example, "The following table outlines the products or services that are used in the architecture for each aspect."

| Aspects            | Architecture components                                            | How the component is used                                                                                                                                                                                                                         |
|--------------------|--------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Compute            | Red Hat OpenShift Virtualization                                           | Provides the infrastructure for virtual machines. Virtual machine lifecycle, nondisruptive VM migration and active resource balancing across the cluster of bare metal nodes.                                                                    |
|                    | Migration Toolkit for virtualization                               | Provides for VMware virtual machine cold and warm migration to Red Hat OpenShift Virtualization.                                                                                                                                                          |
|                    | Live migration                                               | Live migration provides dynamic resource balancing of CPU RAM resources across the worker pool to optimize compute utilization.                                                                                                              |
| Storage            | IBM Cloud File Storage for VPC                                     | File storage that provides NFS-based file storage.                                                                                                                                                                                                    |
|                    | Object Storage                                                     | Backups, Archiving, logs (application, operational, and audit logs).                                                                                                                                                                              |
|                    | Red Hat OpenShift Data Foundation                                          | With CSI provider to host VM disks through Persistent Volume and Persistent Volume Claim.                                                                                                                                                         |
| Networking         | {{site.data.keyword.vpc_short}}                                          | Virtual private cloud for worker Node subnets.                                                                                                                                                                                             |
|                    | Virtual Private Endpoint (VPE)           | For private network access to Cloud Services, for example, Key Protect, Cloud Object Storage, and so on.                                                                                                                                                                        |
|                    | Direct Link                                                        | Enterprise or Cloud connectivity to source VMware datacenter.                                                                                                                                                                                     |
|                    | Transit Gateway                                                    | Connectivity between workload and management VPCs.                                                                                                                                                                                |
|                    | VPC application load balancer                                      | Provides for routing traffic to both Virtual instances pods and container pods.                                                                                                                                                                   |
|                    | IBM Cloud DNS                                                      | Provides Domain Name Resolution.                                                                                                                                                                                                                  |
| Security           | IAM                                                                | IBM Cloud Identity & Access Management.                                                                                                                                                                                                           |
|                    | Key Protect                                                        | Key Management Service.                                                                                                                                                                                                                           |
|                    | Secrets Manager                                                    | Certificate and Secrets Management.                                                                                                                                                                                                               |
|                    | IBM Cloud Security and Compliance Center (SCC) Workload Protection | Integrates governance, risk and compliance capabilities by enforcing security policies, assessing risk, and automating compliance reporting for standards list NIST, PCI DSS, and GDPR.                                                            |
| Service Management | IBM Cloud Monitoring                                               | IBM Cloud Monitoring collects and monitors metrics from the VPC and Red Hat OpenShift resources.                                                                                                                                                          |
|                    | IBM Cloud Logs                                                     | IBM Cloud Logs provides observability services for IBM Cloud so you can view, analyze, and alert on activity tracking events and logging activity.                                                                                                |
|                    | IBM Cloud Event Notification                                       | IBM Cloud Event Notifications is a routing service that provides information about critical events that occur in the VPC resources or Red Hat OpenShift Cluster – triggering automated actions by using webhooks.                                              |
|                    | IBM Cloud Flow Logs for VPC                                        | IBM Cloud Flow Logs for VPC provides the collection, storage, and presentation of information about the Internet Protocol (IP) traffic that goes to and from network interfaces on the Red Hat OpenShift worker nodes within the Virtual Private Cloud (VPC). |
|                    | Red Hat OpenShift GitOps                                                   | Provides for declarative implementation of the virtual machine and operating system desired state.                                                                                                                                                    |
|                    | Red Hat OpenShift Pipelines                                                | Provides for execution of the CI/CD workflows for virtual machine and operating system lifecycle within a DevSecOps delivery model.                                                                                                               |
{: caption="Components" caption-side="bottom"}
