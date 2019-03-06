---
title: Creating Launches
seo-title: Creating Launches
description: Create a launch to enable the updating of a new version of existing web pages for future activation. When you create a Launch, you specify a title and the source page.
seo-description: Create a launch to enable the updating of a new version of existing web pages for future activation. When you create a Launch, you specify a title and the source page.
uuid: 1e52b623-fe95-4886-8b4b-59048fa8ab22
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 47aee77f-fe1c-4650-aea9-ead61b56ab35
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
index: y
internal: n
snippet: y
---

# Creating Launches{#creating-launches}

<!--
Comment Type: remark
Last Modified By: unknown unknown (ims-author-57F1056A4CD116590A746C15@AdobeID)
Last Modified Date: 2017-12-06T04:44:08.035-0500
<p>6.2</p>
<ul>
<li>create from multiple roots</li>
<li>clone a launch from the console
<ul>
<li>os there any connection between the clone and the original launch?<br /> </li>
</ul> </li>
</ul>
-->

Create a launch to enable the updating of a new version of existing web pages for future activation. When you create a Launch, you specify a title and the source page:

* The title appears in the [Sidekick](../../../sites/classic-ui-authoring/using/author-env-basic-handling.md#sidekick), from where authors can access them to work on them.
* The child pages of the source page are included in the launch by default. You can use only the source page if desired. 
* By default, [Live Copy](../../../sites/administering/using/msm.md) automatically updates the launch pages as the source pages change. You can specify that a static copy is created to prevent automatic changes.

Optionally, you can specify the **Launch Date** (and time) to define when the launch pages are to be promoted and activated. However the **Launch Date** only operates in combination with the **Production Ready** flag (see [Editing a Launch Configuration](../../../sites/classic-ui-authoring/using/classic-launches-editing.md#editingalaunchconfiguration)); for the actions to actually occur automatically, both must be set.

## Creating a Launch {#creating-a-launch}

The following procedure creates a launch.

1. Open the Website administration page ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin)). 
1. Click **New...** then **New Launch...**.
1. In the **Create Launch** dialog, specify values for the following properties:

    * **Launch Title**: The name of the Launch. The name should be meaningful for authors.
    * **Source Page**: The path to the page for which to create the launch. By default, all child pages are included.
    * **Exclude Sub Pages**: Select this option to create the launch only for the source page and not the child pages. By default, this option is not selected.
    * **Keep In Sync**: Select this option to automatically update the content of launch pages when the source pages change. This is achieved by making the launch a [live copy](../../../sites/administering/using/msm.md).
    
    * **Launch Date**: The date and time when the launch copy is to be activated (dependent on the **Production Ready** flag; see [Launches - the Order of Events](../../../sites/authoring/using/launches.md#launches-the-order-of-events)).

   ![](assets/chlimage_1-104.png)

1. Click **Create**.

## Deleting a Launch {#deleting-a-launch}

You can also delete a launch.

1. In the [launches console](../../../sites/classic-ui-authoring/using/classic-launches.md), select the required launch.
1. Click **Delete** - confirmation is required:

   ![](assets/chlimage_1-105.png)

   >[!CAUTION]
   >
   >When deleting nested launches you should delete lower levels first.
