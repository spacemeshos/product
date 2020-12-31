# Smapp update Spec

## Preliminaries
1. A Smapp release includes a go-sm binary release that it is designed to work with. We want to keep it this way to avoid users having to download go-sm on app first session as it requires to trust the discovery endpoint and for convince reasons.

2. We decided not to the support more than one sm network in Smapp at any given time, as this requires maintaining a go-sm binary release for each network as not all networks may work with a specific go-sm binary release.

3. Smapp gets the meta-data about a supported public network (e.g. a testnet release) such as config file, dash url, explore url, and more via the sm [public discovery service](https://product.spacemesh.io/#/public_webservices). The only hard-coded network info in Smapp is the discovery service canonical url https://discover.spacemesh.io/networks.json and a go-sm binary release that was tested to work with this network and Smapp assumes that the discovery service only returns data for one sm network. The discovery service includes the latest Smapp and go-sm binary releases numbers supported for the network. For more info refer to https://product.spacemesh.io/#/public_webservices.

4. We will add support for multiple Testnet to the discovery service and to Smapp at a later phase if and when we'll find a need to run more than one long-running open testnet.

## Requirements
1. On Smapp first run user should have an option to opt-out from Smapp checking from updates (it is checked by default), and to disable auto update if check for updates is enabled. For example:

```
Configure App Updates
- [x] Periodically check for app updates
   - [x] Auto-update app when a new update is available.
```

User should be able change these settings at any time from the settings screen. There should also be a manual check for updates button in the settings that will trigger a check for update when the user clicks it regardless of the other settings.

2. Smapp should configure its managed go-sm node to not check for node updates by-itself via the node cli flags it uses to start its managed node. The node update checks are designed to work when the node is running w/o Smapp managing it. e.g. directly from the command line.

3. A new update of Smapp may (or may not) include a new go-sm node binary release. The update should be packaged as an installer for each supported platform that can run in silent-mode by Smapp or by an updater process. So we don't need to prepare a special updater binary, build a ui-only update mechanism, and we just reuse the standard smapp installer for app updates triggered from within Smapp.

4. If user is not opted-out from updates checks then Smapp should periodically (say every 24 hours) check for available updates by using the discovery service endpoint. [link to spec here]. Smapp should determine if there's an available update by comparing its version with the latest release version number specified via the discovery service.

5. If an update is available and auto-update is on, and Smapp is running in the background (minimized main window) then it should start the update process automatically. e.g. download and execute the update installer silently and update itself.

> The actual node update process might be a bit involved but it should be handled by the node update mechanism. Smapp should just trigger these mechanisms.

6. If Smapp is running in the foreground when a new update is available, then it should display a modal dialog box informing its user that an update is available, and prompt him to start the update regardless if auto-update is on or off. If the user clicks on 'Later' because he's busy interacting with the app at the moment, then it should show the modal again in the next update check period.

> It is okay to display this dialog box every 24 hours until the user updates because we want users to run the latest versions and discourage them from running older ones.

7. After Smapp installed an update then it should automatically restart itself running the new updated version. On first run after an update Smapp should display a dialog box indicating to the user that it was updated from version 0.x.x to version 0.y.y.

## Updating to a new Testnet
- A testnet that smapp is using may be discontinued from being supported by sm due to an unrecoverable error such as consensus failure.
- In this case sm is likely to release a new testnet with a new net id, and update the discovery service accordingly. e.g. with a new network id, supported smapp and go-sm  releases and a config file for the new network.
- We want to find a process to migrate smapp users form an old testnet to a new one seamlessly while keeping users informed and in the loop about the network change. Here's a proposed solution.

1. On startup, Smapp checks the discovery service to verify it is running on the supported network. It should compare the net id it has from its current config file with the advertised network id. If there's a mismatch then it should prompt the user to update to the new supported testnet in a modal dialog box.

2. If user clicked to update then smapp should download the new config file and verify that its current included go-sm node release it has, is supported by the new network using the min node version data returned by the discovery service.

In case it needs to update its managed go-sm node then it should prompt the user to update Smapp to join the new network and start the update process if user confirms. See standard update process. If its go-sm node release version is supported by the new network then it can just join the new testnet by providing the new config file from the discovery service to its go-sm node.


# Visual Design Guidelines

## App Startup Flow Changes
1. Add 'App Setup' step before the new wallet setup step in the first-run flow.
2. App Setup Screen content:

Title: App Updates
Content:

- [x] periodically check for app updates
   - [x] auto-update app when a new update is available.

- `Learn more about updates` link - links to docs in the testnet guide.
- If user un-checks the periodical updates checkbox then display an info area in the screen:  `We recommend that you enable all auto-updates. This will ensure that you're always running the latest and greatest software released by the Spacemesh team, and will help keep the network secure. Note that this decision has implications on governance.`.


## App Update Section in Settings Screen

- [x] periodically check for app updates
   - [x] auto-update app when a new update is available.

- `Check for Updates` button to trigger a check for update.

## New Update Available Modal Dialog Box
- Title: 'App Update Available'
- Content:
  - Installed app version: 0.x.x
  - New app version available: 0.y.y
  - 'Install Update' button - clicking on it should start an app update process.
  - 'Later' button - clicking on it should close the modal.

## Migrate to a New Network Modal Dialog Box
- Title: 'Migrate to a new testnet'.
- Content:
   -- `Testnet [net-id] is no longer supported and a new testnet [tn-id] is available. Would you like to migrate your app to work with the new testnet?
   -- `Join new Testnet` button - click will migrate smapp to work with the new net-id.
   -- `Later` button - click will close the dialog and smapp will continue to use the old testnet id.

### Notes
- Migrating to a new testnet should update the net-id in the wallet's file.
- If user was smeshing then we should highlight the smeshing tab with an icon such as `!` and when user opens it we want to prompt him to start smeshing setup for the new network.
