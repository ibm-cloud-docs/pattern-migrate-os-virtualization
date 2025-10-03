---

copyright:
  years: 2025
lastupdated: "2025-10-03"

subcollection: pattern-migrate-os-virtualization

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Security design
{: #security-design}

To securely deploy and manage Red Hat OpenShift Virtualization on IBM Cloud, follow a layered approach across infrastructure, cluster, workloads, and data. Deploy clusters within an {{site.data.keyword.vpc_short}} to isolate workloads from public networks and configure private subnets, access-lists, security groups, and firewalls according to your network policies. Ensure that all storage and data traffic is encrypted at rest and in transit by using IBM Key Protect or Hyper Protect Crypto Services (HPCS) to manage encryption keys in compliance with FIPS 140-2 standards. When you are designing for resilience, distribute clusters across multiple availability zones in Secure Multi-Zone Deployments (MZRs) and use IBM Cloud certified datacenters (ISO 27001, SOC 2, PCI DSS, HIPAA) to inherit compliance controls.

At the cluster level, maintain security by enabling automatic updates for the control plane and worker nodes, configuring role-based access control (RBAC) integrated with your enterprise identity provider, and applying Security Context Constraints (SCCs) to enforce least-privilege policies.

API endpoints are securely exposed through IBM Cloud Internet Services (CIS), which provides multiple layers of protection. Traffic is safeguarded by a Web Application Firewall (WAF) to mitigate application-level threats, SSL/TLS encryption to help ensure data confidentiality and integrity, and distributed denial-of-service (DDoS) protection to maintain availability under high-volume attack scenarios. Enable audit logging and monitoring to track activity and detect threats.

For workloads and virtual machines on Red Hat OpenShift Virtualization, enforce namespace isolation, apply resource quotas, and configure network policies to prevent unauthorized access and limit lateral movement. Scan all VM and container images for vulnerabilities before deployment, with admission controllers that are used to enforce compliance and block unverified images. Live migrations must be encrypted and restricted to private networks to protect data in transit. Store sensitive assets such as credentials, certificates, and encryption keys as Kubernetes secrets or manage them through IBM Secrets manager or IBM Key Protect or Hyper Protect Crypto Services (HPCS), with access that is governed by role-based access controls (RBAC) to help ensure least-privilege access.

Protect data by enabling encryption for all persistent storage, configuring secure backups, and using snapshots through CSI-integrated storage add-ons. For File Storage on VPC, enforce NFS access with enterprise-grade access controls to help ensure secure data sharing across workloads. Use advanced storage capabilities from Red Hat OpenShift Data Foundation (ODF) such as replication, erasure coding, and self-healing, to provide resilience and maintain data availability if there is a failure.

Finally, strengthen your security posture by integrating IBM Cloud Security and Compliance Center workload protection to enhance governance and help ensure continuous compliance. Monitor logs, events, and incidents by using IBM QRadar or Cloud Pak for Security to enable proactive threat detection and response. Regularly scan images for vulnerabilities and centralize identity management by integrating with enterprise IAM systems. By adopting these practices, organizations can deploy and operate Red Hat OpenShift Virtualization workloads securely, resiliently, and in alignment with regulatory requirements.
