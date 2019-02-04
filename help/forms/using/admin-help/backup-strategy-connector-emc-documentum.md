---
title: Backup strategy for Connector for EMC Documentum users
seo-title: Backup strategy for Connector for EMC Documentum users
description: null
seo-description: Check how to create a backup strategy for Connector for EMC Documentum users.
uuid: 4425abb5-c049-4910-8f85-0fd72d38da8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0c7d3f59-0d12-4ec2-ae42-057974de9fd3
index: y
internal: n
snippet: y
---

# Backup strategy for Connector for EMC Documentum users{#backup-strategy-for-connector-for-emc-documentum-users}

<!--
Comment Type: remark
Last Modified By:
Last Modified Date:
<p>Added for bug 1787759, removed for 1811387, modified for bug 1874975:</p>
-->

If you have Connector for EMC Documentum installed, in addition to the instructions in this chapter, your backup and recovery strategy must include backing up (or recovering) the computer that the respective ECM system is installed on. (See the ECM Documentum documentation).

Back up your AEM forms environment by using ECM repository and performing the following tasks:

* Back up AEM forms by following the instructions described in this document.
* Back up your ECM Documentum system by following the instructions in [Back up the EMC Documentum Content Server](../../../forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

Restore AEM forms environment by using ECM repository and performing the following tasks:

* Restore your respective ECM system by following the instructions in [Restore the EMC Documentum Content Server](../../../forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* Restore AEM forms by following the instructions described in this document.
