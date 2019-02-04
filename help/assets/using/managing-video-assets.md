---
title: Managing Video Assets
seo-title: Managing Video Assets
description: null
seo-description: Learn how to upload, preview, annotate, and publish video assets.
uuid: 1040b6a9-2a00-41c5-af70-3715aedbfd09
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
discoiquuid: 4cce90a3-a3da-4844-aa2a-48182e283fe1
index: y
internal: n
snippet: y
---

# Managing Video Assets{#managing-video-assets}

This section describes how to manage and edit video assets.

>[!NOTE]
>
>**Are you a Dynamic Media customer?**
>
>If you are licensed to use Dynamic Media, refer to the [Dynamic Media Video documentation](../../assets/using/video.md).

## Uploading and Previewing Video Assets {#uploading-and-previewing-video-assets}

Adobe Experience Manager Assets generates previews for video assets with the extension **.mp4**. If the format of the asset is not **mp4**, install the FFmpeg pack to generate a preview. See [FFmpeg installation instructions](../../sites/authoring/using/default-components-foundation.md#video). FFmpeg creates video renditions of type **ogg** and **mp4**. You can preview these renditions in the Adobe Experience Manager Assets user interface.

1. In the Digital Assets folder (or sub-folders), navigate to the location where you want to add digital assets.
1. To upload the asset, click or tap **Create** from the toolbar and then choose **Files**. Alternatively, drop it directly in the assets area. See [Uploading assets](../../assets/using/managing-assets-touch-ui.md#uploadingassets) for details around the upload operation.
1. To preview a video in the Card view, click the **Play** button on the video asset.

   ![](assets/chlimage_1-154.png)

   You can pause or play video in the Card view only. The Play/Pause button is not available in the list view.

1. Click or tap the Edit icon on the card to preview the video in the asset details page.

   The video plays in the native video player of the browser. You can play, pause, control the volume, and zoom the video to full screen.

   ![](assets/chlimage_1-155.png)

## Configuration to upload video assets that are larger than 2 GB {#configuration-to-upload-video-assets-that-are-larger-than-gb}

By default, the AEM Assets Touch UI does not let you upload any assets that are larger than 2 GB because of a file size limit. However, you can overwrite this limit by going into CRXDE Lite and creating a node under the `/apps`directory. The node must have the same node name, directory structure, and comparable node properties of order.

>[!NOTE]
>
>The AEM Classic user interface does not have a 2 GB file size limit restriction. Also, end-to-end workflow for large video is not fully supported.

Perform the following steps to configure a higher file size limit (for example 30GB ) in the */apps* directory:

1. In AEM, tap **Tools **&gt; **General** &gt; **CRXDE Lite**.
1. In the CRXDE Lite page, in the directory window on the left, navigate to */libs/dam/gui/content/assets/jcr:content/actions/selection/create/items/fileupload*.

   You may need to touch the **&gt;&gt;** icon to see the directory window.

1. From the toolbar, tap the **Overlay Node…** button. Alternatively, select **Overlay Node...** from the context menu.

   <!--
   Comment Type: remark
   Last Modified By: unknown unknown (rbrough@adobe.com)
   Last Modified Date: 2017-11-30T05:30:03.345-0500
   <p>Are each one of these (gui, content, assets, _jcr_content, body, etc.) as seen in the path below supposed to be created as a node? Or are some of them created as folders or components or something else?</p>
   <p>/gui/content/assets/_jcr_content/body/assetscontent/header/items/items/fileupload</p>
   <p> </p>
   <p>Can you send a screenshot of what the CRXDE Lite page is supposed to look like (with the directory structure on the left side and the Properties tab showing for fileupload) when they've entered the full node path and the property. Then I can better understand what is going on and update the steps.</p>
   -->

1. In the **Overlay Node** dialog, tap **OK**.

   ![](assets/chlimage_1-156.png)

1. Refresh the browser. The overlay node */jcr_root/apps/dam/gui/content/assets/jcr:content/actions/selection/create/items/fileupload* is already selected in the directory window on the left.
1. In the **Properties** tab, enter the appropriate value in bytes to increase the size limit to the desired size. For example, enter the following value to increase the size limit to 30GB:

   `{sizeLimit : "32212254720"}`

1. From the toolbar, touch **Save All**.
1. In AEM, tap **Tools** &gt; **Operations** &gt; **Web Console**.
1. On the Adobe Experience Manager Web Console Bundles page, under the Name column of the table, locate and tap **Adobe Granite Workflow External Process Job Handler**.
1. In the Adobe Granite Workflow External Process Job Handler page, set the seconds for both **Default Timeout** and **Max Timeout** fields to `18000` (5 hours).
1. Tap **Save**.
1. In AEM, tap **Tools** &gt; **Workflow** &gt; **Models**.
1. On the Workflow Models page, select **Dynamic Media Encode Video**, then tap **Edit**.
1. On the workflow page, double-tap the **Dynamic Media Video Service Process** component.
1. In the Step Properties dialog box, under the **Common** tab, expand **Advanced Settings**.
1. In the Timeout field, specify a value of `18000`, then tap **OK** to return to the **Dynamic Media Encode Video** workflow page.
1. Near the top of the page, below the Dynamic Media Encode Video page title, tap **Save**.

## Publishing video assets {#publishing-video-assets}

After your video assets are published, they are available to you for including in a web page by way of a URL or embedding on a web page.

See [Publishing Assets](../../assets/using/publishing-dynamicmedia-assets.md).

## Annotating video assets {#annotating-video-assets}

1. From the Assets console, click or tap the Edit icon on the asset card to display the asset details page.
1. Click or tap the Preview icon to play the video. 
1. To annotate the video, click the **Annotate** button. An annotation is added at the particular timepoint (frame) in the video.

   While annotating, you can draw on the canvas and include a comment with the drawing. Comments are automatically saved in Adobe Experience Manager Assets.

   ![](assets/chlimage_1-157.png)

   To exit the annotation wizard, click **Close**.

1. To jump to a specific point in the video, specify the time in seconds in the **text** field and click **Jump**. For example, to skip the first 10 seconds of video, enter **20** in the **text** field.

   ![](assets/chlimage_1-158.png)

1. Cick an annotation to view it in the timeline. Click **Delete** to delete the annotation from the timeline.

   ![](assets/chlimage_1-159.png)
