## Main 0.2 Open Dev Tasks

### POST Tasks
1. Implement GPU post init scrypt modifications (GPU Project Phase III).
1. Finalize new post construction concrete params for 0.2 for required user params (100GB and up).
1. Implement full Smesher API Service.

### Consensus Tasks
1. Implement all Tortoise (block voting) and Hare related 0.2 changes.
1. Implement and benchmark self healing protocol. Note that this task may require more than 1 dev and benchmarking iteration per research.

### Transaction Processing
1. Implement full transaction processing for all 0.2 supported transaction types (6 types). Generate receipts, store them and properly update accounts db.

## Full Node
1. Finish API 2.0 including SVM related methods.
1. Implement new rewards scheme.
1. Update notion of net-id and miner id per research recommendations.
1. Fix known issues that are blocking open testnet release.

### SVM and Smart Wallets
1. Integrate SVM into go-sm.
1. Implement the vaults 2 smart contracts.
1. Add deployment of vesting vaults from network params file to genesis flow.

### Smapp and CLIWallet
1. Migrate to use API 2.0.
1. Implement vaults features.
1. Implement multi wallets support and wallet only mode.
1. Implement ledger wallet accounts features.

### Integration Testing
- Run a close dev-nets with 0.2 release candidate for open testnet and stabilize it so it is ready for open testnet release.
- Test end-to-end user flows to ensure they are usable (like we did for 0.1 until it got usable).
- Triage bugs and determine which ones are blocking open testnet. Fix them.
