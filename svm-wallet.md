# Overview
A contract wallet abstraction implemented in SVM.

# Core Use Cases
1. Create an on-mesh spending wallet with a hardware-wallet master key or a multi-sig master key.
2. Set daily spending limit.
3. Recycle a lost spending key.

# Requirements
1. Support for spending key recycling, a hardware wallet and/or multi-sig master key and daily spending limit.
2. Support funds vesting. Enforces spending rules over time based on wallet instance params.
1. Don't duplicate code for each wallet instance - use code templates.
2. Users interact with wallet using smart contract transactions.
3. Save wallet instance state in SVM storage trie.
