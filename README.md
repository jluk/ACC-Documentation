# Azure Cloud Console (preview)
This repo includes staged documents for the Azure Cloud Console. Please refer to these documents for updates throughout previews.

![](media/beta-screenshot.png)

* Access via [aka.ms/accbeta] (https://www.aka.ms/accbeta)
* Shortlink to these docs via [aka.ms/accbetadocs] (https://www.aka.ms/accbetadocs)

## About Cloud Console
The Cloud Console is a free service providing a browser accessible BASH shell. User permissions are set as a regular user.
* Console runs on an ephemeral container provided on a per-session, per-user basis
* Machine state and files do not persist beyond the active session 
  * You may [mount Azure storage to persist files in the clouddrive directory](/How-to/acc-persisting-storage.md)

### Features
* Browser accessible BASH shell with pre-installed Azure dev tools (submit requests for new tools in Teams discussion)
* Automatic authentication launched from the Azure Portal
* Bring your own storage for file persistence across sessions

Check the full [feature list here](Concepts/acc-features.md).

## Preview access 
In order to receive internal access you must:

1. Be whitelisted - this was done via a sign-up form on the blog announcement through January 10th, internals may email juluk@microsft.com to request further access. <br>
2. Navigate to [aka.ms/accbeta] (https://www.aka.ms/accbeta). This shortlink provides full Portal access so it can be used as a replacement link. <br>
3. Launch the console via the terminal icon on the top navigation pane.

Your initial session will take ~90 seconds to configure, subsequent sessions will be much faster.

## Console timeout
Your console is set to timeout after 10 minutes of zero output activity. 
You can reactivate your console by pressing the "Enter" key after timeout.

## Pricing
This will be a free service to all Azure customers.

## Supported browsers
The Cloud Console is recommended for Chrome, Edge, and Safari. 
The console is supported for Chrome, Firefox, Safari, IE, and Edge, but shortcut functionality will be subject to specific browser settings.

## Feedback
[Internal] Please provide feedback on the Cloud Console Teams discussion.

## Known Preview Issues
1. CLI 2.0 cmd and autocomplete performance - F1 compensation
2. Force kill/restart is coming soon, if your console freezes please open an issue with repro details. Refreshing the page and relaunching the console acts as a force restart for now.
3. Portal tabs left inactive for long periods of time will have tokens expire, this can disable reactivating the console. Please refresh your page to fix this.
4. Maintaining subscription state across sessions - fix coming
5. Shortcuts (ctrl-v and ctrl-c) not supported on Windows in preview
6. Right-click paste not supported on IE/Firefox