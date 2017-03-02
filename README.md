# Azure Cloud Console (preview)
This repo includes staged documents for the Azure Cloud Console. Please refer to these documents for updates throughout previews.

![](media/beta-screenshot.png)

* Access via [aka.ms/accbeta] (https://www.aka.ms/accbeta)
* Shortlink to these docs via [aka.ms/accbetadocs] (https://www.aka.ms/accbetadocs)

## About Cloud Console
The Cloud Console is a free service providing a browser accessible BASH shell. 
This console is provided from an ephemeral container free of charge by Azure. You are a regular user on the Linux container.

Each console is provided on a per-session, per-user basis so state will only persist in storage explicitly attached for that purpose. 
System-wide changes will not transfer across sessions.

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

## VM sku
Your console is running in a Debian-based Linux container on a single-tenant F1 during preview.

## Pricing
This will be a free service to all Azure customers.

## Supported browsers
The Cloud Console is supported for Chrome, Firefox, Safari, IE, and Edge. Shortcut functionality will be subject to browser settings.

## Feedback
[Internal] Please provide feedback on the Cloud Console Teams discussion.

## Updates
* Mounting storage - v0.1 live (run `createclouddrive` to create subdirectory found in user's HOME)
* Tooling 2.0 - TBD
* Force restart - TBD

## Known Preview Issues
1. CLI 2.0 cmd and autocomplete performance - F1 compensation
2. Force kill/restart is coming soon, if your console freezes please open an issue with repro details. Refreshing the page and relaunching the console acts as a force restart for now.
3. Portal tabs left inactive for long periods of time will have tokens expire, this can disable reactivating the console. Please refresh your page to fix this.
4. Maintaining subscription state across sessions - fix coming
5. Shortcuts (ctrl-v and ctrl-c) not supported on Windows in preview
6. Right-click paste not supported on IE/Firefox