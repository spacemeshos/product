# Spacemesh Platform

> This page lists the main technical resources available for the Spacemesh Protocol, as well as the Github repos that are used to implement the Spacemesh cryptocurrency.

## The Spacemesh Protocol
- [Overview Part 1](https://spacemesh.io/protocol)

- [Overview Part 2](https://spacemesh.io/spacemesh-protocol-v1-0/)

- [Overview Video 1](https://youtu.be/liNmlxrwrvI)

- [Overview Video 2](https://youtu.be/sbZZy9CYjEE)

- [Overview Video 3](https://youtu.be/BjKBYIbrScM)

- [Overview Video 4](https://youtu.be/yTjXFb-ZhOY)

- [Spacemesh Protocol e-print](https://drive.google.com/file/d/18I9GPebWqgpvusI1kMnAB9nayBbL-1qN/view)




- Developers oriented [protocol documentation](https://protocol.spacemesh.io).

---

## Protocol Implementation Github Repos

These are the Github repo that are used to implement the protocol.

### Go-Spacemesh
Implementation of a [Spacemesh full node](https://github.com/spacemeshos/go-spacemesh) written in go lang.

### SVM
The [Spacemesh virtual machine](https://github.com/spacemeshos/svm) runtime and tools written in Rust.

### GO-SVM
[Go bindings for SVM](https://github.com/spacemeshos/go-svm). Used to embed SVM in go-spacemesh.

### Poet
Implementation of the Spacemesh [proof of elapsed time service](https://github.com/spacemeshos/poet) in go lang.

### ED25519
[Custom Ed25519 signature scheme](https://github.com/spacemeshos/ed25519) library used to sign Spacemesh transactions. Drop-in replacement for go lang ed25519 lib with additional features such as extraction of public key from message and signature. Used in go-spacemesh.

### ED25519-WASM
Builds a [WASM library](https://github.com/spacemeshos/ed25519-WASM) from ED25519. Used in Smapp to sign transactions.

### Fixed
[Fixed math arithmetics lib](https://github.com/spacemeshos/fixed) used in go-spacemesh.

### Ledger App
[Spacemesh ledger app](https://github.com/spacemeshos/ledger-app), enabling users to sign Spacemesh  transactions using a ledger device.

### GPU-POST
A c library for generating [proofs of space using gpu compute](https://github.com/spacemeshos/gpu-post). Used in go-spacemesh.

### Smapp
A [cross platform electron app](https://github.com/spacemeshos/smapp) which contains a wallet and user interface for managing a local go-spacemesh full node and mining.

### CLIWallet
A reference [CLI Wallet](https://github.com/spacemeshos/CLIWallet) utilizing the Spacemesh API and a local full node.

### API
Specification and implementation of Spacemesh [full-node api services](https://github.com/spacemeshos/api). Implemented by go-spacemesh full nodes and used by clients such as CLIWallet and Smapp to interact with a full node.
