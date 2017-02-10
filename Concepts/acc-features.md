# Features
Azure Cloud Console offers a full bash shell to interact with Azure from.

## Console session (preview)
Azure provides you with your own Linux container running on a single-tenant F1 VM running a Debian-based Linux operating system.
Each console is provided on a per-user, per-request basis. A console session will persist state while active and terminate after 10 minutes of 
no output activity. After this point you are not guaranteed the same container on a new request.

## Persistent storage (preview)
The Cloud Console allows you to mount your own Azure Files Storage. This will be mounted as a directory within your $HOME directory called `clouddrive`.
This allows sharing files across teams who have access to the Azure Files account and incurs usual charges associated with Azure Files.

To learn more visit [Attaching file storage](../How-to/acc-persisting-storage).

## Pre-installed tools (preview)
* bash, sh 
* Azure CLI 1.0 and 2.0
* less, jq
* vim, Nano
* npm, pip
* git
* Docker, Emacs, Gradle, Make, Maven, nvm (todo)

## Language support (preview)
* Node.js
* Python
* Java, Go, Ruby, PHP (todo)

## Authentication
Cloud Console takes care of authentication since it is launched from your Azure Portal homepage. No additional authorization is needed to access resources from the `az cli 2.0`.

## Telemetry statistics
The Cloud Console collects telemetry through the `az cli 2.0` about what resources are being used. No personally identifiable information such as arguments for commands are captured and as a result collected telemetry can never be tied back to individual users.

## Next steps