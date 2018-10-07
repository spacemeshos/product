# Spacemesh Product Plan

## Overview

Our short-term high-level product plan is to build [MVP1](mvp1.md) and [MVP2](mvp2.md) and release testnets and mainnets for this products according to the project [roadmap](https://github.com/spacemeshos/go-spacemesh/wiki/Roadmap).I

Our long-term high-level product plan is to implement, test and roll-out additional capabilities and features to the platform in subsequent incremental releases until the full platform is released as `Spacemesh 1.0` with support to all the main use cases outlined here.

Incremental product releases, starting with `Spacemesh 0.1` are deployed to testnets first for testing and to the `Spacemesh Mainnet` once they reach production quality status.

---

## Spacemesh 0.1 (MVP1)

### Release Highlights

The main use case case of MVP1 is to support [Spacemesh Coin](spacemesh_coin.md) cryptocurrency transactions between anyone and to award `Spacemesh coins` to validators who run full Spacemesh nodes with their PCs on the Spacemesh mainent. The Spacemesh full node implements the Spacemesh consensus protocol and other protocols to support this use case.

The main goal of this release is to provide a basic working version of a permissionless and trustless Internet money that is secure, decentralized and scalable without using POW or PoStake mechanisms.

### Release main software components

### Use cases
- [Available here](mvp1.md)

1. [go-spacemesh](https://github.com/spacemeshos/go-spacemesh) - Reference implementation of the Spacemesh full node in go-lang for all major PC OSes

2. [Spacemesh POET service](https://github.com/spacemeshos/POET) - a public utility used in the Spacemesh proofs of space time protocol

3. [Spacemesh App](https://github.com/spacemeshos/app) - Spacemesh Wallet and Network Dashboard

4. `Spacemesh Gateway` - Foundation deployed nodes providing the `Spacemesh API` over https-json

5. [Spacemesh API](https://github.com/spacemeshos/go-spacemesh/wiki/spacemesh-api) - The common API provided by gateways and full nodes

6. [Spacemesh Tap](tap.md) - Allows users to get `Spacemesh Coins` on testnets for testing purposes

---

## Release 0.2 (MVP2)

### Release Highlights
The main goal of this release is to add smart contracts capabilities to the Spacemesh platforms. The main new feature of MVP2 is [smart contracts](https://github.com/spacemeshos/go-spacemesh/wiki/Smart-Contracts) support.

In additional to MVP1 functionality, MVP2 enables developers to code, test, deploy and update smart contracts on the Spacemesh global computer and for users to interact with smart contracts using smart contract transactions.

We'd like to build a modern wasm-based VM with `Rust` or `Typescript` as the main smart contracts supported programming languages.

### Release features and components
1. Spacemesh smart contracts dev tools to support devs workflow
2. `Spacemesh full node`, `Spacemesh API` and `Spacemesh Gateway` updates to support smart contract transactions and reading programs state

### Use cases
- [Available here](mvp2.md)

---

## Release 0.3

### Release Highlights
This release enables developer to build `Spacemesh Powered Apps`. Apps the interact with the Spacemesh global computer. e.g. users can execute app-related transactions and read apps related smart contracts state.

In addition support for many-to-many payments and app micropayments with both `Spacemesh Coins` and tokens is added to the platform.

We also introduce an improved user experience for working with dapps on any platform without having to ship a browser extension for web based dapps.

### Main new features
1. `Payment channels` - user-to-user, app-to-user and user-to-app `Spacemesh Coins` and tokens transactions support

2. `Spacemesh SDK` - an SDK for building Spacemesh apps

3. `Spacemesh Wallet App` - mobile native distribution supporting a unified workflow for signing transactions in any dapp on any platform

### New components
1. `Spacemesh full node`, `Spacemesh API` and `Spacemesh Gateway` updates to support payment channels

2. `Spacemesh SDK` - A Javascript npm library for node.js server apps and client-side web apps

3. `Spacemesh Wallet app` - a mobile native for Android and iOS that enables users to log-in to their wallet using the device's bio authentication capabilities and to sign transactions initiated on any dapp with the wallet

4. `Spacemesh Web Service` - a web service that is used in the new transaction signing workflow

### Use cases
1. App publisher adds `Spacemesh Coins` features to its web app

2. App publisher adds token-based functionality to its web app

3. User installs the `Spacemesh Wallet App` on his mobile device and uses his device bio auth capabilities (finger thumb detection, face detection, etc...) to log into the App

4. User uses a `Spacemesh powered apps` on any Internet enabled platform and signs transactions using his `Spacemesh Wallet App`

  - User provides his public wallet address to a `Spacemesh Powered App`
  - To preform a transaction (offchain or onchain), the app sends a transaction meta-data to a web service
  - The `Spacemesh Web service` pushes a notification to the user's mobile wallet
  - User receives the notification on his mobile device and taps to review it
  - `Spacemesh Wallet App` is opened, user signs-in to it using a bio auth method, and the app presents the transaction details
  - User reviews and authorizes the transaction
  - The `Spacemesh Wallet App` sends the signed transaction to the `Spacemesh Web Service`
  - The `Spacemesh Powered App` receives the signed transaction and executes it (onchain or offchain)

----

## Release 1.0

### Release Highlights
This 1.0 release extends the payment channels capabilities to generalized state channels. This enables apps to offload some or all of users app state from the Spacemesh blockmesh or from the cloud, to achieve greater scale and faster performance while not sacrificing security and users data privacy.

### Release features and components
1. `Generalized state channels` - offload app state from the blockmesh

2. `Spacemesh full node`, `Spacemesh API`, `Spacemesh Wallet` and `Spacemesh Gateway`, `Spacemesh SDK` updates to support state channels

### Use cases
1. App publisher adds support for managing user state in their App using the `Spacemesh SDK`

2. User manage their app's off-chain state directly in a `Spacemesh powered app` or using the `Spacemesh Wallet`

----

## Discussion Items

- Support for anon transactions

----
## Additional resources and specifications
- [Spacemesh API](https://github.com/spacemeshos/go-spacemesh/wiki/spacemesh-api)
- [Spacemesh Full Node](https://github.com/spacemeshos/go-spacemesh)
- [Spacemesh Wallet](https://github.com/spacemeshos/app/wiki/wallet)
- [Spacemesh App](https://github.com/spacemeshos/app)
- [Spacemesh POET](https://github.com/spacemeshos/poet)
- `Spacemesh SDK` - A Javascript npm library to integrate Spacemesh into any app. Uses the Spacemesh Gateway as API provider.
- `Spacemesh Gateway` - a public https-json web service providing the Spacemesh API to any client that can speak https-json
- `Spacemesh API Provider` - A software component providing the Spacemesh API over a well defined endpoint.
- `Spacemesh powered apps` - An apps that allows users to use Spacemesh functionality and to sign Spacemesh transactions.

### Testnets & Mainnet
- All releases be deployed to testnets for testing, bug fixing and audits purposes before going live on the Spacemesh mainent
- Once we are satisfied with the level of security and robustness of a release, we will release it to mainent.
