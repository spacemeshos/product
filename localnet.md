# Spacemesh Local Testnet (LocalNet)

## Intro
LocalNet is designed for developers who want to run a fully functional Spacemesh p2p networks on their computers for testing, evaluation and development purposes.

There are 2 main ways to run a LocalNet.
1. Run a LocalNet which uses binary releases of Spacemesh software components (built on github from Spacemesh open source software, and published to dockerhub).
2. Run a localnet which uses locally built components from source code.

<br/>

A functional Spacemesh network includes 3 main components:
1. [go-spacemesh full p2p nodes](https://github.com/spacemeshos/go-spacemesh). Each node participates in the consensus protocol and mines new blocks (we call this smeshing). Each node also provides a GRPC API you can use to submit transactions, view node settings and change node settings.
1. [Poet Service](https://github.com/spacemeshos/poet). This is a proofs of elapsed time service that is used by the full nodes as part of Spacemesh's proof of space time protocol. A network only need one instance of this service to operate.

1. [CLIWallet](https://github.com/spacemeshos/cli-wallet). An open-source terminal wallet. You connect an instance of CLIWallet to any of your LocalNet go-spacemesh nodes. Use CLIWallet to submit transactions to the network via a node, check network and node status, check account balances, and modify any full node runtime behavior.

> go-spacemesh, Poet and CLIWallet are fully open source. You can use binary releases for your platform from each component github repo, or build them locally on your computer.

When you run a LocalNet with the default settings, specific dockerhub releases of Poet and go-spacemesh components are used. However, you can easily modify this to use locally built components from source code.

## LocalNet Prerequisites

- macOS or Linux (Windows 10 is not yet supported)
- Docker
- NPM
- Docker Compose

## About spacemesh-local-testnet

`spacemesh-local-testnet` is an NPM package published to NPM. Use it to create and start a LocalNet, and to stop and delete a running LocalNet.

> The package is fully open source and the source code is available [here](https://github.com/spacemeshos/local-testnet).

When you run `spacemesh-local-testnst` without any custom options, it uses sensible defaults that have been tested to work. You can customizable these settings to override the default network configuration and behavior.

## Installing spacemesh-local-testnst

```
npm install -g spacemesh-local-testnet
```

## Running a LocalNet

To create and start a local network using the default settings run:

```bash
spacemesh-local-testnet create
```

To stop and delete a running network run:

```bash
spacemesh-local-testnet delete
```

## Running a LocalNet with custom settings

You can change a local network default settings and determine which go-spacemesh and Poet components binaries to use in your network. To see available options enter:

```bash
spacemesh-local-testnet --help
```

## Running a LocalNet with locally-built go-spacemesh nodes

Run the following command in your go-spacemesh cloned repo root directory:

```bash
docker build -t spacemesh:local .
```

Next, run the following command to use the image built above in a new LocalNet:

```bash
spacemesh-local-testnet create --go-sm-image=spacemesh:local
```

## Connecting CLIWallet to a LocalNet Node

> The Spacemesh API GRPC endpoint of the first miner (Miner1) is `localhost:8001`. Miner2's endpoint is `localhost:8002`, etc...

To connect to a new with CLIWallet start it with one of the nodes GRPC API endpoint. The following command will start an instance of CLIWallet and connect to the first of the 10 miners in a LocalNet:

```
CLIWallet -server localhost:8001
```

## Executing Transactions with CLIWallet

The default LocalNet settings specify a genesis account with some coins, and sets the rewards account of all the 10 nodes on the network to the same account. The account address is `0x2fbe2610f69237f57ac3043f3213983819fe3ea5`

Follow these steps to use CLIWallet to transact using this account.

1. Download [this wallet file](https://raw.githubusercontent.com/spacemeshos/local-testnet/master/cli-wallet.json) to your computer.
1. Start CLIWallet and connect it to any of the 10 nodes.
1. Open the wallet in CLIWallet. The wallet's password is `spacemesh`.

You can also use CLIWallet to create new accounts and to set the rewards account of any of the 10 nodes to a new account.

## Viewing Logs

If you use Docker Desktop then you can see nodes log in the Docker Dashboard App. You can also enter this command to tail any of the 10 nodes logs:

```bash
docker logs -f --tail 100 miner1
```

To tail the Poet logs use:
```bash
docker logs -f --tail 100 poet
```



## Accessing Logs Using Kibana
You can use the `--elk` optional `spacemesh-local-testnet` startup flag to setup Kibana to view nodes and Poet logs. When Kibana has been setup, access it from your web browser via this url: `localhost:5601`.

## Troubleshooting

### Docker No Such Image Error
If you are getting an `no such image` error when creating a new LocalNet then pull the image using:
```
docker pull spacemeshos/go-spacemesh:v0.1.23
```

and try to create a new LocalNet again.


## Getting Help and Providing Feedback
Join the dev channel on the [Spacemesh community discord](https://chat.spacemesh.io/).
