---
title: Enabling and disabling safe backup mode
seo-title: Enabling and disabling safe backup mode
description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
seo-description: On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory. Learn how to enable and disable safe backup mode.
uuid: 987c6999-c116-420b-b71e-ce36c68b955c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c024e9e1-b192-494a-99ac-e29e706decba
index: y
internal: n
snippet: y
---

# Enabling and disabling safe backup mode{#enabling-and-disabling-safe-backup-mode}

On the Backup Settings page, you can operate AEM forms in safe backup mode so that you can reliably back up your database and Global Document Storage (GDS) (GDS) directory.

While AEM forms is in safe backup mode, it operates normally, except that it does not actively remove files from the GDS directory.

>[!NOTE]
>
>Setting this option does not back up your system; it prepares your system for backup.

## Enable safe backup mode {#enable-safe-backup-mode}

1. In administration console, click Settings &gt; Core Systems Settings &gt; Backup Settings.
1. On the Backup Settings page, select Operate In Safe Backup Mode and click OK.

>[!NOTE]
>
>If the system is already running in safe backup mode, a new reservation will not be created when you click OK.

## Disable safe backup mode {#disable-safe-backup-mode}

1. In administration console, click Settings &gt; Core Systems Settings &gt; Backup Settings.
1. On the Backup Settings page, deselect Operate In Safe Backup Mode and click OK.
