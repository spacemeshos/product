# Smapp User Journeys

All flows described here are happy flows and error cases are not considered for sake of simplicity.

## Basic Journeys - One Wallet

In the flows below, user doesn't have a wallet in the first session and only one wallet on the second app session.

### Flow 1. First-Time User Session - Standard Wallet & Local Node
> User goal: setup new standard wallet, run a local p2p node and sync it with the network, and setup smeshing.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4847%253A8399%26viewport%3D1389%252C671%252C0.10568313300609589%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays the `wallet config` screen (wallet+node or wallet only).
1. User selects to setup a wallet+node (and not just wallet).
1. App displays the `wallet setup` screen (standard or Ledger).
1. User selects to setup a standard wallet.
1. App displays the `set wallet password` screen.
1. User sets password for new wallet.
1. App starts the smeshing setup flow.
1. User sets up smeshing.

### Flow 2. First-Time User Session - Ledger Wallet & Local Node
> User goal: setup new wallet that is using his Ledger wallet, run a local p2p node and sync it with the network, and setup smeshing.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4741%253A1533%26viewport%3D1373%252C698%252C0.10146976262331009%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays the `wallet config` screen (wallet+node or wallet only).
1. User selects to setup a wallet+node (and not just wallet).
1. App displays the `wallet setup` screen (standard or Ledger).
1. User selects to setup a Ledger wallet.
1. App displays the connect Ledger screen until Spacemesh app is open on a usb-connected Ledger device to the user's computer.
1. App displays the `set wallet password` screen.
1. User sets password for new wallet.
1. App starts the smeshing setup flow.
1. User sets up smeshing.

### Flow 3. First-Time User Session - Standard Wallet via Public Api Service

