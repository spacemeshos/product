# testnet-tap

A [Smesh Coins](spacemesh_coin.md) tap for open testnet users

## overview
A Discord bot and a public API providing a way for nodes to obtain testnet `Smesh Coins`.

## Basic Use Case
1. Receive a Spacemesh account public address from a user in the [tap Discord channel](https://discord.gg/ASpy52C)
2. Issue 2 Spacemesh Coins (SMC) to the account's address

## Requirements

### User Input Validation
1. Validate public account id string format.
2. Enforce a cooldown period - don't issue coins to the same account more frequently than once every 24 hours.

### Logging
- Log each requested tap request

## Design Notes
- A similar gitter-channel based implementation is working here for the Kovan testnet: https://gitter.im/kovan-testnet/faucet
- Tap backend should include a go-spacemesh full node and a CLI wallet that has the private key for a genesis-defined account with a large balance. To issue coins, the backend should use the wallet to sign transactions and submit it to the full node instance.

## Dependencies
- Functional CLI walelt with an API to sign coin transactions.

