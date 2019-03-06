---
title: Rich Text Editor Essentials
seo-title: Rich Text Editor Essentials
description: Rich text Editor feature overview
seo-description: Rich text Editor feature overview
uuid: 7b7628d2-e7b1-4a4a-aacc-d62f6fcf45f4
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c789db84-23cf-4328-b401-0fe6ac1e0252
index: y
internal: n
snippet: y
---

# Rich Text Editor Essentials{#rich-text-editor-essentials}

## Overview {#overview}

A Rich Text Editor (RTE) provides the ability to enter text with markup.

For Communities components, while similar to the [rich text editor in the author environment](../../sites/authoring/using/rich-text-editor.md), it affects text entered in the publish environment.

![](assets/chlimage_1-423.png) 

## Enabling Rich Text Editor {#enabling-rich-text-editor}

Communities components that allow user generated content (UGC) can be enabled to allow RTE. Depending on whether the component was added to a page or included within a [function](../../communities/using/functions.md), RTE may or may not be enabled by default.

If not enabled, simply enter [author edit mode](../../communities/using/sites-console.md#authoringsitecontent), select the component for edit, and select the `Rich Text Editor` checkbox.

RTE is available for the following Communities components:

* [blog](../../communities/using/blog-feature.md)
* [calendar](../../communities/using/calendar.md)
* [comments](../../communities/using/comments.md)
* [filelibrary](../../communities/using/file-library.md)
* [forum](../../communities/using/forum.md)
* [messaging](../../communities/using/configure-messaging.md)
* [QnA](../../communities/using/working-with-qna.md)
* [reviews](../../communities/using/reviews.md)

## Customization {#customization}

Customization of the rich text editor is possible as the implementation is based on [CKEditor](http://www.ckeditor.com/).

The current configuration for Communities components is in the `cq.social.  scf   clientlib`, located in the repository at

`/libs/clientlibs/social/commons/scf/ckrte.js`

Modifying the cq.social.scf clientlib is not recommended as future upgrades may override any edits.

### Example Customization : Inline Links {#example-customization-inline-links}

Due to security concerns, the hyperlink options are not included in the set of rich text icons presented to members by default. The ability for mischief is extensive when hrefs are allowed in UGC.

To add the hyperlink options to the toolbar :

* add a toolbar named " `links`"

    * `{ name: 'links', items : [ 'Link','Unlink','Anchor' ] }`

* select **Save All**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links', 
           items : [ 'Link','Unlink','Anchor' ] 
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
