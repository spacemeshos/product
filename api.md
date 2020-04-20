# Spacemesh API design and methodology

This high-level documentation is intended to accompany the [Master API spec](https://docs.google.com/spreadsheets/d/1P89OVWdgJocPy0CGM43Ge7Sx_6dabCBEagaVQfOk9us/edit).

## Goal

The goal of this project is to design a single comprehensive API to allow multiple classes of consumers, including the [Spacemesh app](https://github.com/spacemeshos/smapp), independent wallet software, a [dashboard](https://github.com/spacemeshos/product/blob/master/dashboard.md), and an [explorer](https://github.com/spacemeshos/product/blob/master/resources/Explorer.pdf), to consume Spacemesh node data. This API must be flexible enough to support the different use cases for these (and future) consumers with minimal changes, and it must be intuitive enough to allow a node operator to quickly enable and disable different endpoints while keeping their node secure.

## For reference

For comparison, please see the API implemented in the main Ethereum clients:

- go-ethereum [Management APIs](https://github.com/ethereum/go-ethereum/wiki/Management-APIs)
- go-ethereum [JSON-RPC Server](https://geth.ethereum.org/docs/rpc/server)
- OpenEthereum (formerly Parity Ethereum) [JSON RPC API](https://wiki.parity.io/JSONRPC)

## Design methodology

API methods are grouped together into broad sets, called "facades." This division is made according to the following logic:

1. Function: Endpoints are grouped into facades based primarily upon function. For instance, all endpoints related to mesh data (blocks, transactions, epochs, layers, accounts, rewards, etc.) are grouped together under a "mesh" facade.
2. Archive mode
3. Stream

## Open questions

## Facade Design Method
- Sets of API methods are broken down into groups called "facades." Each facade is separately enabled in the node using a CLI flag.
- Method naming convention: `facade.component.method-name`
- We group methods into facades by
  1. function
  2. mode (read-only methods are grouped together; create-update-delete methods must be explicitly enabled separately)
  3. type (ordinary, archive mode, stream)

## Large data sets support
- Every method which returns list of data supports pagination
- Only return a default no. of items + return a field with the number of items returned and support calling it with an offset to retrieve additional items... NTH: User can specify how many results to retrieve up to a max of say 100 and if he's not specifying it a default is used. e.g. 50. Otherwise: always return up to 20 items (constant) at an offset

## Design Ideas
- Full nodes store historical data of up to n=200 layer or something like that but prune non-consensus data that's older than this.
- For older data, e.g., intermediate states, you must ask an archive node.
- An "archive node" is just a full node with pruning/garbage collection turned off.
- We *may* add an additional distinction whereby archive nodes store some of the same data as a full node but with additional indexes.
- Lots of the API design isssues are due to lack of decision on layer and epoch canonical state and rewards as part of consensus.  We have to resolve this.
- Stream: GRPC only - no json/http/websockets

## Questions

- Are receipts and events part of consensus? Can non-archive nodes prune them?
- What about layer and epoch hashes?
- Is canonical state part of layer data? epoch data? (see [state root checkpointing](https://github.com/spacemeshos/research/issues/45))
- If smart contract txs events and receipts are NOT part of canonical state - how can a node know that the data he's getting from other nodes is correct?
