---
title: Enhanced Smart Tags
seo-title: Enhanced Smart Tags
description: null
seo-description: null
uuid: 18e53658-5898-4b28-9620-ef3e83905d5e
contentOwner: cmajumda
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
discoiquuid: a077e42c-4cfa-4688-abb5-4d1d36f02496
index: y
internal: n
snippet: y
---

# Enhanced Smart Tags{#enhanced-smart-tags}

## Overview of Enhanced Smart Tags {#overview-of-enhanced-smart-tags}

Organizations that deal with digital assets increasingly use taxonomy-controlled vocabulary in asset metadata. Essentially, it includes a list of keywords that employees, partners, and customers commonly use to refer to and search for digital assets of a particular class. Tagging assets with taxonomy-controlled vocabulary ensures that they can be easily identified and retrieved by tag-based searches.

Compared to natural language vocabularies, tagging digital assets based on business taxonomy helps align them with a company's business and ensures that the most relevant assets appear in searches.

For example, a car manufacturer can tag car images with model names so only relevant images appear when images of various models are searched to design a promotion campaign.

For the Smart Content Service to apply the right tags, you must train it to recognize your taxonomy. To train the service, first curate a set of assets and tags that best describe these assets. Apply these tags on the assets and run a training workflow to help the service learn.

Once a tag is trained and ready, the service can now apply these tags on assets through a tagging workflow.

In the background, the Smart Content Service uses Adobe Sensei's AI framework to train its image recognition algorithm on your tag structure and business taxonomy. This content intelligence is then used to apply relevant tags on a different set of assets.

Smart Content Service is a cloud service that is hosted on Adobe I/O. To use it in Adobe Experience Manager (AEM), the system administrator must integrate your AEM instance with Adobe IO.

In summary, here are the main steps to use the Smart Content Service:

* Onboarding
* Reviewing assets and tags (taxonomy definition)
* Training the Smart Content Service
* Automatic tagging

<!--
Comment Type: annotation
Last Modified By: satyam
Last Modified Date: 2018-03-13T01:28:24.890-0400
[Satya Deep] - Typo | Custom | Custom Tags
-->

<!--
Comment Type: annotation
Last Modified By: satyam
Last Modified Date: 2018-03-22T01:52:38.052-0400
[Satya Deep] - "add you as a user." This doesn't make sense. Probably it can be removed.
-->

![](assets/Flowchart.gif) 

## Prerequisites {#prerequisites}

## Onboarding {#onboarding}

The Smart Content Service is available for purchase as an add-on to AEM 6.4. After you purchase, an email is sent to the administrator of your organization with a link to Adobe IO.

The administrator can follow the link to integrate the Smart Content Service with AEM. To integrate the service with AEM Assets, see [Configure Smart Tags](../../assets/using/config-smart-tagging.md).

The onboarding process is complete when the administrator configures the service and adds users in AEM.

>[!NOTE]
>
>The Smart Content Service is supported on AEM 6.4 only. If you are running a previous version of AEM and require automatic tagging service for your assets, see [Smart Tags](/content/help/en/experience-manager/6-3/assets/using/touch-ui-smart-tags).

## Reviewing assets and tags {#reviewing-assets-and-tags}

After you are onboarded, the first thing you want to do is identify a set of tags that best describe these images in the context of your business.

Next, review images to identify a set of images that best represent your product for a particular business requirement. Ensure that the assets in your curated set conform to [Smart Content Service training guidelines](../../assets/using/smart-tags-training-guidelines.md).

Add the assets to a folder and apply the tags to each asset from the properties page. Then, run the training workflow on this folder. The curated set of assets enables the Smart Content Service to effectively train more assets using your taxonomy definitions.

>[!NOTE]
>
>1. Training is an irrevocable process. Adobe recommends that you review the tags in the curated set of assets well before training the Smart Content Service on the tags.
>1. Please do read [Smart Content Service training guidelines](../../assets/using/smart-tags-training-guidelines.md) before starting training for any tag.
>1. When you train the Smart Content Service for the first time, Adobe recommends that you train it on at least two distinct tags.
>

## Training the Smart Content Service {#training-the-smart-content-service}

For the Smart Content Service to recognize your business taxonomy, run it on a set of assets that already include tags that are relevant to your business. After training, the service can apply the same taxonomy on a similar set of assets.

You can train the service multiple times to improve its ability to apply relevant tags. After each training cycle, run a tagging workflow and check whether your assets are tagged appropriately.

You can train the Smart Content Service periodically or on requirement basis.

<!--
Comment Type: annotation
Last Modified By: dee
Last Modified Date: 2018-03-14T04:24:21.407-0400
[dee] 1. we should mention somewhere about defining tags taxonomy. 2. should we mention algorithm here ? 3. add note for first time training should be at least on two set of assets i.e. two different tags for successful running training to complete.
-->

>[!NOTE]
>
>The training workflow runs on folders only.

### Periodic training {#periodic-training}

You can enable the Smart Content Service to train periodically on the assets and associated tags within a folder. Open the properties page of your asset folder, select **Enable Smart Tags** under the **Details** tab, and save the changes.

![](assets/enable_smart_tags.png)

