# Overview
SVM-wallet is contract wallet abstraction implemented in SVM and available for users on the Spacemesh platform.

# Use Cases
1. Create an on-mesh spending wallet with a single hardware-wallet master key or a multi-sig master key (where zero or more keys can be a hardware-wallet keys).
2. Set daily spending limit and have them enforced by the wallet.
3. Recycle a lost spending key using master key.
4. View vested and unvested coin balance.
5. Transfer up to the vested wallet balance from the wallet to another account or wallet.
6. Provide investors and builders with a way to get their coins.

# Requirements
1. Support for spending key recycling, a hardware wallet and/or multi-sig master key and daily spending limit.
2. Support funds vesting. Enforces spending rules over time based on wallet instance params.
3. Don't duplicate code for each wallet instance - use code templates.
4. Users interact with wallet using smart contract transactions.
5. Save wallet instance state in SVM storage trie.
6. Reference Spacemesh desktop wallet should add support for svm-wallet. e.g. users should be able to interact with an svm-wallet instance via the Spacemesh app UI.
7. Support pre-compiled instances with a pre-set balance, master key(s), and vesting params.
8. Receive funds from any other wallet or user coin account via a smart contract transaction.

## Wallet properties
- Total balance (managed by the wallet)
- Available balance - funds available for withdrawals.
- Master key(s) - 1 key for single master, n keys for multi-sig. Need to support 2 out of 3 only multi-sig.
- Vesting enabled - true or false.
- Daily spending limit.
- Spending public key(s) - changeable by owner of master key.

### Vesting Properties
This read-only properties are set for a vesting-enabled wallet. All of these properties must be set at wallet instantiation time and can't be changed later by anyone.

1. Vesting start time. e.g. a layer # from genesis.
2. Vesting start amount. e.g. 3000 coins. The amount that can be withdrawn at the vesting start time.
3. Vesting period. The time period in which vesting withdrawals can be made starting with the first vesting period after the vesting start timestamp. e.g. 1 cal month in num of layers.
4. Vesting period amount. e.g. 500 coins. The amount that can be drawn by the end of each vesting period.

For example, key owner of a vesting wallet may withdraw the the `vesting start amount` on or after the `vesting start time`. On or after the time of the `vesting start time` plus the `vesting period` he may withdraw the vesting period amount.

### Wallet Instantiation

We need to support 2 main instances types:
1. Pre-compiled instances: Instances pre-compiled into the SVM storage trie at genesis.
2. User-instantiated instances: Instances created by users via a smart contract transactions.

For user-instantiated wallets, all properties must be set at creation time in the instantiation transaction.
