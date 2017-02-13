# Persisting storage (preview)
The cloud console allows users to attach their own Azure Files storage to maintain file persistence across console sessions. 
During preview we allow users to bring their own storage account to mount under the user's $HOME directory. Only files in this mounted directory will be persisted across sessions.

As of **2/13/17** your file storage will mount as a directory within the user $HOME directory named `clouddrive`.

**Note** This is under active development so expect behavior to evolve over time, please leave feedback on the Teams discussion for us to consider.

## Mount Azure Files
From your Cloud Console run: <br>
`createclouddrive -s mySub -g myRG -n exName -f myShare`

This will mount existing File storage to your console or prompt you to create new storage to mount.

To see more details run `createclouddrive -h`: <br>

Options: <br>
  -s | Subscription ID or name <br>
  -g | Resource group name <br>
  -n | Storage account name <br>
  -F | Create storage account if it doesn't exist <br>
  -f | Fileshare name <br>
  -? | -h | --help Shows this usage text <br>

You are now be able to upload/download to your fileshare from the `clouddrive` directory.
Uploading and downloading from your local machine can be done via the Azure Files portal blades.

## How it works
The cloud console will add a "tag" to your storage account labeled "cloud-console-files-for-user@domain.com : fileshareName". 
Upon initializing your console session, the cloud console will search for the first account tagged with this marker.

## Upload/download local files
You can utilize the Portal GUI for Azure Files to edit files held in storage. 
Editing/removing/adding files from within the console will also reflect in the Files GUI upon blade refresh.

## Next steps
[ACC Quickstart](../Get-started/acc-quickstart.md) <br>
[About Azure File storage](https://docs.microsoft.com/en-us/azure/storage/storage-introduction#file-storage) <br>