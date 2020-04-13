# API DESIGN Whiteboard
## API Categories

I. NODE APIs (data specific to a specific node instance). Used by app.
Clients: app, wallets.

1. Node / Smeshing - PoST setup and status functionality
    - Post status - setup, size, etc...
    - Setup post

2. Node / Management - Set or get node configurable params
    - Get current Smesher's id

3. Node / TX Processing
    - Submit a new signed tx to the pool


II. Mesh Simple Data APIs - Provided by every full node.
Client: app, wallets.

4. Mesh / Data / Transactions
  - Get tx info/status
  - Get txs info
  - Get account txs (list)
  -
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
Client: app, wallet.

III. Advanced Data APISs - provided by a full node which is synced from genesis under full data archival node.
Client: dashboard, explorer and backup agents data workers.
