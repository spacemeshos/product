# API DESIGN Whiteboard

## API Categories

### I. NODE API
Overview: Data specific to a specific node instance.
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


3. Node / TX Processing
    - Submit a new signed tx to the pool (any tx type)


4. Node / Sync
    - Get sync status ( synced / total layers), sync status num


### II. Mesh Basic Data API
Overview: simple data access with focus on app and api clients.
Provider: Full node.
Clients: apps, wallets.

0. Mesh / Data / General
    - Get current layer and epoch
    - Get Network Genesis time
    - Get Network ID
    - Get latest root-hash {layer #, hash}

1. Mesh / Data / Transactions
    - Get tx info/status
    - Get txs info (pass several tx ids as args)


2. Mesh / Data / Accounts
    - Get account's nonce
    - Get account's balance
    - Get account's rewards (list)
    - Get account txs (list)


3. Mesh / Data / Smart Contracts
    - Get app instance data for a var name / id


4. Mesh / Data / Smeshers
    - Get smesher's coinbase account
    - Get smesher's ATXs (list)


5. Mesh / Data / Streams
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
