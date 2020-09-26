# Smapp User Journeys

All flows described here are happy flows and error cases are not considered for sake of simplicity.

## Basic Journeys - One Wallet

In the flows below, the user doesn't have a wallet in the first session and only one wallet on the second app session.

### Flow 1. First-Time User Session - Standard Wallet & Local Node
> User goal: setup new standard wallet, run a local p2p node and sync it with the network, and setup smeshing.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4847%3A8399&viewport=872%2C486%2C0.07435446232557297&scaling=min-zoom)

1. App displays the `wallet config` screen (wallet+node or wallet only).
1. User selects to set up a wallet+node (and not just wallet).
1. App displays the `wallet setup` screen (standard or Ledger).
1. User selects to set up a standard wallet.
1. App displays the `set wallet password` screen.
1. User sets a password for the new wallet.
1. App starts the smeshing setup flow.
1. User sets up smeshing.

------

### Flow 2. First-Time User Session - Ledger Wallet & Local Node
> User goal: setup new wallet that is using his Ledger wallet, run a local p2p node and sync it with the network, and setup smeshing.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4741%3A1533&viewport=967%2C516%2C0.07319645583629608&scaling=min-zoom)

1. App displays the `wallet config` screen (wallet+node or wallet only).
1. User selects to setup a wallet+node (and not just wallet).
1. App displays the `wallet setup` screen (standard or Ledger).
1. User selects to setup a Ledger wallet.
1. App displays the `connect Ledger screen` until the `Spacemesh Ledger App` is open on a usb-connected Ledger device to the user's computer.
1. App displays the `set wallet password` screen.
1. User sets a password for the new wallet.
1. App starts the smeshing setup flow.
1. User sets up smeshing.

------

### Flow 3. First-Time User Session - Standard Wallet via Public Api Service

> User goal: setup a standard wallet without running a local node.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4847%3A14700&viewport=832%2C680%2C0.10513978451490402&scaling=min-zoom)

1. App displays the `wallet setup` screen. (wallet+node or wallet).
1. User selects to set up the wallet only.
1. App displays the `network selection` screen.
1. User selects a public Spacemesh API web service to use with the wallet.
1. App displays the `wallet setup` screen. (standard or Ledger).
1. User selects to set up a standard wallet.
1. App displays the `set wallet password` screen.
1. User sets a password for the new wallet.
1. App gets wallet balance, transaction history, and network status via the API and presents it to the user in the `wallet screen` and in the `network` screen.
1. User checks his balance, incoming transactions and executes transactions.

------

### Flow 4. First Time User Session - Ledger Wallet via Public Api Service

> User goal: setup a standard wallet without running a local node.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4847%3A21001&viewport=952%2C578%2C0.09025249630212784&scaling=min-zoom)

1. App displays the `wallet setup` screen. (wallet+node or wallet).
1. User selects to set up wallet only.
1. App displays the `network selection` screen.
1. User selects a public Spacemesh API web service to use with the wallet.
1. App displays the `wallet setup` screen. (standard or Ledger).
1. User selects to set up a Ledger wallet.
1. App displays the `connect Ledger screen` until the `Spacemesh Ledger App` is open on a usb-connected Ledger device to the user's computer.
1. App displays the `set wallet password` screen.
1. User sets a password for the new wallet.
1. App displays the main wallet screen.

-----

### Flow 5. Second User Session (Standard or Ledger wallet and a local node)

> User goal: check smeshing rewards, use wallet.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4847%3A3499&viewport=1595%2C884%2C0.14819887280464172&scaling=min-zoom)

1. App starts local node and if smeshing is set up, configures it to smesh.
1. App displays the `unlock wallet` screen.
1. User enters the wallet’s password to access it.
1. App displays the `main wallet` screen and syncs the mesh in the background.
1. User uses the wallet screen features.
1. User switches to `smeshing screen` to view smeshing status.

> User is only prompted to connect the Ledger device to his computer and open the Spacemesh Ledger App on it, when the user needs to sign a new transaction or when user selects to add a new account, and the wallet is a ledger wallet and not a standard one.

----

### Flow 6. Second User Session (Standard or Ledger Wallet via Public Api Service)

> User goal: Work with a wallet without running a full node.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4791%3A20985&viewport=543%2C411%2C0.15232324600219727&scaling=min-zoom)

1. App displays the `unlock wallet` screen.
1. User enters the wallet’s password to access it.
1. App displays the `wallet` screen and updates wallet data via the API,
1. User uses the `wallet` screen features
1. User switches to the `network` screen to view network status.

> User is only prompted to connect the ledger device and open the Spacemesh Ledger App on it, when the user needs to sign a new transaction or when the user selects to add a new account, and the wallet is a ledger wallet and not a standard one.

