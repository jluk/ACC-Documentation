---
title: Azure Cloud Console Overview | Microsoft Docs
description: Overview of the Azure Cloud Console.
services: 
documentationcenter: ''
author: jluk
manager: timlt
tags: azure-resource-manager
 
ms.assetid: 
ms.service: 
ms.workload: infrastructure-services
ms.tgt_pltfrm: vm-linux
ms.devlang: na
ms.topic: article
ms.date: 03/22/2017
ms.author: juluk
---
# Azure Cloud Console (preview)
Azure Cloud Console is your Azure-curated admin machine. 
This console is your personal sandbox enabling you to deploy, manage, and develop Azure resources directly from the browser.

The shortlink to this documentation is [aka.ms/accbetadocs](https://www.aka.ms/accbetadocs)

## Preview access 
### Azure Advisors
1. Get whitelisted from the forms shared in the Advisor Yammer (steady rollout beginning end of March)
2. Navigate to [aka.ms/accbeta](https://www.aka.ms/accbeta)
3. Launch the console via the terminal icon on the top navigation pane.

### Internals
1. Navigate to [aka.ms/accbeta](https://www.aka.ms/accbeta) or ms.portal.azure.com
2. Launch the console via the terminal icon on the top navigation pane.
![](media/console-icon.png)

## Preview FAQ
* [How do I persist files across sessions?](/How-to/acc-persisting-storage.md) 
  * Mount an Azure file share via `createclouddrive -h` to receive 2 methods of persistence:
    1. Entirety of your $Home directory will persist as a 5GB image placed in the specified file share
    2. A `clouddrive` subdirectory under your $Home will sync to the file share for individual file interaction
  * Cloud Console will automatically mount the same share on subsequent sessions
  * Learn more about benefits and how this works at [Persist Files in Cloud Console](/How-to/acc-persisting-storage.md) 

* [How do I upload/download from local machine to Cloud Console?](https://github.com/jluk/ACC-Documentation/blob/master/How-to/acc-persisting-storage.md#upload-or-download-local-files)
  * The Azure Files Portal GUI syncs to the `clouddrive` subdirectory and can be interacted via Azure Portal
  * Follow [step-by-step upload/download instructions here](https://github.com/jluk/ACC-Documentation/blob/master/How-to/acc-persisting-storage.md#upload-or-download-local-files)

* [What does it cost?](Concepts/acc-pricing.md)
  * Cloud Console is free, mounting storage incurs regular Azure Storage charges

* [What tools are installed on the console?](Concepts/acc-features.md)
  * Check the full [feature list here](Concepts/acc-features.md)

* Do I have sudo permissions?
  * Sudo permissions are not supported today given the ephemeral nature of Cloud Console

* [How do I copy and paste?](How-to/acc-use-console-window.md)
  * Currently Windows only supports right-click copy pasting in Chrome and Edge
  * OS X supports cmd-v and cmd-c across all browsers

## Concepts
* Machine state and files do not persist beyond the active session by default
  * You may [mount Azure storage to persist files.](/How-to/acc-persisting-storage.md) 
* Consoles are assigned by unique user IDs so your Azure account is the only one with access to your Cloud Console
* Permissions are set as a regular user
* Console runs on an ephemeral machine provided on a per-session, per-user basis
* Console times out after 10 minutes without output activity

## Features
* A browser-based BASH workstation built for Azure
* Automatic authentication
* Bring your own Azure Files for file persistence

Check the full [feature list here](Concepts/acc-features.md).

## Examples
* Try out the new Azure CLI 2.0
* SSH directly from the Azure Portal
* Manage resources via GUI or CLI, side-by-side
* Test documentation scripts without leaving your browser

## Pricing
The Cloud Console is a free service to all Azure customers. Regular storage costs apply if mounting an Azure file share.

## Supported browsers
The Cloud Console is recommended for Chrome, Edge, and Safari. 

The console is supported for Chrome, Firefox, Safari, IE, and Edge, but shortcut functionality will be subject to specific browser settings.

## Feedback
### Azure Advisors
1. [Advisor Yammer @ aka.ms/accadvisorfeedback](https://aka.ms/accadvisorfeedback) <br>

### Internals
1. [Internal Yammer @ aka.ms/accfeedback](https://aka.ms/accfeedback) <br>
2. Cloud Console Discussion on Microsoft Teams <br>

## Known Preview Issues
1. CLI 2.0 cmd and autocomplete performance
2. Shortcuts (ctrl-v and ctrl-c) not supported on Windows during Preview
3. Right-click paste not supported on IE/Firefox