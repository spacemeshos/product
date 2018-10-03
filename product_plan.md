## Overview

Our short-term high-level product plan is to build [MVP1](mvp1.md) and [MVP2](mvp2.md) and release testnets and mainnets for this products according to the project [roadmap](https://github.com/spacemeshos/go-spacemesh/wiki/Roadmap).

Our longer-term high-level product plan is to implement, test and roll-out additional capabilities and features to the platform in subsequent incremental releases until the full platform is released as `Spacemesh 1.0` with support to all the main use cases outlined here.

---

## Spacemesh 0.1 (MVP1)

The main use case case of MVP1 is to support [Spacemesh Coin](spacemesh_coin.md) cryptocurrency transactions between anyone and to award Spacemesh coins to validators who run full Spacemesh nodes on the Spacemesh mainent. The full node implements the Spacemesh consensus protocol and other protocols to support this use case.

The main goal of this release is to provide a basic working version of a permissionless and trustless Internet money that is secure, decentralized and scalable without using POW or PoStake.

### Release main software components

1. [go-spacemesh](https://github.com/spacemeshos/go-spacemesh) - Reference implementation of the Spacemesh full node in go-lang.
2. [Spacemesh POET service](https://github.com/spacemeshos/POET)
3. [Spacemesh App](https://github.com/spacemeshos/app) - Wallet and Dashboard
4. `Spacemesh Gateway` - Foundation deployed nodes providing the `Spacemesh API` over https-json and
5. [Spacemesh API](https://github.com/spacemeshos/go-spacemesh/wiki/spacemesh-api) - The common API provided by gateways and full nodes
6. [Spacemesh Tap](tap.md) - Allows users to get `Spacemesh Coins` on testnets

### Main use cases
- [Available here](mvp1.md)

---

## Release 0.2 (MVP2)

The main goal of this release is to add smart contracts capabilities to the Spacemesh platforms.

The main new feature of MVP2 is [smart contracts](https://github.com/spacemeshos/go-spacemesh/wiki/Smart-Contracts) support.

In additional to MVP1 functionality, MVP2 enables developers to code, test, deploy and update smart contracts on the Spacemesh global computer and for users to interact with smart contracts using smart contract transactions.

We'd like to build a modern wasm-based VM with `Rust` or `Typescript` as the main smart contracts supported programming languages.

### Release features and components
1. Spacemesh smart contracts dev tools
2. `Spacemesh full node`, `Spacemesh API` and `Spacemesh Gateway` updates to support smart contract transactions and reading programs state

### Use cases
- [Available here](mvp2.md)

---

## Release 0.3

### Main new features
- `Payment channels` - user-to-user, app-to-user and user-to-app `Spacemesh Coins` and tokens transactions support
- `Spacemesh SDK` - an SDK for building Spacemesh apps
- 'Spacemesh browser extension' - providing the `Spacemesh API` to html5/javascript apps which run in the browser.

### Release new components
- `Spacemesh full node`, `Spacemesh API` and `Spacemesh Gateway` updates to support payment channels
- `Spacemesh SDK` - A Javascript npm library for node.js server apps and client-side web apps

### Use cases
1. App publisher adds `Spacemesh Coins` features to its app
2. App publisher adds token-based functionality to its app
3. User install the Spacemesh Browser Extension to enable Spacemesh powered apps
4. User uses `Spacemesh powered apps` and sign transactions using the `Spacemesh browser extension`

These use cases will be implemented by the `Spacemesh SDK` and the `Spacemesh browser extension`.

----

## Release 1.0

### Release features and components
- `Generalized state channels` - offload app state from the blockmesh
- `Spacemesh full node`, `Spacemesh API`, `Spacemesh Wallet` and `Spacemesh Gateway`, `Spacemesh SDK` updates to support state channels

### Use cases
1. App publisher adds support for managing user state in their App
2. User can manage their app's off-chain state using the `Spacemesh Wallet`

----

## Open Issues for Discussion

- Support for anon transactions

----
## Additional Resources and  specifications

- [Spacemesh API](https://github.com/spacemeshos/go-spacemesh/wiki/spacemesh-api)

- [Spacemesh Full Node](https://github.com/spacemeshos/go-spacemesh)

- [Spacemesh Wallet](https://github.com/spacemeshos/app/wiki/wallet)

- [Spacemesh App](https://github.com/spacemeshos/app)

- [Spacemesh POET](https://github.com/spacemeshos/poet)

- `Spacemesh SDK` - A Javascript npm library to integrate Spacemesh into any app. Uses the Spacemesh Gateway and the Spacemesh Browser Extension as API providers.
- `Spacemesh Gateway` - a public https-json web service providing the Spacemesh API to any client that can speak https-json

- `Spacemesh API Provider` - A software component providing the Spacemesh API over a well defined endpoint.

- `Spacemesh Browser Extension` - A standard browser extension providing the Spacemesh API to web applications and allowing users to securely sign transactions generated by apps.

- `Spacemesh powered apps` - An apps that allows users to use Spacemesh functionality and to sign Spacemesh transactions.

### Testnets & Mainnet
- All releases be deployed to testnets for testing, bug fixing and audits purposes before going live on the Spacemesh mainent
- Once we are satisfied with the level of security and robustness of a release, we will release it to mainent

As we are a developers first org and an open source projects, all product plans and specifications are in our [github repos](https://github.com/spacemeshos). So please head over to github using the links above to learn more about the use cases, the roadmap and more details product plans.
