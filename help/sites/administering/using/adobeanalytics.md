---
title: Integrating with Adobe Analytics
seo-title: Integrating with Adobe Analytics
description: null
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 10f48b79-8381-45ca-a832-f9cd05ce638f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: b2b0b653-9eec-451a-973c-fdf7f3a574bf
index: y
internal: n
snippet: y
---

# Integrating with Adobe Analytics{#integrating-with-adobe-analytics}

Integrating Adobe Analytics and AEM allows you to track your web page activity:

* An Adobe Analytics configuration enables AEM to authenticate with Adobe Analytics.   
* A framework identifies the data that is sent to your Adobe Analytics report suite.

The data includes page and user data; for example:

* data that AEM components collect
* link clicks
* video usage information  
* the number of page visits from Adobe Analytics

The following pages help you configure the integration:

* [Connecting to Adobe Analytics and Creating Frameworks](../../../sites/administering/using/adobeanalytics-connect.md)
* [Configuring Link Tracking for Adobe Analytics](../../../sites/administering/using/adobeanalytics-link.md)
* [Mapping Component Data with Adobe Analytics Properties](../../../sites/administering/using/adobeanalytics-mapping.md)
* [Configuring Video Tracking for Adobe Analytics](../../../sites/administering/using/adobeanalytics-video.md)
* [SAINT Exporter](../../../sites/administering/using/adobeanalytics-saint.md)

You can also use the [Opt-in wizard](../../../sites/administering/using/opt-in.md) to easily perform the integration.

>[!NOTE]
>
>See also the how-to article: [Integrating AEM with Adobe Target and Adobe Analytics using DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

### Further Information {#further-information}

See:

* [Extending the Adobe Analytics Integration](../../../sites/developing/using/extending-analytics.md) for information about developing components that collect user data and customizing the Adobe Analytics framework.
* The knowledge base article, [Adobe Analytics integration - troubleshooting issues](http://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), for information about troubleshooting your Adobe Analytics integration.

>[!NOTE]
>
>If you are using Adobe Analytics with a custom proxy configuration, you need to [configure two OSGi bundles](../../../sites/deploying/using/configuring-osgi.md) (for example, with the Web console) required for the **Apache HTTP Client** proxy configurations. Both are required as some functionalities of AEM use the 3.x APIs, while others use the 4.x APIs. Configure:
>
>* **Day Commons HTTP Client 3.1** to configure the 3.x API;  
>  for example, [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** to configure the 4.x API;  
>  for example, [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>
