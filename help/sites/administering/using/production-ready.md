---
title: Running AEM in Production Ready Mode
seo-title: Running AEM in Production Ready Mode
description: null
seo-description: Learn how to run AEM in Production Ready Mode.
uuid: 52fc30bb-c90c-40ab-917d-7efb957813f2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 918d82f4-3dd6-47d5-aa07-e3be20ff5498
index: y
internal: n
snippet: y
---

# Running AEM in Production Ready Mode{#running-aem-in-production-ready-mode}

With AEM 6.1, Adobe introduces the new `"nosamplecontent"` runmode aimed at automating the steps required to prepare an AEM instance for deployment in a production environment.

The new runmode will not only automatically configure the instance to adhere to the security best practices described in the security checklist, but will also remove all the sample geometrixx applications and configurations in the process.

>[!NOTE]
>
>Since, due to practical reasons, the AEM Production Ready Mode will only cover a majority of tasks needed to secure an instance, it is highly recommended you consult the [Security Checklist](../../../sites/administering/using/security-checklist.md) before going live with your production environment.
>
>Also, note that running AEM in Production Ready Mode will effectively disable access to CRXDE Lite. If you need it for debugging purposes, see [Enabling CRXDE Lite in AEM](../../../sites/administering/using/enabling-crxde-lite.md).

![](assets/chlimage_1-95.png)

In order to run AEM in production ready mode all you need to do is add the `nosamplecontent` via the `-r` runmode switch to your existing startup arguments:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

For example, you can use the production ready to launch an author instance with MongoDB persistence like this:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

### Changes part of the Production Ready Mode {#changes-part-of-the-production-ready-mode}

More specifically, the following configuration changes will be performed when AEM is ran in production ready mode:

1. The **CRXDE Support bundle** ( `com.adobe.granite.crxde-support`) is disabled by default in production ready mode. It can be installed at any time from the Adobe public Maven repository. Version 3.0.0 is required for AEM 6.1.

1. The **Apache Sling Simple WebDAV Access to repositories** ( `org.apache.sling.jcr.webdav`) bundle will only be available on **author** instances.

1. Newly created users will be required to change the password on the first login. This does not apply to the admin user.  
1. **Generate debug info** is disabled for the **Apache Java Script Handler**.

1. **Mapped content** and **Generate debug info** are disabled for the **Apache Sling JSP Script Handler**.

1. The **Day CQ WCM Filter** is set to `edit` on **author** and `disabled` on **publish** instances.

1. **The Adobe Granite HTML Library Manager** is configured with the following settings:

    1. **Minify:** `enabled`
    
    1. **Debug:** `disabled`
    
    1. **Gzip:** `enabled`
    
    1. **Timing:** `disabled`

1. The **Apache Sling GET Servlet** is set to support secure configurations by default, as follows:

| **Configuration** |**Author** |**Publish** |
|---|---|---|
| TXT rendition |disabled |disabled |
| HTML rendition |disabled |disabled |
| JSON rendition |enabled |enabled |
| XML rendition |disabled |disabled |
| json.maximumresults |1000 |100 |
| Auto Index |disabled |disabled |
