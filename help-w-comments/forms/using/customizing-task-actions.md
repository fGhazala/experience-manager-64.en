---
title: Customizing Task Actions
seo-title: Customizing Task Actions
description: You can customize appearance of the task actions, use only images for actions, and customize the images used in route actions.
seo-description: You can customize appearance of the task actions, use only images for actions, and customize the images used in route actions.
uuid: 60b68f32-cbcf-47be-ac1f-263e34d9ad8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 4fbd6cb4-b4a7-4afc-a78a-341f9191739c
index: y
internal: n
snippet: y
---

# Customizing Task Actions{#customizing-task-actions}

AEM Forms workspace allows users to customize the task actions. Before customizing the task actions, ensure that you follow the steps listed at [Generic steps for AEM Forms workspace customization](../../forms/using/generic-steps-html-workspace-customization.md).

## Customizing text style {#customizing-text-style}

To customize the text style, add the following code snippet in the `/apps/ws/css/newStyle.css` file:

```css
/*-------- For Task Actions visible in task list task action popup ----------------------------------------------------*/
#taskarea .taskActionsPopUp{
    position:absolute;
    right: 78px;
    top: 16px;
    display: none;
}
 
#taskarea .taskActionsPopUp ul{
    list-style-type: none;
    padding: 0px;
    margin: 0px;
    border: 1px solid #B2B2B2;
    background: #1D1D1D;
    box-shadow: inset 0px 0px 11px 2px #1C1C1C;
    height:34px;
}
 
#taskarea .taskActionsPopUp li{
    width: auto;
    height: 34px;
    float: left;
    border-right: 1px solid #B2B2B2;
}
 
#taskarea .taskActionsPopUp li i{
    height: 34px;
    width: 20px;
    float: left;
    cursor: pointer;
}
 
#taskarea .taskActionsPopUp li a{
    color: white;
    text-decoration: none;
    display: inline-block;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    text-align: left;
    max-width: 150px;
    margin: 8px 10px 0px 4px;
}
 
/*-------- For Task Actions visible in task Details task action popup ----------------------------------------------------*/
.task .taskActionsPopUp {
    position: absolute;
    border: 1px solid #1D1D1D;
    z-index: 110;
    right: 5px;
    top : 35px;
    background: #2f2f2f;
    display:none;
}
 
.task .taskActionsPopUp ul{
    list-style: none outside none;
    font-size: 13px;
    width: 160px;
}
 
.task .taskActionsPopUp li{
    height: 33px;
    border-bottom: 1px solid #474747;
    width: 20px
}
 
.task .taskActionsPopUp ul a{
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    color: white;
    text-decoration: none;
    height: 26px;
    width: 133px;
    padding: 7px 0px 0px 27px;
    display: block;
    text-align: left;
    cursor: pointer;
    border-bottom: 1px solid #474747;
}
```

## Customizing images {#customizing-images}

To customize the images, add the following code snippet in the `/apps/ws/css/newStyle.css` file. The following code snippet customizes image for the *lock* action:

```css
#taskarea .taskActionsPopUp .lock, .task .taskActionsPopUp .lock{
    background: url(../images/icons.png) no-repeat -265px -6px;
}
```

>[!NOTE]
>
>Add separate styles to display different images or images of different resolution for the Task list and Task details actions. For example to change the 'lock' action:

```css
#taskarea .taskActionsPopUp .lock{
    background: url(../images/icons1.png) no-repeat -265px -6px;
}
.task .taskActionsPopUp .lock{
    background: url(../images/icons2.png) no-repeat -265px -6px;
}
```

## Showing only images for actions {#showing-only-images-for-actions}

To show only images for actions, customize the images used in route actions. For detailed information, see [Images for Route Actions](../../forms/using/images-route-actions.md).

### Task List task action&nbsp;pop-up menu {#task-list-task-action-nbsp-pop-up-menu}

