## Main 0.2 Open Dev Tasks

Moved to https://github.com/orgs/spacemeshos/projects/14

------

# Deprecated

### POST Tasks
1. Implement GPU post init scrypt variable output size. Part of [SMIP 27](https://github.com/spacemeshos/SMIPS/issues/27).
1. Finalize new post construction concrete params for 0.2 (e.g. 100GB and up).
1. Implement the full Smesher API Service.

### Consensus Tasks
1. Implement all Tortoise (block voting) and Hare related 0.2 changes.
1. Implement and benchmark self healing protocol. Note that this task may require more than 1 dev and benchmarking iteration per research.

### Transaction Processing
1. Implement full transaction processing for all 0.2 supported transaction types (6 types). Generate receipts, store them and properly update accounts db. See [SMIP 23](https://github.com/spacemeshos/SMIPS/issues/23)

### Full Node
1. Finish [API 2.0 tasks](https://github.com/orgs/spacemeshos/projects/11) including SVM related methods, new rewards and transaction receipts.
1. Implement new rewards scheme.
1. Implement new sync algorithm.
1. Update notion of net-id and miner id per research recommendations. [SMIP 26](https://github.com/spacemeshos/SMIPS/issues/26)
1. Fix known issues that are blocking open testnet release including [backlog issues](https://github.com/orgs/spacemeshos/projects/4).
1. Implement telemetry and opt-in/out.

### SVM and Vaults
1. Fully integrate SVM into node and transaction processing flow.
1. Implement the vaults smart contracts (standard and vesting).
1. Implement deployment of vesting vaults from network params file to genesis flow.

### Smapp and CLIWallet
1. Migrate to use API 2.0.
1. Implement vaults features using svm-codec lib.
1. Implement multi wallets support and wallet-only mode.
1. Implement ledger wallet accounts features.

### Integration Testing and Testnet Readiness
- Run a close dev-net with 0.2 release candidate for open testnet and stabilize it so it is ready for open testnet release.
- Test end-to-end user flows to ensure that the platform is minimally usable (like we did for 0.1 until it got usable).
- Triage bugs and determine which ones are blocking open testnet release. Fix them and test in close dev-net.
