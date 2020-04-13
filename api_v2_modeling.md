# API DESIGN Whiteboard

## API Categories

### I. NODE API
Overview: Data specific to a specific node instance. These should be only be accessible to the node's operator.
Clients: apps, wallets.
Provider: Full node.

1. Node / PoST - PoST setup and status functionality
    - Get Post status - setup, size, progress, etc...
    - Setup post
    - Stop post setup


2. Node / Management - Set or get node configurable params
    - Get current Smesher's ID
    - Get Smesher's coinbase account
    - Set Smesher's coinbase account


3. Node / Sync
    - Get sync status ( synced / total layers), sync status num


### II. Mesh Basic Data API
Overview: simple data access with focus on app and api clients.
Provider: Full node.
Clients: apps, wallets.

0. Mesh / General
    - Get current layer # and epoch #
    - Get Network Genesis time
    - Get Network ID
    - Get latest root-hash {layer #, hash}

1. Mesh / Transactions
    - Get tx info/status
    - Get txs info (pass several tx ids as args)
    - Submit new signed transaction.


2. Mesh / Accounts
    - Get account's nonce
    - Get account's balance
    - Get account's rewards (list)
    - Get account txs (list)
    - Get account type (coin or app instance)


3. Mesh / Smart Contracts
    - Get app instance data for a var name / id


4. Mesh / Smeshers
    - Get smesher's coinbase account
    - Get smesher's ATXs (list)


5. Mesh / Streams
Overview: Server-side streaming data feeds.
Provider: Full node.
Clients: apps, wallets.

    - Subscribe to mesh progress: current layer, epoch, (state-root-hash/layer #)
    - Subscribe to account's txs
    - Subscribe to account's rewards
    - Subscribe to Smesher's rewards
    - Subscribe to Smesher's atxs
    - Unsubscribe from any subscribed data stream - by subscription id ?

### III. Mesh Advanced Data API
Overview: Advanced mesh readonly data.
Provider: A full node which is synced from genesis under full data archival node.
Clients: dashboard, explorer and backup agents data workers.

1. Mesh / FullData / Streams

---

## Design Notes
- Consistency: use canonical format for addresses e.g. 0x[20_bytes_suffix] and not byte arrays.
- Large results set support via pagination. Every response which returns a list of data items should have pagination support built-in.
