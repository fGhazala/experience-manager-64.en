---
title: Changing the locale of AEM Forms workspace user interface
seo-title: Changing the locale of AEM Forms workspace user interface
description: null
seo-description: How to modify the AEM Forms workspace to localize text, collapsed categories, queues, and processes, and the date picker on the interface.
uuid: e895795a-058c-46e6-95c9-e3ac0a1ec00e
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 1212d198-1e39-4deb-81be-1dc39af9f51e
index: y
internal: n
snippet: y
---

# Changing the locale of AEM Forms workspace user interface{#changing-the-locale-of-aem-forms-workspace-user-interface}

AEM Forms workspace provides out of the box support for English, French, German, and Japanese languages. It also provides capability to localize AEM Forms workspace user interface to any other language.

To localize AEM Forms workspace user interface to language of your choice:

* Localize text of the AEM Forms workspace.
* Localize collapsed categories, queues, and processes.
* Localize Date Picker

Before performing above steps, ensure that you follow the steps listed at [Generic steps for AEM Forms workspace customization](../../forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>To change the language of the login screen of AEM Forms workspace, see [Creating a new login screen](../../forms/using/creating-new-login-screen.md).

## Localizing text {#localizing-text}

Perform the following steps to add support for a language *New* and the browser locale code *nw*.

1. Log in to CRXDE Lite.  
   The default URL of CRXDE Lite is `http://[server]:[port]/lc/crx/de/index.jsp`.
1. Navigate to the location `apps/ws/locales` and create a new folder `nw.`
1. Copy the file `translation.json`from the location `/apps/ws/locales/en-US` to location `/apps/ws/locales/nw` .
1. Navigate to `/apps/ws/locales/nw` and open `translation.json` for editing. Make locale-specific changes to the translation.json file.

   The following examples contain the translation.json file for English and French locales of AEM Forms workspace.

   ![](assets/translation_json_in_EN.png) ![](assets/translation_json_in_FR.png)

## Localizing collapsed categories, queues, and processes {#localizing-collapsed-categories-queues-and-processes}

AEM Forms workspace uses images to display headers of categories, queues, and processes. You require development package to localize these headers. For detailed information about creating development package, see [Building AEM Forms workspace code.](../../forms/using/introduction-customizing-html-workspace.md#main-pars-heading-3)

In the following steps, it is assumed that the new localized image files are *Categories_nw.png*, *Queue_nw.png*, and *Processes_nw.png*. The recommended width of the images is 19px.

>[!NOTE]
>
>To find the browser language locale code of your browser. Open `http://[server]:[port]/lc/libs/ws/Locale.html`.

![](assets/collapsing_panels_image.png)

Perform the following steps to localize the images:

1. Using a WebDAV client, place the image files in the */apps/ws/images* folder.
1. Navigate to* /apps/ws/css*. Open *newStyle.css* for editing and add the following entries:

   ```
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
    
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
    
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Perform all the semantic changes listed in the [Workspace Customization](../../forms/using/introduction-customizing-html-workspace.md) article.
1. Navigate to the *js/runtime/utility* folder and open the* usersession.js* file for editing.
1. Locate the code listed in orignal code block and add condition *lang !== 'nw'* to the if statement:

   ```
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   
   ```

   ```
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Localizing Date Picker {#localizing-date-picker}

You require development package to localize the *datepicker *API. For detailed information about creating development package, see [Building AEM Forms workspace code](../../forms/using/introduction-customizing-html-workspace.md#main-pars-heading-3).

1. Download and extract the [jQuery UI Package](http://jqueryui.com/download/all/), navigate to *&lt;extracted jquery UI package&gt;*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Copy the jquery.ui.datepicker-nw.js file for locale code nw to apps/ws/js/libs/jqueryui and make locale specific changes to the file. 
1. Navigate to `apps/ws/js` and open the `jquery.ui.datepicker-nw.js` file for editing. 
1. In the main.js file create an alias for `jquery.ui.datepicker-nw.js.` The code to create an alias for the `jquery.ui.datepicker-nw.js` file is:

   ```
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Use alias `jqueryuidatepickernw` to include the `jquery.ui.datepicker-nw.js` file in all the files that use datepicker. The datepicker is used in the following files:

    * `js/runtime/views/outofoffice.js`
    * `js/runtime/views/searchtemplatedetails.js`

   The sample code below shows how to add the entry of jquery.ui.datepicker-nw.js:

   ```
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {

   ```

   ```
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. In all the files that use the datepicker API, change the default datepicker API settings. The datepicker API is used in the following files:

    * apps\ws\js\runtime\views\searchtemplatedetails.js
    * apps\ws\js\runtime\views\outofoffice.js

   Change the following code to add the new locale:  

   ```
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
    
   ```

   ```
   if (locale === 'ja-JP') {
       $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
       $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
       $.datepicker.setDefaults($.datepicker.regional.fr);
   } else if (locale === 'nw') {
       $.datepicker.setDefaults($.datepicker.regional.nw);
   } else {
       $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

[**Contact Support**](https://www.adobe.com/account/sign-in.supportportal.html)

>[!MORE_LIKE_THIS]
>
>* [Introduction to Customizing AEM Forms workspace](../../forms/using/introduction-customizing-html-workspace.md)
>* [Generic steps for AEM Forms workspace customization](../../forms/using/generic-steps-html-workspace-customization.md)
>* [Managing tasks in an organizational hierarchy using Manager View](../../forms/using/tasks-organizational-hierarchy-using-manager.md)
>* [Integrating Correspondence Management in AEM Forms workspace](../../forms/using/integrating-correspondence-management-html-workspace.md)
>* [Single Sign On and timeout handlers](../../forms/using/single-sign-timeout-handlers.md)
>* [Displaying the user avatar](../../forms/using/displaying-user-avatar.md)
>* [Displaying information in the Task Summary pane](../../forms/using/displaying-information-task-summary-pane.md)
>* [Changing the organization logo](../../forms/using/changing-organization-logo-branding.md)
>* [Changing the color scheme of the interface](../../forms/using/changing-color-scheme-interface.md)
>* [Changing the font on the interface](../../forms/using/changing-font-interface.md)
>* [Changing the locale of the user interface](../../forms/using/changing-locale-user-interface.md)
>* [Customizing error dialogs](../../forms/using/customizing-error-dialogs.md)
>* [Customizing tabs for a task](../../forms/using/customizing-tabs-task.md)
>* [Customizing Task Actions](../../forms/using/customizing-task-actions.md)
>* [Customizing the listing of process instances](../../forms/using/customizing-listing-process-instances.md)
>* [Customizing the task Details page](../../forms/using/customizing-task-details-page.md)
>* [Displaying additional data in ToDo list](../../forms/using/display-additional-data-in-todo-list.md)
>* [Getting Task Variables in Summary URL](../../forms/using/getting-task-variables-summary-url.md)
>* [Images for Route Actions](../../forms/using/images-route-actions.md)
>* [Creating a new login screen](../../forms/using/creating-new-login-screen.md)
>* [Minification of the JavaScript files](../../forms/using/minification-javascript-files.md)
>* [Sorting of Tracking tables and adding more columns](../../forms/using/sorting-tracking-tables-add-columns.md)
>* [Updating the link to the documentation](../../forms/using/updating-link-help-documentation.md)
>* [Hosting two AEM Forms workspace instances on one server](../../forms/using/two-html-workspace-instances-one.md)