> User goal: setup a standard wallet without running a local node.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4847%253A14700%26viewport%3D1186%252C925%252C0.1457517147064209%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays the `wallet setup` screen. (wallet+node or wallet).
1. User selects to setup wallet only.
1. App display the `network selection` screen.
1. User selects a public Spacemesh API web service to use with the wallet.
1. App displays the `wallet setup` screen. (standard or Ledger).
1. User selects to setup a standard wallet.
1. App displays the `set wallet password` screen.
1. User sets password for new wallet.
1. App gets wallet balance, transactions history, and network status via the API and presents it to the user in the `wallet` screen` and in the `network` screen.
1. User checks his balance, incoming transactions and executes transactions.

### Flow 4. First Time User Session - Ledger Wallet via Public Api Service

> User goal: setup a standard wallet without running a local node.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4847%253A21001%26viewport%3D1352%252C784%252C0.12511397898197174%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays the `wallet setup` screen. (wallet+node or wallet).
1. User selects to setup wallet only.
1. App display the `network selection` screen.
1. User selects a public Spacemesh API web service to use with the wallet.
1. App displays the `wallet setup` screen. (standard or Ledger).
1. User selects to setup a Ledger wallet.
1. App displays the connect Ledger screen until Spacemesh app is open on a usb-connected Ledger device to the user's computer.
1. App displays the `set wallet password` screen.
1. User sets password for new wallet.
1. App displays the main wallet screen.

-----

### Flow 5. Second User Session (Standard or Ledger wallet and a local node)

> User goal: check smeshing rewards, use wallet.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4847%253A3499%26viewport%3D2244%252C1208%252C0.20544306933879852%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App starts local node and if smeshing is setup, configures it to smesh.
1. App displays the `unlock wallet` screen.
1. User enters wallet password to access it.
1. App displays the `main wallet` screen and syncs the mesh in the background.
1. User uses the wallet screen features.
1. User switchs to `smeshing screen` to view smeshing status.

> User is only prompted to connect ledger wallet when the user needs to sign a new transaction or when user selects to add a new account, and the wallet is a ledger wallet and not a standard one.
----

### Flow 6. Second User Session (Standard or Ledger Wallet via Public Api Service)

> User goal: Work with wallet without running a full node.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4791%253A20985%26viewport%3D785%252C553%252C0.2111605554819107%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays the `unlock wallet` screen.
1. User enters wallet password to access it.
1. App displays the `wallet` screen and updates wallet data via the API,
1. User uses the `wallet` screen features
1. User switches to `network` screen to view network status.

> User is only prompted to connect ledger wallet when the user needs to sign a new transaction or when user selects to add a new account, and the wallet is a ledger wallet and not a standard one.

--------

### Flow 7. Creating a Ledger Wallet (using Local Node or Public Api Service)

> User goal: User has a standard wallet. He's like to use a Ledger device so sign spacemesh transactions. To ahcieve this he needs to create a new Ledger wallet.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4746%253A952%26viewport%3D1493%252C722%252C0.13630522787570953%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays an `add new wallet` command in the `unlock wallet` screen.
1. User clicks on the `add new wallet` command.
1. App displays the `network selection` screen (local node or public api).
1. User chooses one of the options for the wallet (local or public).
1. App display the `wallet setup` screen.
1. User selects to setup a ledger wallet.
1. App attempts to connect to ledger device using the sm ledger sdk.
1. If app can't connect to Spacemesh app on a sub-connected ledger device, then it displays the `connect ledger device` screen and provides instructions on how to use ledger with spacemesh.
1. User open the Spacemesh app on his ledger device and usb connects it to his computer.
1. App connects to the Spacemesh app on ledger via the sm ledger sdk.
1. App connects to network via public api or starts a local node based on user selection above.
1. App displays the `wallet` screen.

---------

### Flow 8. Creating a new Standard Wallet (using Local Node or Public Api Service)

> User goal: Setup a new standard (hot) wallet to manage funds and vaults seperately than an existing wallet.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4847%253A79%26viewport%3D1680%252C729%252C0.13305002450942993%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays an `add new wallet` command in the `uncock wallet` screen.
1. User clicks on the `add new wallet` command.
1. App displays the `wallet setup` screen (wallet+node or public api).
1. User chooses one of the options for the wallet (local or public).
1. App display the `wallet setup` screen (standard or ledger).
1. User selects to setup a standard wallet.
1. App connect to network via public api or starts a local node based on user selection above.
1. App displays the `wallet` screen.

--------

## Joruneies with Multiple Wallets

In the flows below, user has setup more than one wallet in previous app sessions.

### Flow 9. New App Session (more than one wallet)

> User goal: Access one of his previously created wallets and optionally start local node and smeshing.

This flow happens when more than one wallet was used in the App in a previous session.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4791%253A34669%26viewport%3D1148%252C691%252C0.23537872731685638%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays the `open wallet` screen. It lists all available wallets.
1. User selects a wallet from the screen.
1. If wallet was configured to use public API then the app configures itself to use this api.
1. If wallet was configured to use a local node then the app configures itself to use a local node and starts it. If user has setup smeshing then the app starts smeshing.
1. App opens the wallet and displays it in the `wallet` screen.

--------

### Flow 10. Switching Between Wallets

> User goal: quickly access one of the wallets he'd previously created.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4847%253A7372%26viewport%3D770%252C761%252C0.20979978144168854%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. User clicks on log-out in the main screen.
1. `New App Session` flow runs (above) from step 1.

--------

### Flow 11. Creating a new Vault

User goal: Create a new vault to safely store funds via multisig and ledger wallet support, and optionally set daily spending.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4818%253A18647%26viewport%3D1101%252C691%252C0.16945761442184448%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. App displays drop-down next to wallet name in `wallet` screen with wallet commands.
1. User selects `Add new Vault` command from the drop-down.
1. App starts the `new vault` flow (see Figma).

> New vault is added as an account to the wallet that the user is using in the `wallet` screen. It can be added to astandard or a Ledger wallets.

----------

### Flow 12. Adding an Existing Vault to a Wallet

User goal: Use an existing vault that may have been created by another wallet, by another user or by a Spacemesh network genesis flow.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Fproto%2F6bbFkIAzVu36bIpUNnMqoy%2FSmapp-Working-Mocks%3Fnode-id%3D4870%253A4888%26viewport%3D-383%252C-226%252C0.3340447247028351%26scaling%3Dcontain&chrome=DOCUMENTATION" allowfullscreen></iframe>

1. User selects 'Add existing Vault' command from the wallet's settings commands.
1. App starts the `add existing vault` flow (see figma).

-----------

### Flow 13. Accessing an Existing Vault

User goal: view vault's state (balance, pending tranasactions, etc...) and execute vault transaction.

1. App displays an entry for each wallet's vault in the accounts drop down in the `wallet` screen.
1. User selects a vault from the drop-down.
1. App displays the vault's main screen and state.
1. User executes vault commands from the vault's screen.

-----------


## The Journey - Tehnical View


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

----

![](/resources/wallets_usage_flows.png)