1. You require development package to customize items of the AEM Forms workspace Task list task action pop-up menu. For detailed information about creating development package, see [Building AEM Forms workspace code.](../../forms/using/introduction-customizing-html-workspace.md#main-pars-heading-3)

   [](../../forms/using/introduction-customizing-html-workspace.md#main-pars-heading-3)

1. Copy /libs/ws/js/runtime/templates/task.html to `/apps/ws/js/runtime/templates/task.html`replace the following code snippet:

   ```
   // Orignal code
   <div class="taskActionsPopUp">
           <!--START_TASKACTIONS-->
           <ul>
               <li class="arrow"></li>
               <%if(!isMustOpenToComplete && window.lcWorkspace != undefined && window.lcWorkspace.currentUser != undefined && window.lcWorkspace.currentUser.properties != undefined && window.lcWorkspace.currentUser.properties['/client/routes/formViewOnly'] == 'false'){%>
               <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
               <%}%>
               <%for(var i = 0; i<availableCommands.taskACLCommands.length; i++){%>
               <li class="<%= availableCommands.taskACLCommands[i]%>" alt="<%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.tooltip')%>" value="<%= availableCommands.taskACLCommands[i]%>" data-action="taskACL"><%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.value')%></a>
               </li>
               <%}%>
               <%for(var i = 0; i<availableCommands.otherCommands.length; i++){%>
               <li class="<%= availableCommands.otherCommands[i]%>" alt="<%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.tooltip')%>" value="<%= availableCommands.otherCommands[i]%>" data-action="other"><%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.value')%></a>
               </li>
               <%}%>
           </ul>
           <!--END_TASKACTIONS-->
           <%}%>
       </div>
    
   ```

   ```
   //New code
    
   <div class="taskActionsPopUp">
           <!--START_TASKACTIONS-->
           <ul>
               <li class="arrow"></li>
               <%if(!isMustOpenToComplete && window.lcWorkspace != undefined && window.lcWorkspace.currentUser != undefined && window.lcWorkspace.currentUser.properties != undefined && window.lcWorkspace.currentUser.properties['/client/routes/formViewOnly'] == 'false'){%>
               <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"></a>
               </li>
               <%}%>
               <%}%>
               <%}%>
               <%for(var i = 0; i<availableCommands.taskACLCommands.length; i++){%>
               <li class="<%= availableCommands.taskACLCommands[i]%>" alt="<%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.tooltip')%>" value="<%= availableCommands.taskACLCommands[i]%>" data-action="taskACL"></a>
               </li>
               <%}%>
               <%for(var i = 0; i<availableCommands.otherCommands.length; i++){%>
               <li class="<%= availableCommands.otherCommands[i]%>" alt="<%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.tooltip')%>" value="<%= availableCommands.otherCommands[i]%>" data-action="other"></a>
               </li>
               <%}%>
           </ul>
           <!--END_TASKACTIONS-->
           <%}%>
       </div>
   ```

1. Remove the fixed width assigned to an anchor tag from the `/apps/ws/css/newStyle.css` file:

   ```css
   .task .taskActionsPopUp ul{
       list-style: none outside none;
       font-size: 13px;
       width: 160px;
   }
    
   To
   .task .taskActionsPopUp ul{
       list-style: none outside none;
       font-size: 13px;
   }
    
   AND
    
   .task .taskActionsPopUp ul a{
       white-space: nowrap;
       overflow: hidden;
       text-overflow: ellipsis;
       color: white;
       text-decoration: none;
       height: 26px;
       width: 133px;
       padding: 7px 0px 0px 27px;
       display: block;
       text-align: left;
       cursor: pointer;
       border-bottom: 1px solid #474747;
   }
    
   To
    
   .task .taskActionsPopUp ul a{
       white-space: nowrap;
       overflow: hidden;
       text-overflow: ellipsis;
       color: white;
       text-decoration: none;
       height: 26px;
       width: 0px;
       padding: 7px 0px 0px 27px;
       display: block;
       text-align: left;
       cursor: pointer;
       border-bottom: 1px solid #474747;
   }
   ```

### Task Details task action pop-up menu {#task-details-task-action-pop-up-menu}

Perform the following steps to customize Details task actions pop-up menu:

* Copy the /libs/ws/js/runtime/templates/taskdetails.html file to the `/apps/ws/js/runtime/templates/` folder:
* Encapsulate icon tag inside the anchor tag instead of text. For example, the *new code *listed below encapsulates the icon tag inside the anchor tag:

```
// Original code
<div class="taskActionsPopUp">
        <!--START_ACTIONBUTTONGROUP-->
        <ul>
            <li class="leftArrow"><a href="javascript:void(0);"><</a></li>
             
            <% if (isOwner && showDirectActions) { %>
                <% if (routeList === null) {%>
                    <li class="routeAction">
                        <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
                    </li>
                <% } else { %>
                    <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                        <li class="routeAction">
                            <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                        </li>
                    <%}%>
                <%}%>
             <%}%>
              
            <% if (isOwner || (showACLActions && availableCommands.taskACLCommands !== null && availableCommands.taskACLCommands !== undefined && availableCommands.taskACLCommands.length > 0) ||  availableCommands.otherCommands.length > 2) { %>
                <%for (var i = 0; showACLActions && i < availableCommands.taskACLCommands.length; i++) {%>
                    <li title="<%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.tooltip')%>">
                        <i class="<%= availableCommands.taskACLCommands[i]%>" value="<%= availableCommands.taskACLCommands[i]%>" data-action="taskACL"/>
                        <a href="javascript:void(0);" value="<%= availableCommands.taskACLCommands[i]%>" data-action="taskACL"><%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.value')%></a>
                    </li>
                <%}%>
                 
                <%for (var i = 0; i < availableCommands.otherCommands.length; i++) {%>
                    <li title="<%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.tooltip')%>">
                        <i class="<%= availableCommands.otherCommands[i]%>" value="<%= availableCommands.otherCommands[i]%>" data-action="other"/>
                        <a href="javascript:void(0);" value="<%= availableCommands.otherCommands[i]%>" data-action="other"><%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.value')%></a>
                    </li>
                <%}%>
            <%}%>
             
            <li class="rightArrow"><a href="javascript:void(0);">></a></li>
        </ul>
        <!--END_ACTIONBUTTONGROUP-->
    </div>

```

```
//New code
 
<div class="taskActionsPopUp">
        <!--START_ACTIONBUTTONGROUP-->
        <ul>
            <li class="leftArrow"><a href="javascript:void(0);"><</a></li>
             
            <% if (isOwner && showDirectActions) { %>
                <% if (routeList === null) {%>
                    <li class="routeAction">
                        <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
                    </li>
                <% } else { %>
                    <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                        <li class="routeAction">
                            <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                        </li>
                    <%}%>
                <%}%>
             <%}%>
              
            <% if (isOwner || (showACLActions && availableCommands.taskACLCommands !== null && availableCommands.taskACLCommands !== undefined && availableCommands.taskACLCommands.length > 0) ||  availableCommands.otherCommands.length > 2) { %>
                <%for (var i = 0; showACLActions && i < availableCommands.taskACLCommands.length; i++) {%>
                    <li title="<%= $.t('taskaction.taskaclcommand.'+availableCommands.taskACLCommands[i]+'.tooltip')%>">
                        <a href="javascript:void(0);" value="<%= availableCommands.taskACLCommands[i]%>" data-action="taskACL">
                            <i class="<%= availableCommands.taskACLCommands[i]%>" value="<%= availableCommands.taskACLCommands[i]%>" data-action="taskACL"/>
                        </a>
                    </li>
                <%}%>
                 
                <%for (var i = 0; i < availableCommands.otherCommands.length; i++) {%>
                    <li title="<%= $.t('taskaction.othercommand.'+availableCommands.otherCommands[i]+'.tooltip')%>">
                        <a href="javascript:void(0);" value="<%= availableCommands.otherCommands[i]%>" data-action="other">
                            <i class="<%= availableCommands.otherCommands[i]%>" value="<%= availableCommands.otherCommands[i]%>" data-action="other"/>
                        </a>
                    </li>
                <%}%>
            <%}%>
             
            <li class="rightArrow"><a href="javascript:void(0);">></a></li>
        </ul>
        <!--END_ACTIONBUTTONGROUP-->
    </div>
```

* Open the /apps/ws/js/registry.js file for editing.
* Locate the following text:  
  `text!/lc/libs/ws/js/runtime/templates/taskdetails.html`

* Replace the located text with the following text: `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`

[**Contact Support**](https://www.adobe.com/account/sign-in.supportportal.html)

<!--
<related-links>
<a href="../../forms/using/introduction-customizing-html-workspace.md">Introduction to Customizing AEM Forms workspace</a>
<a href="../../forms/using/generic-steps-html-workspace-customization.md">Generic steps for AEM Forms workspace customization</a>
<a href="../../forms/using/tasks-organizational-hierarchy-using-manager.md">Managing tasks in an organizational hierarchy using Manager View</a>
<a href="../../forms/using/integrating-correspondence-management-html-workspace.md">Integrating Correspondence Management in AEM Forms workspace</a>
<a href="../../forms/using/single-sign-timeout-handlers.md">Single Sign On and timeout handlers</a>
<a href="../../forms/using/displaying-user-avatar.md">Displaying the user avatar</a>
<a href="../../forms/using/displaying-information-task-summary-pane.md">Displaying information in the Task Summary pane</a>
<a href="../../forms/using/changing-organization-logo-branding.md">Changing the organization logo</a>
<a href="../../forms/using/changing-color-scheme-interface.md">Changing the color scheme of the interface</a>
<a href="../../forms/using/changing-font-interface.md">Changing the font on the interface</a>
<a href="../../forms/using/changing-locale-user-interface.md">Changing the locale of the user interface</a>
<a href="../../forms/using/customizing-error-dialogs.md">Customizing error dialogs</a>
<a href="../../forms/using/customizing-tabs-task.md">Customizing tabs for a task</a>
<a href="../../forms/using/customizing-task-actions.md">Customizing Task Actions</a>
<a href="../../forms/using/customizing-listing-process-instances.md">Customizing the listing of process instances</a>
<a href="../../forms/using/customizing-task-details-page.md">Customizing the task Details page</a>
<a href="../../forms/using/display-additional-data-in-todo-list.md">Displaying additional data in ToDo list</a>
<a href="../../forms/using/getting-task-variables-summary-url.md">Getting Task Variables in Summary URL</a>
<a href="../../forms/using/images-route-actions.md">Images for Route Actions</a>
<a href="../../forms/using/creating-new-login-screen.md">Creating a new login screen</a>
<a href="../../forms/using/minification-javascript-files.md">Minification of the JavaScript files</a>
<a href="../../forms/using/sorting-tracking-tables-add-columns.md">Sorting of Tracking tables and adding more columns</a>
<a href="../../forms/using/updating-link-help-documentation.md">Updating the link to the documentation</a>
<a href="../../forms/using/two-html-workspace-instances-one.md">Hosting two AEM Forms workspace instances on one server</a>
</related-links>
-->
