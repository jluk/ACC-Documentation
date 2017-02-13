# Azure Cloud Console (preview)
This repo includes staged documents for the Azure Cloud Console. Please refer to these documents for updates throughout previews.

## About Cloud Console
The Azure Cloud Console is a free service providing a browser accessible BASH shell. This shell is held within an ephemeral container provided free of charge by Azure. When your console times out you may receive a new container for your next session so state will not carry-over.

### Features
* Browser accessible BASH shell with pre-installed Azure dev tools (email juluk@microsoft.com with new suggestions)
* Automatic authentication launched from the Azure Portal
* Bring your own storage for persistence across sessions

Check the full [feature list here](Concepts/acc-features.md).

## Preview access 
In order to receive internal access you must:

1. Be whitelisted - this was done via a sign-up form on the blog announcement through January 10th, internals may email juluk@microsft.com to request further access. <br>
2. Navigate to [aka.ms/accbeta] (www.aka.ms/accbeta). This shortlink provides full Portal access so it can be used as a replacement link. <br>
3. Launch the console via the terminal icon on the top navigation pane.

## Console timeout
Your console is set to timeout after 10 minutes of zero output activity. You can reactivate your console by pressing the "Enter" key after timeout.

## VM sku
Your console is running in a Debian-based Linux container on a single-tenant F1 during preview.

## Pricing
This will be a free service to all Azure customers.

## Supported browsers
The cloud console is supported for Chrome, Firefox, Safari, IE, and Edge.

## Feedback
[Internal] Please provide feedback on the Cloud Console Teams discussion.

## Updates
* Mounting storage - initial state live (currently as `clouddrive` directory found in user's HOME)
* Tooling 2.0 - TBD
* Force restart - TBD

## Known Preview Issues
1. Open issue with CLI 2.0 performance
2. Force kill/restart is coming soon, if your console freezes please open an issue with repro details. Refreshing the page and relaunching the console acts as a force restart for now.
3. Portal tabs left inactive for long periods of time will have tokens expire, this can disable reactivating the console. Please refresh your page to fix this.