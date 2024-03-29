# Spacemesh Local Testnet (Localnet)

- [github repo](https://github.com/spacemeshos/local-testnet)
- [Releases] (https://github.com/spacemeshos/local-testnet/releases)

## Intro
Localnet is designed for developers who want to run a fully functional Spacemesh p2p networks on their computers for testing, evaluation and development purposes.

There are 2 main ways to run a localnet.
1. Run a localnet which uses binary releases of Spacemesh software components (built on github from Spacemesh open source software, and published to dockerhub).
2. Run a localnet which uses locally built components from source code.

<br/>

A functional Spacemesh network includes 3 main components:
1. [go-spacemesh full p2p nodes](https://github.com/spacemeshos/go-spacemesh). Each node participates in the consensus protocol and mines new blocks (we call this smeshing). Each node also provides a GRPC API you can use to submit transactions, view node settings and change node settings.
1. [Poet Service](https://github.com/spacemeshos/poet). This is a proofs of elapsed time service that is used by the full nodes as part of Spacemesh's proof of space time protocol. A network only need one instance of this service to operate.

1. [Smrepl](https://github.com/spacemeshos/smrepl). An open-source terminal wallet. You connect an instance of smrepl to any of your localnet go-spacemesh nodes. Use smrepl to submit transactions to the network via a node, check network and node status, check account balances, and modify any full node runtime behavior.

> go-spacemesh, Poet and smrepl are fully open source. You can use binary releases for your platform from each component github repo, or build them locally on your computer.

When you run a localnet with the default settings, specific DockerHub releases of Poet and go-spacemesh components are used. However, you can easily modify this to use locally built components from source code.

## Localnet Prerequisites

- macOS (x86-64 or ARM/M1) or Linux (Windows 10 is not yet supported)
- Docker
- Docker Compose
- NPM

## About spacemesh-local-testnet

`spacemesh-local-testnet` is an NPM package published to NPM. Use it to create and start a localnet, and to stop and delete a running localnet.

> The package is fully open source and the source code is available [here](https://github.com/spacemeshos/local-testnet).

When you run `spacemesh-local-testnet` without any custom options, it uses sensible defaults that have been tested to work. You can customizable these settings to override the default network configuration and behavior.

## Installing spacemesh-local-testnet

```
npm install -g spacemesh-local-testnet
```

## Running a Localnet

To create and start a local network using the default settings run:

```bash
spacemesh-local-testnet create
```

To stop and delete a running network run:

```bash
spacemesh-local-testnet delete
```

## Running a Localnet with custom settings

You can change a local network default settings and determine which go-spacemesh and Poet components binaries to use in your network. To see available options enter:

```bash
spacemesh-local-testnet --help
```

## Running a Localnet with locally-built go-spacemesh nodes

1. Clone the [go-spacemesh github repo](https://github.com/spacemeshos/go-spacemesh) to your computer.
2. Run the following command in your cloned repo root directory to build a local docker image of go-spacemesh from source code:

```bash
docker build -t spacemesh:local .
```

Use the `-go-sm-image` argument to use your locally built image in a new localnet. For example:

```bash
spacemesh-local-testnet create --go-sm-image=spacemesh:local
```

### Running a localnet with a locally-built PoET service

First, clone the [PoET github repo](https://github.com/spacemeshos/poet) to your computer.

Next, run the following command in your PoET cloned repo root directory to build a local docker image of PoET from source code:

```bash
docker build -t poet:local .
```

Use the `poet-image` argument to use your locally built PoET service in your localnet. For example:

```bash
spacemesh-local-testnet create --go-sm-image=spacemesh:local --poet-image=poet:local
```


## Connecting to Node's API Services

By default, each node provides a `Spacemesh GRPC API server` as well as an `http-json gateway server`.

> The Spacemesh GRPC API server of the first node (Node1) is provided at `localhost:6001`. Node2's server is at `localhost:6002`, etc...

> The Spacemesh API http-json gateway server of the first node (Node1) is provided at `localhost:7001`. Node2's server is at `localhost:7002`, etc...

You can use any GRPC client such as `grpcurl`, or a json-http client such as `postman` to use the API provided by each of the nodes.

## Connecting smrepl to a node

Smrepl is a `Spacemesh GRPC API Client`. You can connect an instance of smrepl to any of a localnet nodes via their GRPC API servers.
For example, use the following bash command to start an instance of smrepl and connect it to the first node in a localnet:

```
./smrepl -server localhost:6001
```

## Executing Transactions with smrepl

> Note that currently you can only execute transactions once epoch 2 (3rd epoch from epoch 0) starts.

The default localnet settings specify a genesis account with some coins, and sets the rewards account of all the 10 nodes on the network to the same account. The account address is `0x99027e1e3DE4de36d99f0054fa646EF663c276AD`.

Follow these steps to use smrepl to transact using this account.

1. Download [this wallet file](https://raw.githubusercontent.com/spacemeshos/local-testnet/master/cli-wallet.json) to your computer.
1. Start smrepl and connect it to any of the 10 nodes.
1. Open the wallet in smrepl. The wallet's password is `spacemesh`.

You can also use smrepl to create new accounts and to set the rewards account of any of the 10 nodes to a new account.

## Getting Node and Network status
Use the smrepl commands to get node and network status.

## Viewing Logs

If you use Docker Desktop then you can see nodes log in the Docker Dashboard App. You can also enter this command to tail any of the 10 nodes logs:

```bash
docker logs -f --tail 100 node1
```

To tail the Poet logs use:
```bash
docker logs -f --tail 100 poet
```

## Accessing Logs Using Kibana
You can enable Kibana to view nodes and poet logs.
To enable it set `--elk true` when creating a new localnet. For example:

```bash
spacemesh-local-testnet create --elk true
```

When Kibana is enabled, access it from your web browser via this url: `localhost:5601`. Continue to login using user name `elastic` and password `spacemesh`.


## Getting Help and Providing Feedback
Join the dev channel on the [Spacemesh community discord](https://chat.spacemesh.io/).
