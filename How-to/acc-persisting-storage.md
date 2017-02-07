# Persisting storage (preview)
The cloud console allows users to attach their own Azure Files storage to maintain persistence across console sessions. 
This also enables you to work on shared files between team members straight from the browser.

## Mount Azure Files
From your Cloud Console run: <br>
`create clouddrive`

This will prompt you for information to select an Azure Files account or create one for you.

## How it works
The cloud console will add a "tag" to your storage account labeled "cloudconsole". 
When searching for the correct storage account to mount, the cloud console will grab the first account tagged with this marker.

If you have multiple storage accounts with this special tag, the Cloud Console will grab the first it can find.

## Next steps