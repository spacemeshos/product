# Ledger Hardware Wallet Support in Smapp

## Motivation
We would like to empower users to use a Ledger hardware wallet to sign Spacemesh transactions via Smapp.

## Design Direction
- A Smapp wallet can be a standard hot-wallet (what we have working today) or a Ledger wallet - a wallet which is managed in Smapp but signing transactions is done on the Ledger hardware device. This is a cleaner direction than mixing hot and cold wallets functionality in one wallet.
- Allow users to create multiple wallets and to switch easily between wallets.

## Working with Ledger Wallets in Smapp

- Smapp will include the `Spacemesh Ledger App SDK`. A javascript library with interface to the Ledger app.
- User can create a Ledger wallet or a hot wallet in smapp and easily switch between standard wallets and a ledger wallet.
- For the first release, user can only have one ledger wallet per ledger device he owns. This is consistent with the way ledger apps work - each app has 1 secret seed which is used to derive keys securely on the hardware device.

### New Ledger Wallet Setup

1. User is expected to install the `Spacemesh Ledger App` on his ledger device via `Ledger Live` App or by other install flows.

2. when using smapp for the first time - user is prompted to select the type of wallet he'd like to setup.

![](https://raw.githubusercontent.com/spacemeshos/product/master/resources/ledger_wallet/smapp_create_new_wallet.png)

3. After selecting a new ledger wallet, user is prompted to connect his ledger device via USB to his computer and open the Ledger app on the device.

![](https://raw.githubusercontent.com/spacemeshos/product/master/resources/ledger_wallet/smapp_connect_ledger_device.png)

4. The Ledger wallet is displayed in Smapp and it has one or more accounts similar to a standard hot wallet.

![](https://raw.githubusercontent.com/spacemeshos/product/master/resources/ledger_wallet/smapp_sign_with_ledger.png)

- Each account is an account on the ledger device and user can access additional accounts (create account in smapp jargon).

- A wallet data file is maintained via smapp on the computer for the Ledger wallet. It doesn't contain a seed but it is password protected and includes contacts, number of accounts created, named accounts, the bip32 path of each account on the ledger device, etc...

- When executing a transaction in smapp for an account which is a ledger account, the user is prompted to review the transaction information and sign it on the ledger device. Smapp is using the spacemesh ledger sdk to community with the ledger ap on the device to implement this feature.

5. When user signs a transaction on ledger Smapp displays a confirmation screen about transaction being signed and submitted to the network for processing.

![](https://raw.githubusercontent.com/spacemeshos/product/master/resources/ledger_wallet/smapp_ledger_tx_submitted.png)
