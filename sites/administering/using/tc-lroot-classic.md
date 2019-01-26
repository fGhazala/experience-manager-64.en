---
title: Creating a Language Root Using the Classic UI
seo-title: Creating a Language Root Using the Classic UI
description: null
seo-description: Learn how to create a language root using the Classic UI.
uuid: 62bc67eb-6af9-4f7d-89e8-05e6d1838670
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 8dee8b57-c1fd-4278-a03e-904846b73439
isreadyforlocalization: false
index: y
internal: n
snippet: y
---

# Creating a Language Root Using the Classic UI{#creating-a-language-root-using-the-classic-ui}

The following procedure uses the classic UI to create a language root of a site. For more information, see [Creating a Language Root](../../administering/using/tc-prep.md#main-pars-title).

1. In the Websites console, in the Websites tree, select the root page of the site. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Add a new child page that represents the language version of the site:

    1. Click New &gt; New Page.
    1. In the dialog, specify the Title and the Name. The Name needs to be in the format of `<language-code>` or `<language-code>_<country-code>`, for example en, en_US, en_us, en_GB, en_gb.

        * The supported language code is lower-case, two-letter code as defined by ISO-639-1
        * The supported country code is lower-case or upper-case, two-letter code as defined by ISO 3166

    1. Select the Template and click Create.

   ![](assets/newpagefr.png)

1. In the Websites console, in the Websites tree, select the root page of the site.
1. In the Tools menu, select Language Copy.

   ![](assets/toolslanguagecopy.png)

   The Language Copy dialog displays a matrix of available language versions and web pages. An x in a language column means that the page is available in that language.

   ![](assets/languagecopydialog.png)

1. To copy an existing page or page tree to a language version, select the cell for that page in the language column. Click the arrow and select the type of copy to create.

   In the following example, the equipment/sunglasses/irian page is being copied to the French language version.

   ![](assets/languagecopydilogdropdown.png) 

   | Type of language copy |Description |
   |---|---|
   | auto |Uses the behavior from parent pages |
   | ignore |Does not create a copy of this page and its children |
   | <language>+ (e.g. French+) |Copies the page and all its children from that language |
   | <language> (e.g. French) |Copies only the page from that language |

1. Click OK to close the dialog.
1. In the next dialog, click Yes to confirm the copy.
