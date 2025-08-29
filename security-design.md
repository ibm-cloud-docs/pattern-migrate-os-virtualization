---

copyright:
  years: 2025
lastupdated: "2025-08-29"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Security design
{: #security-design}

To securely deploy and manage Red Hat OpenShift Virtualization on IBM Cloud, follow a layered approach across infrastructure, cluster, workloads, and data. Deploy clusters within an IBM Cloud Virtual Private Cloud (VPC) to isolate workloads from public networks and configure private subnets, access-lists, security groups and firewalls according to your network policies. Ensure all storage and data traffic is encrypted at rest and in transit, using IBM Key Protect or Hyper Protect Crypto Services (HPCS) to manage encryption keys in compliance with FIPS 140-2 standards. When designing for resilience, distribute clusters across multiple availability zones in Secure Multi-Zone Deployments (MZRs) and leverage IBM Cloud’s certified datacentres (ISO 27001, SOC 2, PCI DSS, HIPAA) to inherit compliance controls.

At the cluster level, maintain security by enabling automatic updates for the control plane and worker nodes, configuring Role-Based Access Control (RBAC) integrated with your enterprise identity provider, and applying Security Context Constraints (SCCs) to enforce least-privilege policies.   

API endpoints are securely exposed through IBM Cloud Internet Services (CIS), which provides multiple layers of protection. Traffic is safeguarded by a Web Application Firewall (WAF) to mitigate application-level threats, SSL/TLS encryption to ensure data confidentiality and integrity, and distributed denial-of-service (DDoS) protection to maintain availability under high-volume attack scenarios. Enable audit logging and monitoring to track activity and detect threats.  

For workloads and virtual machines on Red Hat OpenShift Virtualization, enforce namespace isolation, apply resource quotas, and configure network policies to prevent unauthorized access and limit lateral movement. All VM and container images should be scanned for vulnerabilities before deployment, with admission controllers used to enforce compliance and block unverified images. Live migrations must be encrypted and restricted to private networks to 
protect data in transit. Sensitive assets such as credentials, certificates, and encryption keys should be stored in Kubernetes Secrets or managed through IBM Secrets manager or IBM Key Protect or Hyper Protect Crypto Services (HPCS), with access governed by role-based access controls (RBAC) to ensure least-privilege access.  

Protect data by enabling encryption for all persistent storage, configuring secure backups, and leveraging snapshots through CSI-integrated storage add-ons. For File Storage on VPC, enforce NFS access with enterprise-grade access controls to ensure secure data sharing across workloads. Use advanced storage capabilities from OpenShift Data Foundation (ODF) or IBM Storage Fusion, such as replication, erasure coding, and self-healing, to provide resilience and maintain data availability in the event of failures.

Finally, strengthen your security posture by integrating IBM Cloud Security and Compliance Center workload protection to enhance governance and ensure continuous compliance. Monitor logs, events, and incidents using IBM QRadar or Cloud Pak for Security to enable proactive threat detection and response. Regularly scan images for vulnerabilities and centralize identity management by integrating with enterprise IAM systems. By adopting these practices, organizations can deploy and operate Red Hat OpenShift Virtualization workloads securely, resiliently, and in alignment with regulatory requirements.