--------

### Flow 7. Creating a Ledger Wallet (using Local Node or Public Api Service)

> User goal: User has a standard wallet. He likes to use a Ledger device so sign spacemesh transactions. To achieve this he needs to create a new Ledger wallet.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4746%3A952&viewport=1054%2C534%2C0.0983254462480545&scaling=min-zoom)

1. App displays an `add new wallet` command in the `unlock wallet` screen.
1. User clicks on the `add new wallet` command.
1. App displays the `network selection` screen (local node or public api).
1. User chooses one of the options for the wallet (local or public).
1. App displays the `wallet setup` screen.
1. User selects to set up a ledger wallet.
1. App attempts to connect to ledger device using the sm ledger sdk.
1. If the App can't connect to Spacemesh App on a usb-connected ledger device, then it displays the `connect ledger device` screen and provides instructions on how to use ledger with spacemesh.
1. User opens the Spacemesh app on his ledger device and usb connects it to his computer.
1. App connects to the Spacemesh app on ledger via the sm ledger sdk.
1. App connects to a Spacemesh network via public api or starts a local node based on user selection above.
1. App displays the `wallet` screen.

---------

### Flow 8. Creating a new Standard Wallet (using Local Node or Public Api Service)

> User goal: Setup a new standard (hot) wallet to manage funds and vaults seperately than an existing wallet.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4847%3A79&viewport=1189%2C539%2C0.09597726166248322&scaling=min-zoom)

1. App displays an `add new wallet` command in the `uncock wallet` screen.
1. User clicks on the `add new wallet` command.
1. App displays the `wallet setup` screen (wallet+node or public api).
1. User chooses one of the options for the wallet (local or public).
1. App displays the `wallet setup` screen (standard or ledger).
1. User selects to set up a standard wallet.
1. App connects to a Spacemesh network via public api or starts a local node based on user selection above.
1. App displays the `wallet` screen.

--------

## Journeys with Multiple Wallets

In the flows below, the user has set up more than one wallet in previous app sessions.

### Flow 9. New App Session (more than one wallet)

> User goal: Access one of his previously created wallets and optionally start local node and smeshing.

This flow happens when more than one wallet was used in the App in a previous session.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4791%3A34669&viewport=805%2C511%2C0.16979332268238068&scaling=min-zoom)

1. App displays the `open wallet` screen. It lists all available wallets.
1. User selects a wallet from the screen.
1. If the wallet was configured to use a public API then the app configures itself to use this api.
1. If the wallet was configured to use a local node then the app configures itself to use a local node and starts it. If the user has setup smeshing then the app starts smeshing.
1. App opens the wallet and displays it on the `wallet screen`.

--------

### Flow 10. Switching Between Wallets

> User goal: quickly access one of the wallets he'd previously created.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4847%3A7372&viewport=533%2C562%2C0.15134163200855255&scaling=min-zoom)

1. User clicks on log-out in the main screen.
1. `New App Session` flow runs (above) from step 1.

--------

### Flow 11. Creating a new Vault

User goal: Create a new vault to safely store funds via multisig and ledger wallet support, and optionally set daily spending.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4818%3A18504&viewport=771%2C511%2C0.12224031984806061&scaling=min-zoom)

1. App displays drop-down next to wallet name in `wallet` screen with wallet commands.
1. User selects the `Add new Vault` command from the drop-down.
1. App starts the `new vault` flow (see Figma).

> New vault is added as an account to the wallet that the user is using in the `wallet` screen. It can be added to a standard or a Ledger wallets.

----------

### Flow 12. Adding an Existing Vault to a Wallet

User goal: Use an existing vault that may have been created by another wallet, by another user or by a Spacemesh network genesis flow.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4870%3A4888&viewport=-299%2C-151%2C0.24096724390983582&scaling=min-zoom)

1. User selects the 'Add existing Vault' command from the wallet's settings commands.
1. App starts the `add existing vault` flow (see figma).

-----------

### Flow 13. Accessing an Existing Vault

User goal: view vault's state (balance, pending transactions, etc...) and execute vault transactions.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=4904%3A15&viewport=-2525%2C1140%2C0.21393637359142303&scaling=min-zoom)

1. App displays an entry for each wallet's vault in the accounts drop down on the `wallet` screen.
1. User selects a vault from the drop-down.
1. App displays the vault's main screen and state.
1. User executes vault commands from the vault's screen.

-----------

### Flow 14. Withdrawing from a Simple Vault (without daily spending)

> For this and the following interactions, we assume the user has accessed a vault (see Flow 13 above) and it is displayed in the wallet screen.

User goal: send coins from a vault to another account.

