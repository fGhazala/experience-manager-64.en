---
title: Configure AEM forms to prefetchdomain information
seo-title: Configure AEM forms to prefetchdomain information
description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups. 
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups. 
uuid: a29bb752-0aaf-4ae3-978f-8aa714955be5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: eb66bd8a-9d1d-4fbd-902a-14f99c323447
index: y
internal: n
snippet: y
---

# Configure AEM forms to prefetchdomain information{#configure-aem-forms-to-prefetchdomain-information}

<!--
Comment Type: remark
Last Modified By:
Last Modified Date:
<p>Bugs 2295870, 2380230:</p>
-->

Users may experience a slower response time if they belong to many groups (for example, 500 or more) or if the groups are nested deeply (for example, 30 levels). If you are experiencing this problem, you can configure AEM forms to prefetch information from certain domains.

1. In administration console, click Settings &gt; User Management &gt; Configuration &gt; Import And Export Configuration Files.
1. To export the current configuration setting to a file, click Export and save the configuration file in another location.
1. Add the following node (marked in bold):

   ```as3
    <node name="UM"> 
    <map/>  
    <node name="PrincipalCache"> 
        <map> 
            <entry key="principalCacheSize" value="1000"/> 
            <entry key="principalCacheBatchFetchSize" value="10"/> 
            <entry key="rebuildCacheAfterSync" value="true /> 
            <entry key="enableFullPrefetch" value="false"/> 
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/> 
        <map> 
    </node> 
    <node name="APSAuditService">
   ```

   In this example, multiple domains are configured for prefetch. The domain names are separated by a "/". This is shown in the example above with *Domain_Name1*, *Domain_Name2*, and *Domain_Name3*.

1. To import the updated file, in User Management, click Configuration &gt; Import And Export Configuration Files.
1. Click Browse to find the file, click Import, and then click OK.