Once this option is selected for a folder, AEM runs a training workflow automatically to train the Smart Content Service on the folder assets and their tags. By default, the training workflow runs on a weekly basis at 12:30 AM on Saturdays.

### On-demand training {#on-demand-training}

You can train the Smart Content Service whenever required from the Workflow console.

1. Tap/click the AEM logo, and go to **Tools** &gt; **Workflow** &gt; **Models**.
1. From the **Workflow Models** page, select the **Smart Tags Training** workflow and then tap/click **Start Workflow** from the toolbar.
1. In the **Run Workflow** dialog, browse to the payload folder that includes the tagged assets for training the service.
1. Specify a title for the workflow and a add a comment. Then, tap/click **Run**. The assets and tags are submitted for training.

   ![](assets/workflow_dialog.png)

>[!NOTE]
>
>Once the assets in a folder are processed for training, only the modified assets are processed in subsequent training cycles.

### Viewing training reports {#viewing-training-reports}

To check whether the Smart Content Service is trained on your tags in the training set of assets, review the training workflow report from the Reports console.

<!--
Comment Type: annotation
Last Modified By: sneh
Last Modified Date: 2018-03-14T04:23:16.683-0400
Do we want to do away with the word algorithm or is it ok?
-->

1. Tap/click the AEM logo, and go to **Tools** &gt; **Assets** &gt; **Reports**.
1. In the **Asset Reports** page, tap/click **Create**.
1. Select the **Smart Tags Training** report, and then tap/click **Next** from the toolbar.
1. Specify a title and description for the report. Under **Schedule Report**, leave the **Now** option selected. If you want to schedule the report for later, select **Later** and specify a date and time. Then, tap/click **Create** from the toolbar.
1. In the **Asset Reports** page, select the report you generated. To view the report, tap/click the **View** icon from the toolbar.
1. Review the details of the report.

   The report displays the training status for the tags you trained. The green color in the **Training Status** column indicates that the Smart Content Service is trained for the tag. Yellow color indicates that the service is not completely trained for a particular tag. In this case, add more images with the particular tag and run the training workflow to train the service completely on the tag.

   If you do not see your tags in this report, run the training workflow again for these tags.

1. To download the report, select it from the list, and tap/click the **Download** icon from the toolbar. The report downloads as an Excel file.

## Tagging assets automatically {#tagging-assets-automatically}

After you have trained the Smart Content Service, you can trigger the tagging workflow to automatically apply appropriate tags on a different set of similar assets.

You can run the tagging workflow periodically or whenever required.

>[!NOTE]
>
>The tagging workflow runs on both assets and folders.

### Periodic tagging {#periodic-tagging}

You can enable the Smart Content Service to periodically tag assets within a folder. Open the properties page of your asset folder, select **Enable Smart Tags** under the **Details** tab, and save the changes.

Once this option is selected for a folder, the Smart Content Service automatically tags the assets within the folder. By default, the the tagging workflow runs every day at 12:00 AM.

<!--
Comment Type: annotation
Last Modified By: asgupta
Last Modified Date: 2018-07-05T10:35:28.739-0400
Which time zone? Distributed server.
-->

### On-demand tagging {#on-demand-tagging}

You can trigger the tagging workflow from the following to instantly tag your assets:

* Workflow console
* Timeline

>[!NOTE]
>
>If you run the tagging workflow from the timeline, you can apply tags on a maximum of 15 assets at a time.

#### Tagging assets from the Workflow console {#tagging-assets-from-the-workflow-console}

1. Tap/click the AEM logo, and go to **Tools** &gt; **Workflow** &gt; **Models**.
1. From the **Workflow Models** page, select the **DAM Smart Tags Assets** workflow and then tap/click **Start Workflow** from the toolbar.

   ![](assets/dam_smart_tag_workflow.png)

1. In the **Run Workflow** dialog, browse to the payload folder containing assets on which you want to apply your tags automatically.
1. Specify a title for the workflow and an optional comment. Then, tap/click **Run**.

   ![](assets/tagging_dialog.png)

   Navigate to the asset folder and review the tags to verify whether the Smart Content Service tagged your assets properly. For details, see [Managing Smart Tags](../../assets/using/managing-smart-tags.md).

#### Tagging assets from the timeline {#tagging-assets-from-the-timeline}

1. From the Assets user interface, select the folder containing assets or specific assets to which you want to apply smart tags.
1. Tap/click the GlobalNav icon and open the timeline.
1. Tap/click the arrow at the bottom, and then tap/click **Start Workflow**.

   ![](assets/start_workflow.png)

1. Select the **DAM Smart Tag Assets** workflow, and specify a title for the workflow.
1. Tap/click **Start**. The workflow applies your tags on assets. Navigate to the asset folder and review the tags to verify whether the Smart Content Service tagged your assets properly. For details, see [Managing Smart Tags](../../assets/using/managing-smart-tags.md).

>[!NOTE]
>
>In the subsequent tagging cycles, only the modified assets are tagged again with newly-trained tags.
>
>However, even unaltered assets are tagged if the gap between the last and current tagging cycles for the tagging workflow exceeds 24 hours.
>
>For periodic tagging workflows, unaltered assets are tagged when the gap exceeds 6 months.
