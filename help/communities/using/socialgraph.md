---
title: Using Social Graph
seo-title: Using Social Graph
description: null
seo-description: Adding a Following component to a page
uuid: b4dbb6ca-c874-41f5-8acd-61e4b8fefa30
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: b3f2b513-a460-4719-885d-3a2a70a2bd73
index: y
internal: n
snippet: y
---

# Using Social Graph{#using-social-graph}

### Introduction {#introduction}

The ability for a community member to follow [activities](../../communities/using/activities.md) as well as be followed is established through two components : `Follow`and `Following`.

The `Follow`component must be associated with another resource, and this association is already established for community members and features.

The `Following`component simply lists the members that are either following the current member or are being followed by the current member. This social graph of the relationships between members is included in the user profile established for a [community site](../../communities/using/overview.md#communitiessites).

### Adding Following to a Page {#adding-following-to-a-page}

If it is desired to add a `Following`component to a page in author mode, locate the component

* `Communities / Following`

and drag it into place on a page where the social graph should appear.

For necessary information, visit [Communities Components Basics](../../communities/using/basics.md).

When the [required client-side libraries](../../communities/using/essentials-socialgraph.md#essentialsforclientside) are included, this is how the `Following` component will appear :

![](assets/chlimage_1-459.png)

### Configuring Following {#configuring-following}

Currently, it is necessary to set the property to determine whether the component displays the `follows`relationship, or the `following`relationship.

### Additional Information {#additional-information}

More information may be found on the [Social Graph Essentials](../../communities/using/essentials-socialgraph.md) page for developers.