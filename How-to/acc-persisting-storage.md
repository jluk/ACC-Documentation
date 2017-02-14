# Persisting storage (preview)
The Cloud Console allows users to attach their own Azure Files storage to maintain file persistence across console sessions. 
During preview we allow users to bring their own storage account to mount under the user's $HOME directory. Only files in this mounted directory will be persisted across sessions.

As of **2/13/17** your file storage will mount as a directory within the user $HOME directory named `clouddrive`.

**Note** This is under active development so expect behavior to evolve over time, please leave feedback on the Teams discussion for us to consider.

## How it works
Upon choosing to mount a storage account, the Cloud Console will add a "tag" to the selected storage account using the format: <br>

| Key | Value |
|:-------------:|:-------------:|
|cloud-console-files-for-user@domain.com|fileshareName|

Upon initialization, every Cloud Console session searches for and mounts the storage account containing this tag.

## Mount Azure Files
From your Cloud Console run: <br>
`createclouddrive -s mySub -g myRG -n exName -f myShare`

This will prompt you to restart the console or prompt you to create a new storage account if it does not already exist.

To see more details run `createclouddrive -h`: <br>

Options: <br>
  -s | Subscription ID or name <br>
  -g | Resource group name <br>
  -n | Storage account name <br>
  -F | Create storage account if it doesn't exist <br>
  -f | Fileshare name <br>
  -? | -h | --help Shows this usage text <br>

You should now be able to upload/download to/from your fileshare from the `clouddrive` directory within the Cloud Console.
Uploading and downloading from your local machine can be done via the Azure Files portal blades.

## Unmounting a storage account
## Show tagged storage account
To list details about your mounted storage account run: <br>
`az group list --tag cloud-console-files-for-user@domain.com=fileshareName`

## Upload/download local files
You can utilize the Portal GUI for Azure Files to edit files held in storage. 
Editing/removing/adding files from within the console will also reflect in the File Storage GUI upon blade refresh.

## Next steps
[ACC Quickstart](../Get-started/acc-quickstart.md) <br>
[About Azure File storage](https://docs.microsoft.com/azure/storage/storage-introduction#file-storage) <br>
[Learn more about Storage tags](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) <br>