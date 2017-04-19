---
title: Azure Cloud Shell (Preview) Overview | Microsoft Docs
description: Overview of the Azure Cloud Shell.
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
# Azure Cloud Shell (preview)
Azure Cloud Shell is an interactive, browser-based command-line interface for managing Azure resources.

The shortlink to this documentation is [aka.ms/accbetadocs](https://www.aka.ms/accbetadocs)

## Preview access 
### Azure Advisors
1. Get whitelisted from the forms shared in the Advisor Yammer (steady rollout beginning end of March)
2. Navigate to [aka.ms/accbeta](https://www.aka.ms/accbeta)
3. Launch the Shell via the terminal icon on the top navigation pane.
![](media/shell-icon.png)

### Internals
1. Navigate to [aka.ms/accbeta](https://www.aka.ms/accbeta) or ms.portal.azure.com
2. Launch the Cloud Shell via the terminal icon on the top navigation pane.

## Preview FAQ
* [How do I persist files across sessions?](acc-persisting-storage.md) 
  * Mount an Azure file share via `createclouddrive -h` to receive file persistence in two areas:
    1. Entirety of your $Home directory will persist as a 5-GB image placed in the specified file share
    2. A `clouddrive` subdirectory under your $Home will sync to the file share for individual file interaction
  * Cloud Shell will automatically mount the same share on subsequent sessions
  * Learn how this works at [Persist Files in Cloud Shell](acc-persisting-storage.md) 

* [How do I upload/download from local machine to Cloud Shell?](https://github.com/jluk/ACC-Documentation/blob/master/acc-persisting-storage.md#upload-or-download-local-files)
  * The Azure Files portal GUI syncs to the `clouddrive` subdirectory and can be interacted via Azure portal
  * Follow [step-by-step upload/download instructions here](https://github.com/jluk/ACC-Documentation/blob/master/acc-persisting-storage.md#upload-or-download-local-files)

* [What does it cost?](acc-pricing.md)
  * Cloud Shell is free, mounting storage incurs regular Azure Storage charges

* [What tools are installed on Cloud Shell?](acc-features.md)
  * Check the full [feature list here](acc-features.md)

* Do I have sudo permissions?
  * Sudo permissions are not supported today given the ephemeral nature of Cloud Shell

* [How do I copy and paste?](acc-use-shell-window.md)
  * Currently Windows only supports right-click copy pasting in Chrome and Edge
  * OS X supports cmd-v and cmd-c across all browsers

## Concepts
* Machine state and files do not persist beyond the active session by default
  * You may [mount Azure storage to persist files.](acc-persisting-storage.md) 
* Cloud Shells are assigned at one machine per unique user
  * Your Azure account is the only one with access to your user assigned Cloud Shell
* Permissions are set as a regular Linux user
  * You may install packages via curl to your $Home directory

* Cloud Shell runs on an ephemeral machine provided on a per-session, per-user basis
* Cloud Shell times out after 10 minutes without output activity

## Features
* A browser-based BASH workstation built for Azure
* Automatic authentication
* Bring your own Azure Files for file persistence

Check the full [feature list here](acc-features.md).

## Examples
* Create or edit scripts to manage Azure resources from any browser
* Simultaneously manage resources via portal and command line
* Test-drive Azure CLI 2.0

## Pricing
The Cloud Shell is a free service to all Azure customers. Regular storage costs apply if mounting an Azure file share.

## Supported browsers
The Cloud Shell is recommended for Chrome, Edge, and Safari. 

The Cloud Shell is supported for Chrome, Firefox, Safari, IE, and Edge, but shortcut functionality is subject to specific browser settings.

For all limitations visit [limitations of Cloud Shell](acc-limitations.md).
## Feedback
### Azure Advisors
1. [Advisor Yammer @ aka.ms/accadvisorfeedback](https://aka.ms/accadvisorfeedback) <br>

### Internals
1. [Internal Yammer @ aka.ms/accfeedback](https://aka.ms/accfeedback) <br>
2. Cloud Shell Discussion on Microsoft Teams <br>

## Known Preview Issues
1. CLI 2.0 cmd and autocomplete performance
2. Shortcuts (ctrl-v and ctrl-c) not supported on Windows during Preview
3. Right-click paste not supported on IE/Firefox