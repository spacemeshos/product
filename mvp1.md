# About MVP1

Our main goal is to create a simple, minimalistic, functional cryptocurrency powered by the permissionless `Spacemesh protocol` and to demonstrate the platform's security, distribution, usability and scalability properties on a public open testnet.

MVP1 is the product and services we release as part of the Spacemesh Open Testnet.

MVP1 only supports Spacemesh Coins transactions and does not support smart contracts yet.

# Primary User Story - Desktop Computer Owner - Run a full p2p Node
1. Download the `Spacemesh App Installer` for Windows 10, OS X or Linux
2. Run the installer to install the `Spacemesh App` on desktop
3. Create a new wallet, awards account and setup mining in the App
4. Leave App open running 24x7 and participate in the Spacemesh protocol
5. Earn awards according to the protocol for honest participation and view awards in the awards account transaction log
6. Get Spacemesh coins from the `Spacemesh Tap` (faucet)
7. Transfer Spacemesh coins to any account by executing a coin transaction in the App

# Primary User Story - Desktop Computer Owner - Transact with Spacemesh Coins
1. Download the `Spacemesh App Installer` for Windows 10, OS X or Linux
2. Run the installer to install the `Spacemesh App` on desktop
3. Create a new wallet with one main accounts
4. Receive coins to the account from another account or from the tap
5. Send Spacemesh Coins to another account

# Primary User Story - Developer
1. Build `Spacemesh full p2p node` and `Spacemesh CLI Wallet` directly from source code for Windows 10, OS X or Linux
2. Configure network so the full node can accept incoming connections
3. Run the full node console App
4. Create a new `Spacemesh Coins Account` in the CLI wallet
5. Perform the POST setup in the full node console app
6. Leave node running 24x7 and participate in the Spacemesh protocol
7. Earn awards according to the protocol for honest participation
8. Get Spacemesh coins from the `Spacemesh Tap` (faucet)
9. Transfer Spacemesh coins to any account by executing a coin transaction in the CLI wallet
10. View on-chain Spacemesh account balances via the CLI wallet

# Secondary User Stories
## Testing Scenarios
1. Identify a security issue or another critical issue and get bounty awards based on issue severity and impact

## Release Highlights
- Native `Spacemesh full p2p node` for Linux, Windows 10 and OS X implementing the Spacemesh Protocol
- Basic node config via CLI flags or a config file
<<<<<<< HEAD
- A native `Spacemesh App` which includes a full p2p node and a wallet
- A native `App installer` for Windows 10, OS X and Linux
- A comprehensive Open Testnet user guide
- Supporting POET and Spacemesh API Gateway web services
- Spacemesh Coin Transactions
- Spacemesh protocol implementation in the full p2p node
- Spacemesh Coins awards to full nodes awards account per the Spacemesh Protocol
- Open Testnet genesis config file network bootstrapping
- Managed Spacemesh bootstrap full p2p nodes on the cloud
- Spacemesh Coins Tap in a discord channel
- Auto-updated for the Spacemesh App to automatically install app and full node updates
=======
- A barebones `Spacemesh UI App` with the `Spacemesh wallet app` and the `Spacemesh dashboard app`
- An implementation of the Spacemesh blockmesh consensus protocol
- POST setup phase with a GPU-optimized hashing algorithm
- Ship POET and NIPST supporting services
- User accounts and balances Merkle tree as the canonical state with native support for Spacemesh Coin (SMC) transactions=
- Genesis state support for network bootstrapping

## Supported Transactions
Transactions are signed by user in the wallet app
1. Transfer coins between any two accounts. On-chain accounts should be created on demand on first transaction to an account.

2. Simple user data transactions
User can store binary data on the blockmesh and anyone may read it.

`write(key: bytes32, value: bytes)`
- Write a value in user's db
- key is a 32 bytes binary data
- Gas cost is based on sizeof(value)
- Can only be called by the user

`delete(key)`
- Deletes a value previously written by user
- Gas credit is based on sizeof(value)
- Can only be called by the user
- Exception if value is not store

## Spacemesh API methods
1. Read canonical account on-chain meta-data (e.g. nonce) and balance
2. Get the confirmed transactions for a layer (transactions that modified the state, not just entered the blockmesh)
3. Get current layer number, number of blocks and transactions
4. Execute the a supported transaction (signed and unsigned variants) - returns transaction hash
5. Get transaction receipt based on a transaction hash if it was confirmed
6. Get layer data based on layer number
7. Get account ids (requires user confirmation for Spacemesh Wallet or Spacemesh Browser Extension)
8. Get latest layer number
9. read(userId, key) - Read a value previously written by userId for a key from the blockmesh

## Network testing highlights
Part of the goals of the testnet is to perform various tests required to finalize the platform for a mainent release.
- Setup a large-scale swarm on multiple regional cloud data centers
- Optimize protocol params for the most desirable tradeoffs
- Simulate various attack vectors
- Simulate large number of user transactions
- Validate resistance to double spending and ddos attacks

## Testnet Cloud Services
The testnet should include the following deployed services
- Foundation bootstrap nodes
- POET supporting web service with some redundancy
- Gitter chat channel Tap (faucet)
>>>>>>> e21e6c5a50ae7e4f7f3cd68f6a79a8f0e5327e41
