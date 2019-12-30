# Overview
A contract wallet abstraction implemented in SVM.

# Core Use Cases
1. Create an on-mesh spending wallet with a single hardware-wallet master key or a multi-sig master key (where zero or more keys can be a hardware-wallet keys).
2. Set daily spending limit and have them enforced by the wallet.
3. Recycle a lost spending key using master key.
4. View vested and unvested coin balance.
5. Transfer up to the vested wallet balance from the wallet to another account or wallet.

# Requirements
1. Support for spending key recycling, a hardware wallet and/or multi-sig master key and daily spending limit.
2. Support funds vesting. Enforces spending rules over time based on wallet instance params.
3. Don't duplicate code for each wallet instance - use code templates.
4. Users interact with wallet using smart contract transactions.
5. Save wallet instance state in SVM storage trie.
6. Reference Spacemesh desktop wallet should add support for svm-wallet. e.g. users should be able to interact with an svm-wallet instance via the Spacemesh app UI.
