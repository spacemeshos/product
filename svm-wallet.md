# Overview

SmeshCash is a flexible, smart contract-based multisig wallet implemented in SVM and available to all users on the Spacemesh platform.

# Use Cases

1. Create an on-mesh spending wallet with a single master key or multiple master keys (any of these keys can be hardware-wallet keys).
1. Generation of any number of replaceable "spending keys." These spending keys can be burned at any time, or replaced if lost, by the master key.
1. Daily spending limits enforced by the wallet: master spending limit, and per-key spending limit.
1. View vested and unvested coin balance.
1. Transfer up to the vested wallet balance from the wallet to another account or wallet.
1. Provide investors and builders with a way to track vesting and get their coins.

# Requirements

1. Support for spending key recycling, multi-sig master key, and daily spending limit.
1. Support funds vesting. Enforces spending rules over time based on wallet instance params.
1. Don't duplicate code for each wallet instance - use code templates.
1. Users interact with wallet using smart contract transactions and gasless "quasi transactions" (that don't change state).
1. Save wallet instance state in SVM storage trie.
1. Reference Spacemesh desktop wallet supports for SmeshCash. e.g. users should be able to interact with a wallet instance via the Spacemesh app UI.
1. Support pre-compiled instances with a pre-set balance, master key(s), and vesting params.
1. Receive funds from any other wallet or user coin account via a smart contract transaction.

## Wallet properties

- Total balance managed by the wallet.
- Balance funds available for withdrawals out of the total balance.
- Master key(s) - 1 key for single master, n keys for multi-sig. Need to support m-of-n multi-sig.
- Vesting enabled - true or false.
- Daily spending limit - changeable by owner master key(s).
- Spending public key(s) - changeable by owner of master key(s). Master key owner can retire old keys at any time and add new ones.

### Vesting Properties

This read-only properties are set for a vesting-enabled wallet. All of these properties must be set at wallet instantiation time and can't be changed later by anyone.

1. Vesting start time. e.g. a layer # from genesis.
2. Vesting start amount. e.g. 3000 coins. The amount that can be withdrawn at the vesting start time.
3. Vesting period length. The time period in which vesting withdrawals can be made starting with the first vesting period after the vesting start timestamp. e.g. one calendar month (specified in num of layers).
4. Vesting period amount. e.g. 500 coins. The amount that can be drawn by the end of each vesting period.

For example, key owner of a vesting wallet may withdraw the the `vesting start amount` on or after the `vesting start time`. On or after the time of the `vesting start time` plus the `vesting period` they may withdraw the vesting period amount.

### Wallet Instantiation

We need to support 2 main instances types:
1. Pre-compiled instances: Instances pre-compiled into the SVM storage trie at genesis.
2. User-instantiated instances: Instances created by users via a smart contract transactions.

For user-instantiated wallets, all properties must be set at creation time in the instantiation transaction.
