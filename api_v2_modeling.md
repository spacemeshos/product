# API DESIGN Whiteboard

## API Categories

### I. NODE APIs (data specific to a specific node instance). Used by app.
Clients: apps, wallets.

1. Node / Smeshing - PoST setup and status functionality
    - Post status - setup, size, etc...
    - Setup post

2. Node / Management - Set or get node configurable params
    - Get current Smesher's id

3. Node / TX Processing
    - Submit a new signed tx to the pool

### II. Mesh Simple Data APIs - Provided by every full node.
Clients: apps, wallets.

4. Mesh / Data / Transactions
    - Get tx info/status
    - Get txs info
    - Get account txs (list)

5. Mesh / Data / Accounts
    - Get account nonce
    - Get account balance
    - Get account's rewards (list)

6. Mesh / Data / Smart Contracts
    - Get app instance data for a var name / id

6. Mesh / Data / Smeshers
    - Get smesher's coinbase account
    - Get smesher's ATXs (list)

7. Mesh / Pubsub - Subscribe to server-side streaming data feeds
Clients: apps, wallets.

    - Subscribe to account's txs
    - Subscribe to account's rewards
    - Subscribe to smesher's rewards
    - Subscribe to smesher's atxs
    - Unsubscribe from any subscribed data stream.

### III. Advanced Data APIS - provided by a full node which is synced from genesis under full data archival node.
Clients: dashboard, explorer and backup agents data workers.
