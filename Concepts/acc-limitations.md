---
title: Azure Cloud Console Limitations | Microsoft Docs
description: Overview of limitations of Azure Cloud Console
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
ms.date: 03/09/2017
ms.author: juluk
---

# Limitations
Azure Cloud Console has the following known limitations.

## User permissions
* Permissions are set as regular users without sudo access given the stateless nature of the feature
* Should you see a valid need for sudo level access, please provide this feedback to the team on Yammer

## System state and persistence
The container providing your Cloud Console session is ephemeral and is recycled after your session is inactive for 30 minutes.
* Without mounting storage all modifications will be lost
* With mounted storage all modifications outside your `$Home` are lost

## Performance
* Cloud Console's first initiation may take up to 25 seconds, subsequent sessions should be about five seconds
* New container builds are generated often in an effort to include more tools, performance may fluctuate as this process is refined

## Browser support
* Cloud Console supports the latest versions of Microsoft Edge, Microsoft Internet Explorer, Google Chrome, Mozilla Firefox, and Apple Safari
* Safari in private mode is not supported
* Windows machines do not currently support copy-paste shortcuts
* Firefox and Internet Explorer do not support right-click paste

## Usage limits
* Cloud Console is intended for interactive use cases, as a result any long-running non-interactive sessions will be ended automatically. Extreme prolonged usage will cause session termination without warning.

## Network connectivity
* Any latency in the Cloud Console is subject to local internet connectivity, Cloud Console will continue to attempt functioning to any instructions sent.

## Next steps
[ACC Quickstart](../Get-started/acc-quickstart.md) <br>
[Mount storage to Cloud Console to persist files](/How-to/acc-persisting-storage.md) 