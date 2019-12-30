# Overview
A contract wallet abstraction implemented in SVM. 

# Core Use Cases
1. A spending user wallet with support for spending key recycling, a hardware wallet and/or multisig master key and daily spending limit.
2. Support funds vesting. Enforces spending rules over time based on wallet instance params.

# Requirements
1. Don't duplicate code for each instance - use code templates.

