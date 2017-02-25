# Persisting storage (preview)
The Cloud Console allows users to attach their own fileshare held in Azure Storage to maintain file persistence across console sessions. 
During preview we allow users to bring their own storage account to mount under the user's $HOME directory as a directory named `clouddrive`. 
Only files in this mounted directory will be persisted across sessions.

**NOTE 2/13/17** 
* Your file storage will mount as a directory within the user $HOME directory named `clouddrive`.
* This is under active development so expect behavior to evolve over time, please leave feedback on the Teams discussion for us to consider.

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
This will prompt you to restart the console or prompt you to create a new storage account if it does not already exist.

You should now be able to upload/download to/from your fileshare from the `clouddrive` directory within the Cloud Console.
Uploading/downloading from/to your local machine can be done via the Azure Files portal blades.

To see more details run `createclouddrive -h`: <br>

Options: <br>
  -s | Subscription ID or name <br>
  -g | Resource group name <br>
  -n | Storage account name <br>
  -F | Create storage account if it doesn't exist <br>
  -f | Fileshare name <br>
  -? | -h | --help Shows this usage text <br>

## Unmounting a storage account
Coming soon

## Show tagged storage account
Coming soon

## Upload/download files
You can utilize the Portal GUI for Azure Files to upload or download files to/from storage.
Editing/removing/adding files from within the console will also reflect in the File Storage GUI upon blade refresh.

1. Navigate to the mounted fileshare
![](../media/touch-txt-storage.png)
2. Select target file in Portal
3. Hit "Download"
![](../media/download-storage.png)

## Next steps
[ACC Quickstart](../Get-started/acc-quickstart.md) <br>
[About Azure File storage](https://docs.microsoft.com/azure/storage/storage-introduction#file-storage) <br>
[Learn more about Storage tags](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) <br>