
# testnet-tap
[Spacemesh](https://github.com/spacemeshos/go-spacemesh) testnet tap (Faucet) web app and API.

## overview
A gitter bot and a public API providing a way for nodes to obtain `Spacemesh Coins` on the `Spacemesh testnet`.

## Basic Use Case
1. Receive a Spacemesh account public address from a user in a gitter channel
2. Issue 2 Spacemesh Coins (SMC) to the account address


## User Input Validation
1. Validate public account id string format
2. Cool down - don't issue coins to the same account more frequently than one in 24 hours

## Design Notes
- Detailed information regarding how to create a Gitter node.js chat bot: https://github.com/gitterHQ/node-gitter
- A similiar implementation is working here for the Kovan testnet: https://gitter.im/kovan-testnet/faucet
- Mock use of a HTTPS/JSON API to a Spacemesh full node or to a Spacemesh HTTPS gateway. In production, the server will sign a transaction from the tap account to issue coins to the requester.
- Implement logic to only execute a request every 7 seconds (tap frequency) and a queue to queue up all verified client requests. Log to server logs each executed tap request. Do not issue coins to the same address more than once every 24 hours.

## Implementation Notes
- Add integration tests of the basic use case and the validation logic
- You should implement the server side logic without using a persistent data store by utilizing node.js / express capabilities so it can be deployed in a self contained manner without needing an external db.
