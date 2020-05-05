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
2. Archive mode: Certain endpoints are only available from archive nodes (see below). These are grouped together into an `archive` facade.
3. Stream: Certain endpoints provide streams of real-time data (see below). These are grouped together into stream facades.

The fully-qualified name for an endpoint, as used canonically in the API, is `facade.method-name`.

## Support for large data sets

Some data sets served by the API may group to hundreds of thousands, or millions, of rows. In order to support this amount of data, all API endpoints that return multiple rows of data return data in pages. Each call to one of these endpoints can optionally include a page size and page number. By default, the API will return the first page containing 50 elements. There is also a maximum page size, of ~1000 rows.

## Archive nodes

The vast majority of data exposed by the API are available from any fully synced full node. However, the API also includes a few endpoints (under the `archive` facade) that are only available on a special class of node called an "archive node." An archive node is identical to a full node, except that it stores _all intermediate state,_ i.e., the state at the end of every layer. This allows it to provide data such as the trace and state diff for all historical transactions. (This is a very large amount of data, and a non-archive full node would have to rerun all transactions from genesis to determine the historical state before an arbitrary historical transaction.)

Another way to conceive of an archive node is that it's a full node with "state pruning" or "garbage collection" turned off.

We *may* add an additional distinction whereby archive nodes store some of the same data as a full node but with additional indexes.

These endpoints should only be consumed by blockchain explorers; as an example, see how Etherscan displays a [state diff](https://etherscan.io/tx/0xeb9c0156b5d40caf446170d422b25f159dd2efe9bc0a0c12aeee05b673309a6e#statechange).

## Non-streaming vs. streaming endpoints

For certain data sets, such as blocks, transactions, and account data, in addition to the non-streaming (paginated) endpoints, there are also streaming endpoints. These streams are designed to provide _new data only:_ they do not accept any parameters, and just stream new data in real-time as it becomes available. For instance, the `mesh-stream.account` endpoint streams all events that touch an account: transactions, balance updates, rewards, etc. Older data must be downloaded using the corresponding non-stream endpoints.

Note that all stream endpoints are unidirectional (read-only), and run only via GRPC (no JSON/HTTP/websockets/etc.).

## Open questions
- Do we want receipts and event logs? Are they part of consensus? Should non-archive nodes prune them?
- What about layer and epoch hashes?
- Is canonical state part of layer data? epoch data? (see [state root checkpointing](https://github.com/spacemeshos/research/issues/45))
