# Features
Azure Cloud Console offers a full bash shell to manage resources and develop applications on Azure directly from the Azure Portal.

## Browser-access to a BASH shell (preview)
Azure provides you with your own Linux container running on a single-tenant F1 VM running a Debian-based Linux operating system.
Each console is provided on a per-session, per-user basis. 

A console session will persist state while active and terminate after 10 minutes of 
no output activity. After this point you are not guaranteed the same container on a new request for a console.

## Persistent storage (preview)
Since the Cloud Console is allocated on a per-session basis with an ephemeral container, files will not persist across sessions by default.
You may mount your own fileshares in Azure Files storage to persist files across sessions.

This allows sharing files across teams who have access to the Azure Files account and incurs usual charges associated with Azure Files.
Once a fileshare is associated with your console, it will be mounted on every console created for you.

To learn more visit [Attaching file storage](../How-to/acc-persisting-storage.md).

## Pre-installed tools (preview)
Since the Cloud Console runs off of a container image, the Azure platform will manage updating tools on your behalf so each session offers the latest and greatest tools.

* bash, sh 
* Azure CLI 1.0 and 2.0
* less, jq
* vim, nano
* npm, pip
* git

## Language support (preview)
* Node.js
* Python

## Authentication
Cloud Console takes care of authentication since it is launched from your Azure Portal homepage. No additional authorization is needed to access resources from the `az cli 2.0`.

## Telemetry statistics
The Cloud Console collects telemetry through the `az cli 2.0` about what resources are being used. No personally identifiable information such as arguments for commands are captured and as a result collected telemetry can never be tied back to individual users.

## Next steps
[ACC Quickstart](../Get-started/acc-quickstart.md) <br>
[Azure CLI 2.0 documentation](https://docs.microsoft.com/en-us/cli/azure/) <br>
