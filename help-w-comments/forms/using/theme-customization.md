---
title: Theme Customization
seo-title: Theme Customization
description: How to customize the theme of your AEM Forms app.
seo-description: How to customize the theme of your AEM Forms app.
uuid: 4609075c-9a36-4fff-b948-706b23d6eeb9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 7a48608e-c42a-46e0-85aa-3a928ee3052d
index: y
internal: n
snippet: y
---

# Theme Customization{#theme-customization}

You can customize the HTML code and CSS file to provide a distinct organization-specific look and feel to AEM Forms app. For example, you can change the background color and height of tasks or Startpoints. The following example provides instructions to change:

* display instructions in place of the description  
* number of display routes  
* background gradient color

### Steps {#steps}

1. Open your project.

    * For iOS, open `Capture.xcodeproj` in Xcode
    * For Android, open the Android project in Eclipse. 
    * For Windows, open `MWSWindows.sln` in Visual Studio.

1. Navigate to the templates folder.

    * In Xcode, navigate to the **Capture &gt; www &gt; wsmobile &gt; js &gt; runtime &gt; templates**folder.
    * In Eclipse, navigate to the** assets &gt; www &gt; wsmobile &gt; js &gt; runtime &gt; templates**folder.
    * In Visual Studio, navigate to the **MWSWindows &gt; www &gt; wsmobile &gt; js &gt; runtime &gt; templates** folder.

1. Open the `template.html` file for editing.
1. Locate the following string:

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   Replace it with `<%`.

1. Locate the following code in the `template.html` file:

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Comment the following line and save the file.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Navigate to the css folder.

    * In Xcode, navigate to **Capture &gt; www &gt; wsmobile &gt; css**.  
    
    * In Eclipse, navigate to **assets &gt; www &gt; wsmobile &gt; css**.
    * In Visual Studio, navigate to **MWSWindows &gt; www &gt; wsmobile &gt; css**.

1. 
   Open the `_style.css` file for editing.  
1. For Background image, change `#323232` to `#fff`.
1. Save the changes and close `_style.css` file.
1. Open the AEM Forms app.

   The AEM Forms app now displays instructions instead of description.

[**Contact Support**](https://www.adobe.com/account/sign-in.supportportal.html)