[Interactive prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=5707%3A22305&viewport=236%2C-22%2C0.20278094708919525&scaling=min-zoom)

1. User clicks on the `Send` button in the wallet screen.
1. App displays the `Send SMH` screen with the `from field` set to the vault's single master account. App displays the amount available for Withdrawing - it is the vault's balance.
1. User specifies the destination account address, the coin amount, the transaction fee (gas units and gas unit price).
1. App validates that the amount to send + the transaction fees are equal or smaller than the vault's balance.
1. User clicks 'Send'
1. App displays the transaction summary screen.
1. User clicks 'Send'
1. App sends the transaction and displays the transaction sent screen.

-----------

### Flow 15. Withdrawing from a Simple Vault (with daily spending)
User goal: send coins from a vault to another account.

[Interactive prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=5707%3A19207&viewport=568%2C-111%2C0.22096964716911316&scaling=min-zoom)

1. User clicks on the `Send` button in the wallet screen.
1. App displays the select account screen. (See vault interactions figma page, screen #4).
1. User clicks on the `master account` button.
1. Flow continues from Flow 14, step 2.

-----------

### Flow 16. Withdrawing from a MultiSig Vault (without daily spending)

User goal: send coins from a vault to another account.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=5707%3A21426&viewport=-184%2C79%2C0.24070248007774353&scaling=min-zoom)

