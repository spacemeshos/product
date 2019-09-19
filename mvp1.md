# About MVP1

Our main goal is to create a simple, minimalistic, functional cryptocurrency powered by the permissionless `Spacemesh protocol` and to demonstrate the platform's security, distribution, usability and scalability properties on a public open testnet.

MVP1 is the product and services we release as part of the Spacemesh Open Testnet.

MVP1 only supports Spacemesh Coins transactions and does not support smart contracts yet.

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

# Primary User Story - Desktop Computer Owner
1. Download the `Spacemesh App Installer` for Windows 10, OS X or Linux
2. Run the installer to install the `Spacemesh App` on desktop
3. Create a new wallet, awards account and setup mining in the App
4. Leave App open running 24x7 and participate in the Spacemesh protocol
5. Earn awards according to the protocol for honest participation and view awards in the awards account transaction log
6. Get Spacemesh coins from the `Spacemesh Tap` (faucet)
7. Transfer Spacemesh coins to any account by executing a coin transaction in the App

# Secondary User Stories
## Testing Scenarios
1. Identify a security issue or another critical issue and get bounty awards based on issue severity and impact
2. Configure node to submit performance data to team Spacemesh so it identify critical issues and measure network latency

## Release Highlights
- Native `Spacemesh node` packaging for linux, Windows 10 and OS X
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

## Network testing highlights
Part of the goals of the testnet is to perform various tests required to finalize the platform for a Mainent release.
- Setup a large-scale swarm on multiple regional cloud data centers
- Optimize protocol params for the most desirable tradeoffs
- Simulate various attack vectors
- Simulate large number of user transactions
- Validate resistance to double spending and ddos attacks

## Testnet Cloud Services
The testnet should include the following deployed services
- Foundation bootstrap nodes
- POET supporting web service with some redundancy
- Discord chat channel Tap (faucet)
