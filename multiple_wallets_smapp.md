# Design Notes: Multiple Wallets and Ledger Wallets in Smapp

## Multiple Wallets Features

### Motivation
With the addition of Ledger wallets to smapp it is becoming important to enable users to easily switch between the wallets they have created w/o having to restore a wallet into smapp.

### Smapp Wallets Functionality
1. When creating a wallet, ask the user to provide the type of the wallet - Ledger wallet or standard wallet (hot wallet) - see Ledger wallet below.

2. User can create a new wallet from the settings. New wallet can be standard wallet or ledger wallet.

3. User should be able to switch between any wallet he'd previously created by his smapp instance from the settings.

4. User should be able to add a wallet to his wallets from file (similar to restore but just adds the wallet to available wallets in the app).

5. Each wallet should still be backed by a wallet data file. Ledger wallets also have a password protected wallet file but not encrypted random seed in the file. The random seed is maintained on the ledger device, in the Spacemesh Ledger App.

6. When more than 1 wallet is available, on app startup, user is prompted to chose with what wallet he'd like to work with in this app's session. He can always switch it via the settings later.

7. To set a rewards address backed by hardware wallet security - user is expected to use a Ledger Wallet and set one of its addresses as its smesher rewards address.

## Wallet Account Types
Each wallet can have multiple accounts. There are two types of accounts we should support:
1. Standard accounts - derived from the wallet's random seed.
2. Vault accounts - a vault account is an abstraction that is backed by an on-mesh smart wallet instance.

Both ledger wallets and standard hot wallets should support vault accounts. Vault accounts do not have a bip32 path - they are just a collection of meta-data on vault on-chain instances. When using a vault account from a ledger wallet, signing transactions is done via ledger. When using a vault account from a standard wallet, signing transactions is done by smapp. Any wallet account can be used to sign messages for the same wallet's vault account.
