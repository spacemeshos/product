Main 0.2 Dev Tasks

POST
1. Finalize GPU post init scrypt modifications, implement and test them.
1. Finalize new post construction concrete params for 0.2 for required user params (100GB and up).
1. Implement new POST construction and GPU init components.

Consensus
1. Implement all Tortoise (block voting) and Hare related 0.2 changes.

Transaction Processing and Global State
1. Fully specify the state transition function, stored global state (e.g tx receipts) and API and implement in go-sm according to spec.
1. Update transaction data structures and all related tx processing code to support SVM transactions and ed25519 signature scheme. Currently only supports simple coin transactions and ED25519++ signature scheme.

SVM and Smart Wallets
1. Integrate SVM into go-sm.
1. Implement the smart wallet smart wasm contract.
1. Update genesis flow to support deployment of genesis smart wallets.