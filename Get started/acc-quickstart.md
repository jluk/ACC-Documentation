# Quickstart
This article shows you how to use the Azure Cloud Console in the [Azure Portal](https://portal.azure.com/).

The requirements are:
* [an Azure account](https://azure.microsoft.com/pricing/free-trial/)

## Sign in
Sign into the Azure portal with your Azure account identity, click **+ New** in the upper left corner:

![screen1](../media/virtual-machines-linux-quick-create-portal/screen1.png)

## Start console
Click the **Start Azure Cloud Console** button in the top navigation bar of the page.

You are now authenticated and ready to begin use.

## Command line usage
Try the Azure CLI 2.0 with 'az --version'. This will output versions of each Azure SDK installed.

### Set your subscrciption
1. Check subscriptions you have access to: <br>
`az account list`
2. Copy paste the id of your target subscription from the json output: <br>
`"id": "12345678-test-expl-123456789101"`
3. Set your account to the chosen subscription: <br>
`az account set --subscription ExampleGUID`

### Create a resource group

`az resource group create -l westus -n MyRG` <br>
You can now search for `MyRG` in Portal and utilize the GUI if preferred.

### Create a Linux VM
Create an Ubuntu VM in your new resource group: <br>
`az vm create -n my_vm_name -g myrg --image UbuntuLTS --authentication-type ssh --ssh-key-value "<ssh-rsa-key, key-file-path or not specified for default-key-path>"`

### Cleaning up 
Delete your resource group and VM: <br>
`az group delete -n MyRG`

You can now exit the console with the 'x' in the right corner of the console window. You session will be active for 10 minutes after the last output at which point it will timeout. You may reactivate a console anytime for free.

## Attach persistent storage
For preview we allow you to attach any Azure Files Storage account you have. This enables you to share persistent storage with teams to share scripts, docs, or other files. [Azure Files storage costs](https://azure.microsoft.com/en-us/pricing/details/storage/files/) will be charged baesd on storage consumption.

### First time

### Changing storage

## Next Steps
[Learn more about Azure CLI 2.0] (https://docs.microsoft.com/en-us/cli/azure/) <br>
[Learn more about Azure File Storage] (https://docs.microsoft.com/en-us/azure/storage/storage-introduction#file-storage) <br>
