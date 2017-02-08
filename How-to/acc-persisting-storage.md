# Persisting storage (preview)
The cloud console allows users to attach their own Azure Files storage to maintain persistence across console sessions. 
This also enables you to work on shared files between team members straight from the browser.

## Mount Azure Files
From your Cloud Console run: <br>
`createclouddrive -h`

Options: <br>
  -s | Subscription ID or name <br>
  -g | Resource group name <br>
  -n | Storage account name <br>
  -F | Create storage account if it doesn't exist <br>
  -f | Fileshare name <br>
  -? | -h | --help Shows this usage text <br>

This will prompt you for information to select an Azure Files account or create one for you.

## How it works
The cloud console will add a "tag" to your storage account labeled "cloudconsole". 
When searching for the correct storage account to mount, the cloud console will grab the first account tagged with this marker.

## Upload files
You can utilize the Portal GUI for Azure Files to edit files held in storage. You can also edit/remove/add files from the console and see it reflect in the GUI.

## Next steps