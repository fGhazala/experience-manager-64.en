---
title: Coding Guidelines
seo-title: Coding Guidelines
description: null
seo-description: Communities developer guidelines, tips, and tricks
uuid: b1b1d3be-bb36-475f-b8dd-b3c0b0e82492
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 51cae6fa-73e3-4e1d-ab91-3bd76745ad89
index: y
internal: n
snippet: y
---

# Coding Guidelines{#coding-guidelines}

## Guidelines, Tips and Tricks {#guidelines-tips-and-tricks}

Working with AEM Communities has evolved from being heavily dependant on Java Server Pages to flexibility in the choice of templating scripting languages where business logic, style, and page content are distinct from one another.

Further flexibility in working with user generated content (UGC) is through the SocialResourceProvider API, which eliminates the need for awareness of which [SRP](../../communities/using/srp.md) option was chosen for the deployment.

Following are various coding guidelines and best practices for AEM Communities developers :

### Code {#code}

* [Accessing UGC with SRP](../../communities/using/accessing-ugc-with-srp.md) - how to avoid writing an application that only works when UGC is stored in JCR (JSRP).
* [SocialUtils Refactoring](../../communities/using/socialutils.md) - utility methods for SRP that replace SocialUtils.
* [Naming Conventions](../../communities/using/naming-conventions.md) - naming conventions for custom Java classes.

### Scripts {#scripts}

* [Sideloading Communities Components](../../communities/using/sideloading.md) - how to dynamically add a component after the page loads.
* [Rich Text Editor Essentials](../../communities/using/rte.md) - how to customize the rich text UI provided to members for posting content.

### IDE {#ide}

* [Using Maven for Communities](../../communities/using/maven.md) - how to include the Communities API jar.
* [SocialUtils Refactoring](../../communities/using/socialutils.md) - utility methods for SRP that replace SocialUtils.
