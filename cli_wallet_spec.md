# CLI WALLET 0.1 SPEC

## GOALS
- Provide a simple CLI wallet that developers can use together with a local running go-spcamesh full node (configured to run in a specific testnet) to execute transactions, check account balance and nonce and sign messages.
- The CLI wallet is a reference wallet for developers and not for non-technical users - it is a basic reference wallet and doesn't need to be secure. e.g. the wallet data file should not be encrypted at rest and we should not require a password to load the wallet data file (like we do in smapp wallet).

## High-level Requirements
- Supported runtime platforms: Linux, Windows and OS X.
- Easily build from source code on any platform.
- Ideally implemented in GO and not in Python so it can be compiled to a stand-alone binary that doesn't require specific version of python or messing with venv. As our main client is in Go, it makes sense to write this in Go so it is easy for GO dev to read the code and modify it.
- Support a toml config file with good defaults. e.g. connect to local node over the default http api endpoint.
- Wallet should be started with optional flags that override the values in the config file.
- User should interact with the wallet via simple CLI commands - similar to an interpreter.
- Should communicate with the node using the http/json API - not GRPC.

## CLI Flags
- `--api <ip:port>` - full-node http-json api url (defaults to the default node local host http-json api url).
- `--config <path>` - config file url (overrides default to same dir as wallet executable).

## REPL Commands
1. `NEW` - Create a new account (key pair) - should be auto persisted to a wallet data file. Becomes current account.
3. `SET` - Enumerate previously created accounts (key pairs) loaded from the data file and set one of them as current.
4. `INFO` - Display current account's balance, counter/nonce, account public address (0x[20_bytes] format), full private and public keys and the smeshing status (post status, post data file path)
5. `NET` - Display local node status (/v1/nodestatus) + the current POST status.
6. `TX` - Execute a coin transaction (only if local node is synced) to a target account. Will be signed by current account. User needs to input the dest account string - 0x[20_hex_bytes) format.
7. `SIGN` - Sign a text message with the current account private key. When message is empty, sign the public key.
8. `COINBASE` - set current account as coinbase account in the node.
9. `SMESH` - Start smeshing. User needs to provide a path to the POST file as a param. The current account should be used as the coinbase accoount. User must have rw permissions to this path. e.g. `SMESH c:\`.
10. `TXS` - Get a list of transactions (outgoing and incoming) for the current account since layer 0. For each transaction, display full transaction info.

- When a wallet is launched, it should read the data file and set the first persisted account (if any) as the current account.
- Always display accounts using the 0x[20_hex_bytes] format.
