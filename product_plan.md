# Spacemesh Product Plan

## The main problems that Spacemesh aims to solve
1. Cryptocurrency fair global distribution
2. Cryptocurrency as a global means of payment
3. Censorship from participating in a fair, global and open monetary system
4. Distributed apps are too hard to develop and to be used by everyday people
5. Issues involved in Proof of Work based consensus mechanisms, mining pools and ASIC mining
6. Issues involved in Proof of Stake based consensus mechanisms

## Overview

Our short-term high-level product plan is to build [Spacemesh 0.1](spacemesh01.md), release an open public testnet, follow-up with `Spacemesh 0.x` releases testnet updates and launch a mainnet according to the project [roadmap](roadmap.md).

Our long-term high-level product plan is to implement, test and roll-out additional capabilities and features to the platform in subsequent incremental releases until the full platform is released as `Spacemesh 1.0` with support to all the main use cases outlined here.

Incremental product releases, starting with `Spacemesh 0.1` will be deployed to testnets first for testing and to the `Spacemesh Mainnet` once they reach production quality level and have been security audited.

## TL;DR

![](https://raw.githubusercontent.com/spacemeshos/product/master/resources/roadmap2019.png)

---

## Spacemesh 0.1

### Release Highlights

The main use case case of `Spacemesh 0.1` is to support [Spacemesh Coins](spacemesh_coin.md) cryptocurrency transactions between any two parties and to award `Spacemesh coins` to people who run full Spacemesh full p2p nodes on their PCs. The Spacemesh full node implements the [Spacemesh consensus protocol 1.0](https://spacemesh.io/spacemesh-protocol-v1-0/) and other protocols to support this use case.

The main goal of this release is to provide an MVP of a permissionless and trustless Internet money that is secure, decentralized and scalable without using POW or PoStake mechanisms.

### Use Cases
- [Available here](spacemesh01.md)

### Visual Story
![Story](https://raw.githubusercontent.com/spacemeshos/product/master/resources/sm_0.1_story.jpg)

### Release Main Components

1. [go-spacemesh](https://github.com/spacemeshos/go-spacemesh) - The reference implementation of the Spacemesh full node in go-lang for Windows 10, OS X and Linux.

2. [Spacemesh POET service](https://github.com/spacemeshos/POET) - a public utility used in the Spacemesh proofs of space time protocol.

3. [Spacemesh App](https://github.com/spacemeshos/smapp) - A desktop app for Windows 10, OS X and Linux which includes a Wallet, a managed full p2p node and mining.

4. `Spacemesh Gateway` - Foundation deployed node(s) providing the `Spacemesh API` for wallets and for the app to check coin balance, and execute transactions. We call this wallet-only app mode.

5. [Spacemesh Tap](tap.md) - Enables users to get Testnet `Spacemesh Coins` for testing purposes.

6. [Spacemesh POST](https://github.com/spacemeshos/post) - A component implementing the proofs of space protocol used by Spacemesh full nodes.

### App Users Guide
[Spacemesh Testnet guide](https://testnet.spacemesh.io/#/dict)

---

## Spacemesh 0.x
0.x releases are going to include bug fixes, updates and additional features for testing on the public testnet prior to mainanet launch. The mainnet will be launched once we are comfortable with the quality, security and performance of a 0.x release.

---

## Spacemesh 1.0

### Release Highlights
The main goal of this release is to add `smart contracts capabilities` to the Spacemesh platform.

The main new feature of Spacemesh 1.0 is smart contracts support enabled by the [Spacemesh Virtual Machine](https://github.com/spacemeshos/svm).

In additional to Spacemesh 0.x features and improvements to these features, Spacemesh 1.0 will enable developers to code, test, deploy and update smart contracts on the Spacemesh global computer and for users to interact with deployed smart contracts using smart contract transactions.

We are building modern [wasm-based](https://webassembly.org/) VM and a programming language called `SMESH` as the main smart contracts supported programming languages.

### Release features and components
1. Spacemesh smart contracts dev tools to support various devs workflow and the Smesh programming language

2. `Spacemesh full node`, `Spacemesh API` and `Spacemesh Gateway` updates to support smart contract transactions and reading smart contracts blockmesh state

3. `Spacemesh Wallet` updates to supports interacting with smart contracts - reading smart contract state and executing smart contract transactions

### Use cases
- Coming soon
---
