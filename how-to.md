---
copyright:
  years: 2024
lastupdated: "2025-08-13"

keywords:

subcollection: pattern-migrate-os-virtualization

---

{{site.data.keyword.attribute-definition-list}}

# Deploying the OpenShift Virtualization Operator

{: \#unique-id}

This is a short description that introduces the content in this topic. {: shortdesc}

## Before you begin

{: \#unique-id-2}

You need the following items to deploy and configure this reference architecture:

-   An [IBM Cloud account](https://cloud.ibm.com/registration)
-   [Required IAM access policies](https://github.com/terraform-ibm-modules/terraform-ibm-web-app-mzr-da/tree/main/solutions/e2e#required-iam-access-policies).
-   A VPC [public and private SSH key pair](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/source/docs/vpc?topic=vpc-ssh-keys&interface=ui) that is not in the deployment region.
-   An [IBM Cloud API key](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/source/docs/account?topic=account-userapikey&interface=ui) for the user or service ID with the correct IAM access policies.
-   [Secrets Manager Instance](https://cloud.ibm.com/docs/secrets-manager?topic=secrets-manager-create-instance&interface=ui)
-   An [Trusted Profile](https://cloud.ibm.com/docs/secure-enterprise?topic=secure-enterprise-tp-project&interface=ui) for an alternate authentication for project-based access.
-   An understanding of the [Planning for the landing zone deployable architectures](https://github.ibm.com/cloud-docs-solutions/pattern-webapp-openshift-vpc/blob/source/docs/secure-infrastructure-vpc?topic=secure-infrastructure-vpc-plan).

###

###

## Installing the OpenShift Virtualization Operator

{: \#unique-id-3}

This is content under a second-level subheading.

1.  Provision [**Cloud Automation for RedHat OpenShift Virtualization**](https://cloud.ibm.com/catalog/7a4d68b4-cf8b-40cd-a3d1-f49aff526eb3/architecture/deploy-arch-ibm-ocp-virtualization-e4e5b526-5a08-4d63-bea6-04417c30583e-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPXZpcnR1YWxpemF0aW9uI3NlYXJjaF9yZXN1bHRz) deployable architecture in a new or existing Project.
2.  Once the deployable architecture is added to the project, fill in required and optional parameters.

For the OpenShift Virtualization Operator deployable architecture, the following parameters must be set:

-   Security tab: \`api_key\` or \`trusted_profile_id\`, this can be connected to a Secrets Manager instance to input or Trusted profiles.
-   Inputs tab: \`region\` and \`resource_group\`.
3.  Once the validation is successful, click “**Approve**” and add a comment. Then click “**Deploy**” to deploy the plan.

## Installing OpenShift MTV operator

{: \#unique-id-4}

To install and configure the MTV operator on OpenShift cluster, complete the following steps outlined in the [Installing MTV Operator installation guide](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/installing-the-operator#installing-mtv-operator_web).

## Migrating VMWare Instances to OpenShift Virtualization

{: \#unique-id-5}

To migrate VMWare Instances for OpenShift Virtualization, complete the following steps outlined in the [Migrating virtual machines by using the MTV web console.](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console)

1.  Add an [OpenShift Virtualization provider](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console#adding-virt-provider_mtv).
2.  Create a [Migration Plan.](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console#creating-migration-plan_mtv)
3.  [Run your Migration plan](https://docs.redhat.com/en/documentation/migration_toolkit_for_virtualization/2.2/html/installing_and_using_the_migration_toolkit_for_virtualization/migrating-vms-web-console#running-migration-plan_mtv) and view within the MTV web Console.
