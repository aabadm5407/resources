---

copyright:

  years: 2015, 2020

lastupdated: "2020-03-03"

keywords: resource FAQs, resource frequently asked questions, resource groups

subcollection: resources

---


{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# FAQs for managing resources
{: #resources-faq}

## What is a resource group?
{: #resource-group}
{: faq}

A resource group is a way for you to organize your account resources in customizable groupings. Any account resource that is managed by using {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) access control belongs to a resource group within your account. You assign resources to a resource group when you create them from the catalog. You can then view usage per resource group in your account, and easily assign users access to all resources in a resource group or just to a single resource in a resource group.

For more information about creating and working with resource groups, see [Managing resource groups](/docs/resources?topic=resources-rgs).  

## Why should I migrate my Cloud Foundry service instances to a resource group?
{: #instance-migrated}
{: faq}

Migrating your Cloud Foundry services to a resource group means that the services you're using are now available for use with IAM access control and resource groups. You can take advantage of fine-grained access control by using IAM roles. You can also view usage per resource group in your account. 

When you have Cloud Foundry services that can be migrated to a resource group, you receive a notification on your resource list. For more information about the migration process, see [Migrating Cloud Foundry service instances and apps to a resource group](/docs/resources?topic=resources-migrate).

## Why can't I add a resource to a resource group?
{: #create-add-resource}
{: faq}

Most likely you're dealing with an access issue. You must have at least the Viewer role on the resource group itself and at least the Editor role on the service in the account. Learn more in [Adding resources to a resource group](/docs/resources?topic=resources-rgs#add_to_rgs).

For more information about how to check your assigned access, see [Reviewing your assigned access](/docs/iam?topic=iam-iammanidaccser#review_your_access).

If you need additional access in the account, contact the account owner that is listed on the [Users](https://{DomainName}/iam#/users) page. 

## Who can create resource groups?
{: #create-resource}
{: faq}

You can create resource groups only if you're assigned the Administrator role on All Account Management services in the account.

Lite accounts can have only the default resource group, so you can't create any additional resource groups even if you have the required access.

## Can I delete a resource group?
{: #delete-resource-group}
{: faq}

Yes, you can delete a resource group only if it doesn't contain any resources, and it's not the default resource group. See [Deleting a resource group](/docs/resources?topic=resources-rgs#delete_rgs) for more information. 

## Can I move service instances between resource groups?
{: #instances-between-rgs}
{: faq}

You can't move service instances between resource groups. If you assign a service instance incorrectly, you must delete and recreate the instance to assign it to another resource group.  

## How do I delete a service from my account?
{: #service-removal}
{: faq}

You can delete a service instance by using the following steps:

1. From your dashboard, click **View resources** within the Resources summary widget.
2. Expand the sections to locate the service instance that you want to delete.
3. Select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu for the row, and click **Delete**.

## Can I view usage per resource group?
{: #view-usage}
{: faq}

Yes, you can. To open the Usage Dashboard page, in the IBM Cloud console, click **Manage** &gt; **Billing and usage**. Select **Usage** to view a summary of the usage by resource group for the account. 

## Who can add tags to a resource?
{: #tag-faq}
{: faq}

Any user assigned the correct access for the specific type of resource can add tags. When a resource is tagged, it is visible to all users who have read access to the resource. However, to add or remove a tag from a resource, certain access roles or permissions are required depending on the resource type. For example, for any resources that are managed by using IAM, you must be assigned the Editor or Administrator role on the resource. For more information about the required access for other resources types, see [Tagging permissions](/docs/resources?topic=resources-access#tagging-permissions).

## Where can I find my SoftLayer resources in the {{site.data.keyword.Bluemix_notm}} console?
{: #slitems}
{: faq}

The formerly named SoftLayer is now called {{site.data.keyword.Bluemix_notm}} classic infrastructure. To view your devices, storage, network, security, and services, you can use any of the following options:

* Click the **Menu icon** ![Menu icon](../icons/icon_hamburger.svg) > **Classic Infrastructure**.
* Click the **Menu icon** ![Menu icon](../icons/icon_hamburger.svg) > **Resource List**. 
* Click any of the links that are listed in the Classic infrastructure widget on your dashboard. Go to **Menu icon** ![Menu icon](../icons/icon_hamburger.svg) > **Dashboard**.

For more information, see [Transitioning to the {{site.data.keyword.Bluemix_notm}} experience](/docs/overview?topic=overview-ui#redirect-cloud).
