---

copyright:
  years: 2025
lastupdated: "2023-12-18"

subcollection: pattern-vpc-vsi-multizone-resiliency

keywords:

---

# Architecture decisions for security
{: #security-architecture}



The following are security architecture decisions for the pattern name.

## Architecture decisions for data security - encryption
{: #data-encryption}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Encryption approach | Encrypt all data to protect it from unauthorized disclosure. | - Encryption with provider keys \n - Encryption with customer-managed keys | Encryption with customer-managed keys | Using encryption with customer-managed keys gives organizations direct control over encryption, letting them own, rotate, and revoke keys to meet compliance requirements, enforce zero-trust security, limit insider risk, and maintain data portability. This approach provides granular access control, auditability, and the ability to immediately render data inaccessible if keys are revoked, ensuring stronger security and customer trust |
| Data encryption at rest of primary storage | Encrypt all application data to protect it from unauthorized disclosure. | - Storage encryption with provider-managed keys \n - Storage encryption with customer-managed keys \n - App-level encryption with customer-managed keys | Storage encryption with provider-managed keys | Storage encryption with provider-managed keys automatically protects the worker node’s OS and system files at rest using provider-controlled keys, ensuring confidentiality without customer-managed key overhead. |
| Data encryption at rest of backups | Encrypt all backup data to protect it from unauthorized disclosure. | - Encryption with provider keys \n - Encryption with customer-managed keys | Encryption with customer-managed keys | Using customer-managed keys for backup storage encryption allows organizations to control the encryption keys that protect backup data, enabling key rotation, revocation, and auditability, ensuring compliance, stronger security, and the ability to render backups inaccessible if needed. |
| Data encryption at rest of logs | Encrypt all operational and audit logs at rest to protect them from unauthorized disclosure. | - Encryption with provider keys \n - Encryption with customer-managed keys | Encryption with customer-managed keys | teEncrypting logs at rest with customer-managed keys gives organizations control over key management, ensuring security, compliance, and the ability to restrict or revoke access as needed.xt |
| Data encryption in transit of web app | Encrypt all application data in transit to protect it from unauthorized disclosure. | Application-level encryption with TLS | Application-level encryption with TLS | Web app uses HTTPS protocol to encrypt data transmissions. |
| Data encryption in transit of DB tier | Encrypt all application data in transit to protect it from unauthorized disclosure. | Application-level encryption with TLS | Application-level encryption with TLS | The database application uses TLS to encrypt data in transit. |
{: caption="Data encryption architecture decisions" caption-side="bottom"}

## Architecture decisions for data security - key management
{: #kms}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Key lifecycle management and HSM | Encrypt data at rest and in transit by using customer-managed keys to protect them from unauthorized access.  | - Key Protect \n - Hyper Protect Crypto Services (HPCS) | Key Protect | Key Protect is recommended for applications that need to comply with regulations requiring encryption of data with customer-managed keys. Key Protect provides key management services by using a shared (multi-tenant) FIPS 140-2 Level 3 certified hardware security modules (HSMs). |
| | | | Hyper Protect Crypto Services (HPCS) | HPCS is recommended for financial services and highly regulated industry applications. HPCS provides Key Management Services with the highest level of security and control that is offered by any cloud provider in the industry. It uses a dedicated (single-tenant) FIPS 140-2 Level 4 certified Hardware Security Module and supports customer-managed master keys, giving the customer exclusive control of the entire key hierarchy. |
| Certificate management | Protect secrets through their entire lifecycle and secure them using access control measures | Secrets Manager \n BYO Certificate Manager | Secrets Manager | IBM Secrets Manager creates, leases, and centrally manages secrets that are used by IBM Cloud Services or customer applications. Secrets are stored in a dedicated instance of Secrets Manager and can be encrypted by using any of IBM Cloud Key Management Services. |
{: caption="Key management architecture decisions" caption-side="bottom"}

## Architecture decisions for identity and access management
{: #iam}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Identity access & role management (IDM) | Securely authenticate users for platform services and control access to resources consistently across IBM Cloud| IBM Cloud IAM| IBM Cloud IAM| Use IAM access policies to assign users, service IDs, and trusted profiles access to resources within the IBM Cloud account.|
{: caption="Identity and access management architecture decisions" caption-side="bottom"}

## Architecture decisions for application security
{: #app-security}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| DDoS | - Enforce information flow policies and protect the boundaries of the application. \n - Protect against or limit the effects of denial-of-service attacks. | IBM Cloud Internet Services (CIS) | IBM Cloud Internet Services (CIS) | IBM Cloud Internet Services provide Distributed Denial of Service (DDoS) to protect applications that are exposed to the public network. |
| SSL/TLS | - Enforce information flow policies and protect the boundaries of the application. \n - Protect against or limit the effects of denial-of-service attacks. | IBM Cloud Internet Services (CIS) | IBM Cloud Internet Services (CIS) | IBM Cloud Internet Services provide SSL/TLS (Secure Sockets Layer / Transport Layer Security) to protect applications that are exposed to the public network. |
| Web application firewall | Protect web applications from application layer attacks. | - IBM Cloud Internet Services (CIS) \n - BYO Firewall on Virtual Server for VPC | IBM Cloud Internet Services (CIS) | IBM Cloud Internet Services provides Web Application Firewall security features to protect applications that are exposed to the public network. |
{: caption="Application security architecture decisions" caption-side="bottom"}

## Architecture decisions for infrastructure and endpoint
{: #infrastructure and endpoint}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Core network protection                 | -   Strict separation of duties \n-   Isolated security zones between environments \n-   Isolated, private cloud environment | Red Hat OpenShift on IBM Cloud (VPC) | - **Network Isolation and Segmentation:** Virtual networks (VPCs) and subnets isolate OpenShift clusters and virtual machines (KVM-based VMs), limiting lateral movement of threats. \n - **Access-lists and Security Groups:** Control inbound/outbound traffic at the VM and subnet level to enforce strict access policies. \n - **Policy-Driven Access Control:** Role-based access control (RBAC) and network policies restrict which pods or VMs can communicate, reducing attack surfaces. | Core network protection for OpenShift Virtualization on IBM Cloud secures virtualized workloads through network isolation, segmentation, access-lists, security groups, and policy-driven access controls, with encrypted communication, and continuous monitoring to ensure compliance and reduce attack surfaces. |
| Edge and endpoint protection  | - Worker node Security \n - Resource Isolation \n - Least Privilege & Access Control \n - Network Segmentation \n - Encryption (in-transit & at-rest) \n - Resilience & High Availability \n - Observability, Logging, Monitoring and Activity Tracker \n Secrets and Key management \n - Incident Response & Recovery | Red Hat OpenShift Virtualization on IBM Cloud (VPC) | Red Hat OpenShift Virtualization on IBM Cloud (VPC) | Red Hat OpenShift Virtualization on IBM Cloud VPC secures edge and endpoint protection for workloads through private networking, encrypted storage, strong workload isolation, and strict access controls, with automated patching and centralized logging to maintain a consistent, resilient, and compliant security posture across distributed environments. |
{: caption="Infrastructure and endpoint architecture decisions" caption-side="bottom"}

## Architecture decisions for threat detection and response
{: #threat detection and response}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
|Threat detection and response|- Boundary protection: highest level of isolation from external network threats \n - IPS/IDS protection at all ingress/egress \n - Unified Threat Management (UTM) Firewall|BYO Virtual Firewall (on VSI) in Edge VPC (deployed across availability zones) client choices: \n [Fortigate](https://cloud.ibm.com/catalog/content/ibm-fortigate-AP-HA-terraform-deploy-5dd3e4ba-c94b-43ab-b416-c1c313479cec-global)  \n  [Juniper vSRX](https://cloud.ibm.com/catalog/content/juniper-vsrx-catalog-deploy-1.4-dc1e707c-33dd-4321-b2a5-c22dbf0dd0ee-global) \n [Palo Alto](https://cloud.ibm.com/catalog/content/ibmcloud-vmseries-1.9-6470816d-562d-4627-86a5-fe3ad4e94b30-global)| Firewall choice should align with in-house expertise, balancing control and simplicity |Can be provided by Enterprise Network DMZ \n In addition, if client requires: \n - Virtual FW on VSI in the Transit/Edge VPC \n - Client preference however recommendation is Fortigate or Juniper \n - Fortigate supports native HA configuration \n - Fortigate and Juniper both support both IPS & IDS|
{: caption="Threat detection and response architecture decisions" caption-side="bottom"}

## Architecture decisions for governance, risk and compliance
{: #governance, risk and compliance}

| Architecture decision | Requirement |  Option | Decision | Rationale |
| -------------- | -------------- | -------------- | -------------- | -------------- |
|Governance, risk and compliance| - Continuous compliance monitoring \n - Risk assessment and scoring \n - Policy enforcement \n - Threat detection and response \n - Vulnerability management \n - Cloud security posture management (CSPM) \n - Automated reporting for audits \n - Unified Security and compliance across hybrid cloud  | - IBM Cloud Security and Compliance Center (SCC) Workload Protection | IBM Cloud Security and Compliance Center (SCC) Workload Protection | IBM Cloud Security and Compliance Center (SCC) provides centralized workload protection for OpenShift Virtualization and container environments by continuously monitoring VMs and containerized workloads for vulnerabilities, misconfigurations, and security risks. It integrates governance, risk, and compliance (GRC) capabilities by enforcing security policies, assessing risk exposure, and automating compliance reporting for standards like CIS Benchmarks, NIST, PCI DSS, and GDPR. SCC enables organizations to maintain audit-ready environments, ensure regulatory adherence, and integrate security into DevSecOps pipelines, providing end-to-end visibility and protection across hybrid and cloud-native workloads.|
{: caption="Govenrnace, risk and compliance architecture decisions" caption-side="bottom"}
