# CLI WALLET 0.1 SPEC

## GOALS
- Provide a simple CLI wallet that developers can use together with a local running go-spcamesh full node (configured to run in a specific testnet) to execute transactions, check account balance and nonce and sign messages.
- The CLI wallet is for developers and not users - it is a basic reference wallet and doesn't need to be secure. e.g. the wallet data file should not be encrypted at rest and we should not require a password to load the wallet data file (like we do in smapp wallet).

## High-level Requirements
- Supported platforms: Linux, Windows and OS X.
- Easily build from source code on any platform.
- Ideally implemented in GO and not in Python so it can be compiled to a stand-alone binary that doesn't require specific version of python or messing with venv. As our main client is in Go, it makes sense to write this in Go so it is easy for GO dev to read the code and modify it.
- Support a toml config file with good defaults. e.g. connect to local node over the default http api endpoint.
- Wallet should be started with optional flags that override the values in the config file.
- User should interact with the wallet via simple CLI commands - similar to an interpreter.

## Use Cases
1. Create a new account (key pair) - should be auto persist to a wallet data file. Becomes current account.
2. Set current account from previously created accounts (key pairs) from a wallet data file.
3. Enumerate previously created accounts (key paris) and select an account to use.
4. Display current account balance and nonce.
5. Display local node status (/v1/nodestatus)
6. Execute a coin transaction (only if local node is synced) to a target account. Will be signed by current account.
7. Sign a text message with the account private key.


