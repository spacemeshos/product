# testnet-tap

A [Spacemesh Coins](spacemesh_coin.md) tap for open testnet users

## overview
A Discord bot and a public API providing a way for nodes to obtain `Spacemesh Coins` on the `Spacemesh testnet`

## Basic Use Case
1. Receive a Spacemesh account public address from a user in a Discord channel
2. Issue 2 Spacemesh Coins (SMC) to the account address

## User Input Validation
1. Validate public account id string format
2. Cool down - don't issue coins to the same account more frequently than one in 24 hours

## Design Notes
- A similar gitter-channel based implementation is working here for the Kovan testnet: https://gitter.im/kovan-testnet/faucet
- Implement logic to only execute a request every 7 seconds (tap frequency) and a queue to queue up all verified client requests. Log to server logs each executed tap request. Do not issue coins to the same address more than once every 24 hours

## Resources
- A Web-based tap [skeleton](https://github.com/spacemeshos/testnet-tap)
