# API DESIGN Whiteboard

## API Categories

### I. NODE API
Overview: Data specific to a specific node instance.
Clients: apps, wallets.
Provider: Full node.

1. Node / Smeshing - PoST setup and status functionality
    - Post status - setup, size, etc...
    - Setup post


2. Node / Management - Set or get node configurable params
    - Get current Smesher's id


3. Node / TX Processing
    - Submit a new signed tx to the pool

### II. Mesh Basic Data API
Overview: simple data access with focus on app and api clients.
Provider: Full node.
Clients: apps, wallets.

1. Mesh / Data / Transactions
    - Get tx info/status
    - Get txs info (pass several as args)


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


5. Mesh / Data / Pubsub
Overview: Server-side streaming data feeds.
Provider: Full node.
Clients: apps, wallets.

    - Subscribe to account's txs
    - Subscribe to account's rewards
    - Subscribe to Smesher's rewards
    - Subscribe to Smesher's atxs
    - Unsubscribe from any subscribed data stream - by subscription id ?

### III. Mesh Advanced Data API
Overview: Advanced mesh readonly data.
Provider: A full node which is synced from genesis under full data archival node.
Clients: dashboard, explorer and backup agents data workers.
