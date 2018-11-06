# Overview
Our main goal is to create a simple, minimalistic, functional crypto currency powered by the permissionless `Spacemesh protocol` and to demonstrate the platform's security, distribution, usability and scalability properties on a public open testnet. MVP1 will not support smart contracts yet. Smart contracts is the main focus of MVP2.

# Primary User Story
1. Build `Spacemesh Node` and `Spacemesh UI` apps from source code or download a packaged release
2. Create a new `Spacemesh HD Wallet` and a `Spacemesh user account`
3. Start a node and use its REPL to set a coin-base account and perform node POST commitment setup
4. Run node in a console session and participate in the consensus protocol as validator
5. Earn validators coin awards according to the protocol for honest participation
6. Get Spacemesh coins from the `Spacemesh Tap` (faucet)
7. Transfer Spacemesh coin to any account
8. View onchain Spacemesh account balances

# Secondary User Stories
## Testing Scenarios
1. Identify a security issue or another critical issue and get bounty awards based on issue severity and impact
2. Configure node to submit performance data to team Spacemesh so it identify critical issues and measure network latency

## Release Highlights
- Native `Spacemesh node` packaging for linux, windoz and os x
- Basic node config via CLI flags or a config file
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
