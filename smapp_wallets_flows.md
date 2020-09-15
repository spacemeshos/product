# Smapp User Journeys

## Entities

### Testnet Config File
A full node config file describing a Spacemesh Testnet. Required to connect to a testnet. Currently 1 config file embedded in Smapp. We'd like to enable user to use Smapp to connect to different Testnets without having to use a new version of Smapp. The config file specifies a network unique id. To connect to a Testnet, user needs to obtain its config file and save it in a designated location for Smapp to be able to identify it on startup.

### Mainnet Config File
A minimal config file which includes mainnet network id. It is used to create wallets for use on mainnet pre-genesis. Before genesis, a mainnet full config file will be provided and users need to download it and use it to connect to the Mainnet. The full config file will replace the minimal one.

### Wallet File
A wallet data file. Includes wallet and contacts information. Used by both hot wallets and ledger wallets. Private data in this file is always encrypted with the user's provided password. Each wallet must have a data file that specifies it. So user will have a wallet file for each wallet it created in smapp.

### Wallets File
A simple data file which contains a list of user's wallet data files and the location of the data file for each such wallet. This enables users to access any wallet in Smapp. Smapp can only work with one wallet at a time.
If this file is getting corrupted or deleted then user will just need to restore wallets (from paper backup or backup file) to be able to work with them. Path to a restored wallet's data file is added to the Wallets file.

### Public API Web Service
A web servive providing the Spacemesh API over the Internet. The service is using its own managed nodes to connect to the Spacemesh network. A wallet can use this API instead of using an API provided by a local running node.

---------


# Journeys

All flows described here are happy flows and error cases are not considered for sake of simplicity.

## Basic Journeys - One Wallet

In the flows below, user doesn't have a wallet in the first session and only one wallet on the second app session.

### First-Time User Session (Local Node)
> User goal: setup new standard wallet, run a local p2p node and sync it with the network, and setup smeshing.

1. App displays the `wallet config` screen (wallet+node or wallet only).
1. User selects to setup a wallet+node and not just wallet.
1. App displays the `wallet setup` screen (standard or ledger).
1. User selects to setup a standard wallet.
1. App displays the `set wallet password` screen.
1. User sets password for new wallet.
1. App starts the smeshing setup flow.
1. User sets up smeshing.

-----

### Second User Session (Local Node)

> User goal: view smeshing rewards, use wallet.

1. App starts local node and if smeshing is setup, configures it to smesh.
1. App displays the `unlock wallet` screen.
1. User enters wallet password to access it.
1. App displays the `main wallet` screen and syncs the mesh in the background.
1. User uses the wallet screen features
1. User switchs to `smeshing screen` to view smeshing status.

-----

### First Time User Experience - (via Public Api)

> User goal: setup a standard wallet without running a local node.

1. App displays the `wallet setup` screen. (wallet+node or wallet).
1. User selects to setup wallet only.
1. App display the `network selection` screen.
1. User selects a public Spacemesh API web service to use with the wallet.
1. App displays the `wallet setup` screen. (standard or ledger).
1. User selects to setup a standard wallet.
1. App displays the `set wallet password` screen.
1. User sets password for new wallet.
1. App gets wallet balance, transactions history, and network status via the API and presents it to the user in the `wallet` screen` and in the `network` screen.
1. User checks his balance, incoming transactions and executes transactions.

----

### Second User Session (via Public Api)

> User goal: work with wallet without running a full mnode.

1. App displays the `unlock wallet` screen.
1. User enters wallet password to access it.
1. App displays the `wallet` screen and updates wallet data via the API,
1. User uses the `wallet` screen features
1. User switches to `network` screen to view network status.

--------

### Adding a Ledger Wallet

> User goal: use a ledger device so sign spacemesh transactions.

1. App displays an `add new wallet` command in the `unlock wallet` screen.
1. User clicks on the add new wallet command.
1. App displays the `network selection` screen (local node or public api)
1. User chooses one of the options for the wallet (local or public)
1. App display the `wallet setup` screen.
1. User selects to setup a ledger wallet.
1. App attempts to connect to ledger device using the sm ledger sdk.
1. If app can't connect to Spacemesh app on a sub-connected ledger device, then it displays the `connect ledger device` screen and provides instructions on how to use ledger with spacemesh.
1. User open the Spacemesh app on his ledger device and usb connects it to his computer.
1. App connects to the Spacemesh app on ledger via the sm ledger sdk.
1. App connects to network via public api or starts a local node based on user selection above.
1. App displays the `wallet` screen.

---------

### Adding a new Standard Wallet

> User goal: setup a new wallet to manage funds and vaults seperately than an existing wallet.

1. App displays an `add new wallet` command in the `uncock wallet` screen.
1. User clicks on the add new wallet command.
1. App displays the `wallet setup` screen (wallet+node or public api)
1. User chooses one of the options for the wallet (local or public)
1. App display the `wallet setup` screen (standard or ledger).
1. User selects to setup a standard wallet.
1. App connect to network via public api or starts a local node based on user selection above.
1. App displays the `wallet` screen.

--------

## Joruneies with Multiple Wallets

In the flows below, user has setup more than one wallet in previous app sessions.

## New App Session (more than one wallet)

> User goal: access one of his previously created wallets and optionally start local node and smeshing.

This flow happens when more than 1 wallet was used in the App in a previous session.

1. App displays the `open wallet` screen. It lists all available wallets.
1. User selects a wallet from the screen.
1. If wallet was configured to use public API then the app configures itself to use this api.
1. If wallet was configured to use a local node then the app configures itself to use a local node and starts it. If user has setup smeshing then the app starts smeshing.
1. App opens the wallet and displays it in the `wallet` screen.


--------

## Switching between wallets

> User goal: quickly access one of the wallets he'd previously created.

1. User clicks on log-out in the main screen.
1. `New App Session` flow runs (above) from step 1.

--------

## Adding a new Vault


----------

## Adding an Existing Vault to a Wallet

-----------



## The Journey - Conceptual View

![](/resources/wallets_usage_flows.png)
