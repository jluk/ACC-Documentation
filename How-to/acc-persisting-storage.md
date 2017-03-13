---
title: Persisting files in Azure Cloud Console | Microsoft Docs
description: Walkthrough of how to mount Azure file shares to the Azure Cloud Console.
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

# Persisting storage (preview)
The Cloud Console allows users to attach their own fileshare held in Azure Storage to maintain file persistence across console sessions.
Anything stored in Azure Files is subject to regular Azure Storage pricing. [Click here for details on Azure Files prices.](https://azure.microsoft.com/en-us/pricing/details/storage/files/)

Persisting files in Cloud Console follows this process: <br>

1. Specify a file share to mount via `createclouddrive` command and Cloud Console will tag it
2. Console start searches for tag and if found, mounts on /usr/userName/clouddrive
3. Subdirectory `clouddrive` is created and supports GUI interaction to [upload/download to/from your local machine via Azure Portal](#upload-or-download-local-files)
4. A 5GB image is also created and stored in the file share to persist the user $Home directory

This enables many use cases such as: <br>
* Upload/download local files to/from the Cloud Console via clouddrive
* Persisting ssh keys stored in your .ssh folder across sessions (captured in mounted file share's .img)
* Allowing multiple users to edit a shared file share from the Cloud Console

## How it works
Upon choosing to mount an Azure Storage account, the Cloud Console will add a "tag" to the selected storage account using the format: <br>

| Key | Value |
|:-------------:|:-------------:|
|cloud-console-files-for-user@domain.com|fileshareName|

Upon initialization, every Cloud Console session searches for the key and mounts the fileshare specified in the value.

## Mounting a storage account
To mount an Azure Files storage account: <br>
1. Open a Cloud Console session <br>
2. Run: <br>
```
createclouddrive -s mySub -g myRG -n exName -f myShare
```
If successful you will be prompted to restart the console or to create a new storage account if the storage account does not already exist.
```
justin@Azure:~$ createclouddrive -s borisb-internal-sub -g acc-a0 -n acca0disks656 -f myClouddrive
INFO: Setting subscription (juluk-subscription)
INFO: User Principal Name: juluk@microsoft.com
INFO: Getting storage account (acca0disks656) in resource group (acc-a0)
{
  "accessTier": null,
  "creationTime": "2017-03-02T19:43:03.975183+00:00",
  "customDomain": null,
  "encryption": null,
  "id": "/subscriptions/ex-subscription-guid/resourceGroups/acc-a0/providers/Microsoft.Storage/storageAccounts/acca0disks656",
  "kind": "Storage",
  "lastGeoFailoverTime": null,
  "location": "westus",
  "name": "acca0disks656",
  "primaryEndpoints": {
    "blob": "https://acca0disks656.blob.core.windows.net/",
    "file": "https://acca0disks656.file.core.windows.net/",
    "queue": "https://acca0disks656.queue.core.windows.net/",
    "table": "https://acca0disks656.table.core.windows.net/"
  },
  "primaryLocation": "westus",
  "provisioningState": "Succeeded",
  "resourceGroup": "acc-a0",
  "secondaryEndpoints": null,
  "secondaryLocation": null,
  "sku": {
    "name": "Standard_LRS",
    "tier": "Standard"
  },
  "statusOfPrimary": "available",
  "statusOfSecondary": null,
  "tags": {
    "cloud-console-files-for-juluk@microsoft.com": "myClouddrive"
  },
  "type": "Microsoft.Storage/storageAccounts"
}
INFO: Provision succeeds. Please type 'exit' to restart the console.
```

You should now be able to upload/download to/from your fileshare from the `clouddrive` directory within the Cloud Console.
Uploading/downloading from/to your local machine can be done via the Azure Files portal blades.

To see more details run `createclouddrive -h`: <br>
```
Options: <br>
  -s | Subscription ID or name <br>
  -g | Resource group name <br>
  -n | Storage account name <br>
  -F | Create storage account if it doesn't exist <br>
  -f | Fileshare name <br>
  -? | -h | --help Shows this usage text <br>
```
## Updating a storage account
Using the `createclouddrive` command will automatically remove the tag of the previous storage account and add it to the new storage account.

## Unmounting a storage account
To unmount a fileshare from Cloud Console, simply delete the storage tag on the storage account.

![](../media/unmount-storage.png)

## Show tagged storage account
To find details about your mounted storage run `df`. The filepath to clouddrive will show your storage account name and fileshare in the url.

`//storageaccountname.file.core.windows.net/filesharename`

```
justin@Azure:~$ df
Filesystem                                         1K-blocks    Used  Available Use% Mounted on
overlay                                             29711408 5577940   24117084  19% /
tmpfs                                                 986716       0     986716   0% /dev
tmpfs                                                 986716       0     986716   0% /sys/fs/cgroup
/dev/sda1                                           29711408 5577940   24117084  19% /etc/hosts
shm                                                    65536       0      65536   0% /dev/shm
//exporterstorage219.file.core.windows.net/tester 5368709120      64 5368709056   1% /home/justin/clouddrive
justin@Azure:~$
```

## Upload or download local files
You can utilize the Portal GUI for Azure Files to upload or download files to/from storage.
Editing/removing/adding files from within the console will also reflect in the File Storage GUI upon blade refresh.

1. Navigate to the mounted fileshare
![](../media/touch-txt-storage.png)
2. Select target file in Portal
3. Hit "Download"
![](../media/download-storage.png)

**Note** <br>
If you need to download a local file that exists in your $Home directory:
1. Copy it to `clouddrive` <br>
2. Follow [previous steps](#upload-or-download-local-files) <br>

## Next steps
[ACC Quickstart](../Get-started/acc-quickstart.md) <br>
[About Azure File storage](https://docs.microsoft.com/azure/storage/storage-introduction#file-storage) <br>
[Learn more about Storage tags](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) <br>