1. User clicks on the `Send` button in the wallet screen.
1. App displays the `Send SMH` screen with the `from field` set to the vault's single master account. App displays the amount available for Withdrawing - it is the vault's balance.
1. App displays a note regarding the required approval of one of the other master accounts owners (See vault interactions figma page, screen #5). User is encouraged to notify one of the other master accounts owner about the transaction.
1. User specifies the destination account address, the coin amount, the transaction fee (gas units and gas unit price).
1. App validates that the amount to send + the transaction fee are equal or smaller than the vault's balance.
1. User clicks 'Send'
1. App displays the transaction summary screen.
1. User clicks 'Send'
1. App submits the transaction to the transactions pool for processing, and displays the transaction sent screen.

> The flow continues on instances of Smapp in which the same vault has been added to a wallet. For multisig vaults, this will happen in Smapp of the 2 other master account owners.

1. User accesses the vault's account in the wallet screen.
1. App displays a `pending approval request` (see left side of screen #6 in Vault Interactions figma page).
1. User clicks on the 'review' button.
1. App displays the Send SMH review screen (Screen #6 in Vault Interactions figma page).)
1. User reviews the transaction and clicks 'Approve'.
1. App displays an approval transaction screen where the user can modify transaction fee (gas units and gas unit price).
1. User clicks 'Approve'
1. App submits the user-signed approval transactions to the transactions pool for processing and displays the transaction sent screen.

-----------

### Flow 17. Withdrawing from a MultiSig Vault (with daily spending)
User goal: send coins from a vault to another account.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=5707%3A24211&viewport=222%2C22%2C0.1997256726026535&scaling=min-zoom)

1. User clicks on the `Send` button in the wallet screen.
1. App displays the select account screen. (See vault interactions figma page, screen #4).
1. User clicks on the `master account` button.
1. Flow continues from Flow 16, step 2.

------------

### Flow 18. Daily Spending from a Vault.
> This flow assumes the user has set up daily spending on a simple or a MultiSig vault.

User goal: Send coins from daily spending account to any other account.

[Interactive Prototype](https://www.figma.com/proto/6bbFkIAzVu36bIpUNnMqoy/Smapp-Designs?node-id=5711%3A872&viewport=624%2C510%2C0.1901005655527115&scaling=min-zoom)

1. User clicks on the `Send` button in the wallet screen.
1. App displays the select account screen. (See vault interactions figma page, screen #4).
1. User clicks on the `Use daily spending` button.
1. App verifies that the wallet has the user's daily spending account (he needs to sign with that account in order to spend).
1. Flow continues from Flow 14, step 2 with the from account set to the daily spending account, and in the transaction screen the app validates that the amount that the user inputs is available for withdrawal in the current day. (User can only spend up to the daily spend amount every 24 hours).

> Note that if the user's daily spending account is specified in another wallet, then to daily spend, the user needs to add the vault to that wallet. In this flow we assumed that the current wallet has that account.

-----------

### Flow 19. Change daily spending limit - Simple Vault.

User goal: Change the daily spending amount.

1. User views a vault on the wallet's screen.
2. App is displaying the `edit` button in the `Daily spending limit` section if the wallet includes the vault's master key.
3. User clicks on `edit` in the `Daily spending limit` row.
4. App displays the `Daily Spending Limit` screen (screen 8 in figma).

> Note that the authorization info is not displayed as no authorization is required in a single vault.

5. User sets a new spending amount, provides gas units, gas unit price and clicks `next`.
6. App displays a confirmation screen with the transaction details (missing mock in figma - needs to be added).
7. User clicks `Approve`.
8. The app signs the change daily spending amount vault transactions and submits it to the network for processing.

------

### Flow 20. Change daily spend limit - Multisig Vault.

User goal: Change the daily spend amount.

1. User views a vault on the wallet's screen.
1. App is displaying the `edit` button in the `Daily spending limit` section if the wallet includes the vault's master key.
1. User clicks on `edit` in the `Daily spending limit` row.
1. App displays the `Daily Spending Limit` screen (screen 8 in figma).
1. User sets a new spending amount, provides gas units, gas unit price and clicks `next`.
1. App displays a confirmation screen with the transaction details (missing mock in figma - needs to be added).
1. User clicks `approve`.
1. The app signs the change daily spending amount vault transactions and submits it to the network for processing.

> The flow now continues on one of the other 2 master account holders' wallets in smapp.

1. User accesses a wallet with the vault's account in smapp.
2. App displays a `Pending approval request` button on the wallet's screen.
3. User clicks on `review` to display the request.
4. App displays the request (Screen #11 in figma).
5. User reviews the requests and clicks `approve`.
6. App signs the approval transaction, submits it to the network for processing and displays a transaction submitted notification in the status.

------

### Flow 21. Change daily spend account - Simple Vault.

User goal: Change the daily spend account.

1. User views a vault on the wallet's screen.
2. App is displaying the `edit` button in the `Daily spending account` section if the wallet includes the vault's master key.
3. User clicks on `edit` in the `Daily spending account` row.
4. App displays the `Daily Spending Account` screen (screen #10 in figma).

> Note that the authorization info is not displayed as no authorization is required in a single vault.

5. User sets up a new spending account, provides gas units, gas unit price and clicks `next`.
6. App displays a confirmation screen with the transaction details (missing mock in figma - needs to be added).
7. User clicks `Approve`.
8. The app signs the change daily spending amount vault transactions and submits it to the network for processing.

------

### Flow 22. Change daily spend account - Multisig Vault.

User goal: Change the daily spend account.

1. User views a vault on the wallet's screen.
1. App is displaying the `edit` button in the `Daily spending account` section if the wallet includes the vault's master key.
1. User clicks on `edit` in the `Daily spending account` row.
1. App displays the `Daily Spending Account` screen (screen #10 in figma).
1. User sets up a new spending amount, provides gas units, gas unit price and clicks `next`.
1. App displays a confirmation screen with the transaction details (missing mock in figma - needs to be added).
1. User clicks `approve`.
1. The app signs the change daily spending amount vault transactions and submits it to the network for processing.

> The flow now continues on one of the other 2 master account holders' wallets in smapp.

1. User accesses a wallet with the vault's account in smapp.
2. App displays a `Pending approval request` button on the wallet's screen.
3. User clicks on `review` to display the request.
4. App displays the request (Screen #11 in figma).
5. User reviews the requests and clicks `approve`.
6. App signs the approval transaction, submits it to the network for processing and displays a transaction submitted notification in the status.

-----------

## The Journey - Technical View


## Entities

### Testnet Config File
A full node config file describing a Spacemesh Testnet. Required to connect to a testnet. Currently 1 config file embedded in Smapp. We'd like to enable users to use Smapp to connect to different Testnets without having to use a new version of Smapp. The config file specifies a network unique id. To connect to a Testnet, a user needs to obtain its config file and save it in a designated location for Smapp to be able to identify it on startup.

### Mainnet Config File
A minimal config file which includes mainnet network id. It is used to create wallets for use on mainnet pre-genesis. Before genesis, a mainnet full config file will be provided and users need to download it and use it to connect to the Mainnet. The full config file will replace the minimal one.

### Wallet File
A wallet data file. Includes wallet and contacts information. Used by both hot wallets and ledger wallets. Private data in this file is always encrypted with the user's provided password. Each wallet must have a data file that specifies it. So users will have a wallet file for each wallet they create in smapp.

### Wallets File
A simple data file which contains a list of user's wallet data files and the location of the data file for each such wallet. This enables users to access any wallet in Smapp. Smapp can only work with one wallet at a time.
If this file is getting corrupted or deleted then the user will just need to restore wallets (from paper backup or backup file) to be able to work with them. Path to a restored wallet's data file is added to the Wallets file.

### Public API Web Service
A web service providing the Spacemesh API over the Internet. The service is using its own managed nodes to connect to the Spacemesh network. A wallet can use this API instead of using an API provided by a local running node.

----

![](/resources/wallets_usage_flows.png)
