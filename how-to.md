---
copyright:
  years: 2025
lastupdated: "2025-10-03"

keywords:

subcollection: pattern-migrate-os-virtualization

---

{{site.data.keyword.attribute-definition-list}}

# Deploying the Red Hat OpenShift Virtualization Operator
{: #unique-id}

You can migrate VMWare workloads from on-premises, colocated, or IBM Cloud Classic, by using the IBM Cloud Red Hat OpenShift Virtualization operator and Migration Toolkit for Virtualization operator. {: shortdesc}

## Before you begin
{: #unique-id-2}

You need the following items to deploy and configure this reference architecture:

-   An [IBM Cloud account](https://cloud.ibm.com/registration)
-   [Required IAM access policies](https://github.com/terraform-ibm-modules/terraform-ibm-web-app-mzr-da/tree/main/solutions/e2e#required-iam-access-policies).
-   A VPC [public and private SSH key pair](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/source/docs/vpc?topic=vpc-ssh-keys&interface=ui) that is not in the deployment region.
-   An [IBM Cloud API key](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/source/docs/account?topic=account-userapikey&interface=ui) for the user or service ID with the correct IAM access policies.
-   [Secrets Manager Instance](https://cloud.ibm.com/docs/secrets-manager?topic=secrets-manager-create-instance&interface=ui)
-   A [Trusted Profile](https://cloud.ibm.com/docs/secure-enterprise?topic=secure-enterprise-tp-project&interface=ui) for an alternative authentication for project-based access.
-   An understanding of the [Planning for the landing zone deployable architectures](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/source/docs/secure-infrastructure-vpc?topic=secure-infrastructure-vpc-plan).

## Installing the Red Hat OpenShift Virtualization Operator
{: #unique-id-3}

To install the operator, you must:

1.  Provision [**Cloud Automation for Red Hat OpenShift Virtualization**](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-ocp-virtualization-e4e5b526-5a08-4d63-bea6-04417c30583e-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPXZpcnR1YWxpemF0aW9uI3NlYXJjaF9yZXN1bHRz) deployable architecture in a new or existing Project.
2.  After the deployable architecture is added to the project, complete the required and optional parameters.

For the Red Hat OpenShift Virtualization Operator deployable architecture, the following parameters must be set:

-   Security tab: \`api_key\` or \`trusted_profile_id\` can be connected to a Secrets Manager instance to input or Trusted profiles.
-   Inputs tab: \`region\` and \`resource_group\`.
3.  After the validation is successful, click “**Approve**” and add a comment. Then, click “**Deploy**” to deploy the plan.

## Installing Red Hat OpenShift MTV operator
{: #unique-id-4}

To install and configure the MTV operator on Red Hat OpenShift cluster, complete the following steps that are outlined in the [Installing MTV Operator installation guide](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/installing-the-operator#installing-mtv-operator_web).

## Creating a Transit Gateway Connection
{: #unique-id-5}

To connect the Red Hat OpenShift Virtualization cluster to the source VMware cluster in either IBM Cloud Classic or the Enterprise location, complete a transit gateway connection.

-   [A VPC](/docs/transit-gateway?topic=transit-gateway-adding-cross-account-connections&interface=ui#tg-ui-adding-cross-account-connection-transit-gateway) network connection configuration or a [Direct Link](/docs/dl?topic=dl-cross-account-virtual-connection-vpc&interface=ui) network configuration.
-   A [Transit Gateway](/docs/transit-gateway?topic=transit-gateway-ordering-transit-gateway&interface=ui#tg-ui-creating-transit-gateway) request is needed for a network connection to another account

## Migrating VMWare Instances to Red Hat OpenShift Virtualization
{: #unique-id-6}

To migrate VMWare Instances for Red Hat OpenShift Virtualization, complete the following steps that are outlined in the [Migrating virtual machines by using the MTV web console.](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console){: external}

1.  Start by adding an [Red Hat OpenShift Virtualization provider](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console#adding-virt-provider_mtv){: external}.
2.  Next, create a [Migration Plan.](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console#creating-migration-plan_mtv){: external}
3.  Afterward, you can [Run your Migration plan](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console#running-migration-plan_mtv){: external} and view within the MTV web Console.

## Additional references
{: #unique-id-7}

-   [Adding worker nodes to VPC clusters](/docs/openshift?topic=openshift-add-workers-vpc)
