---
title: Using Content Properties to Export Content
seo-title: Using Content Properties to Export Content
description: null
seo-description: The following page shows App Properties and Nodes.
uuid: 2b0786e0-7836-4744-9fd3-e6d22bcfbadc
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: acbffddd-e188-470f-b950-ca334cdde94f
index: y
internal: n
snippet: y
---

# Using Content Properties to Export Content{#using-content-properties-to-export-content}

>[!NOTE]
>
>Adobe recommends using the SPA Editor for projects that require single page application framework-based client-side rendering (e.g. React). [Learn more](../../sites/developing/using/spa-overview.md).

Apps are represented as *cq:Pages* in AEM.

They share the same common properties found in any *cq:Page* in addition to others shown below that represent integration supporting properties.

## App Properties {#app-properties}

The following table shows **App Properties and Nodes**.

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td><strong>PropertyName</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr> 
  <tr> 
   <td>dps-cloudConfig</td> 
   <td>String:Path</td> 
   <td><p>Path to a configured Mobile On-Demand Cloud Service. Used for AEM Mobile to Mobile On-Demand actions (API invocation)</p> <p>This association is configured via the Manage Connection tile when an author chooses a Mobile On-Demand Cloud Service to associate the app to.</p> </td> 
  </tr> 
  <tr> 
   <td>dps-exportTemplate</td> 
   <td>String:Path</td> 
   <td><p>Path to the app's export configs. The export config is a folder with 2 child ContentSync export configuration templates;</p> <p><i>dps-article</i>: ContentSync export configuration to export article content</p> <p><i>dps-HTMLResources</i>: ContentSync export configuration to export app/article shared resources</p> </td> 
  </tr> 
  <tr> 
   <td>dps-projectId</td> 
   <td>String</td> 
   <td><p>Id/URI of the Mobile On-Demand project this App is linked/bound to.</p> <p>This association is configured via the Manage Connection tile when an author chooses the project from a list of available projects for the associated Mobile On-Demand Cloud Service.</p> </td> 
  </tr> 
  <tr> 
   <td>dps-projectTitle</td> 
   <td>String</td> 
   <td>App title.</td> 
  </tr> 
  <tr> 
   <td>dps-resourceType</td> 
   <td>String</td> 
   <td>Content type.</td> 
  </tr> 
  <tr> 
   <td>dps-sharedHTMLResources-lastUploaded</td> 
   <td>Date</td> 
   <td>Date of last upload of shared resources from AEM to AEM Mobile.</td> 
  </tr> 
  <tr> 
   <td>dps-sharedHTMLResources-lastUploadedBy</td> 
   <td>String:userid</td> 
   <td>Id of the user that performed the last upload of shared resources request from AEM to AEM Mobile.</td> 
  </tr> 
  <tr> 
   <td>pge-dashboard-config</td> 
   <td>String:Path</td> 
   <td>Path to a dashboard configuration. The path can be redirected to a custom dashbaord configuration as needed.</td> 
  </tr> 
  <tr> 
   <td>sling:resourceType</td> 
   <td>String:Path</td> 
   <td><p>Path to a cq:Component that is or extends <i>mobileapps/core/components/instance.</i></p> <p>This provides the presence and rendering in the Apps Catalog.</p> </td> 
  </tr> 
 </tbody> 
</table>

You can use ***Content Properties*** to create content. See the following resources for creating and exporting articles and shared resources:

* [Content Properties](../../mobile/using/content-properties.md)
* [Creating Article Export Configuration](../../mobile/using/creating-article-export-configuration.md)
* [Creating Shared Resources Export Configuration](../../mobile/using/creating-shared-resources-export-configuration.md)
