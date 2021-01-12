# Spacemesh 0.2 Transactions

## Glossary
- `ED22519` - ed25519 signature scheme. Ed25519 is the [EdDSA signature scheme](https://en.wikipedia.org/wiki/EdDSA) using SHA-512 (SHA-2) and Curve25519.
- `Ed25519++` - custom ed25519 signature scheme, as implemented in [this library](https://github.com/spacemeshos/ed25519). When used, transaction does not include a public key field.
- `NetworkId` - 32 bytes binary data that is unique for a Spacemesh network, e.g. a testnet or a mainnet. The network id is computed by a full node based on immutable network params and genesis data.
- `Address` - a Spacemesh address identifies an account. It is the 20-byte suffix of an account's public key.
- `XDR` - Transactions data is encoded in binary format using the [XDR codec](https://tools.ietf.org/html/rfc4506).

## Supported Transactions Types
Spacemesh 0.2 supports 3 transactions types:
1. `Simple Coin Transfer Transaction` (to another account or app).
1. `Call App Transaction` - call a method on a smart wallet instance (app).
1. `Spawn App Transaction` - create a smart wallet app from a deployed code-template.


A Spacemesh 0.2 transaction must be signed by one of 2 supported signature schemes: ED25519 and ED25519++.

----

## Transaction Data Item

Transaction data item is binary data item encoded using XDR. It is used by other data items defined below to describe a SignedTransaction. Following are the data items and the binary layout for each of the three supported transaction types.

### Simple Coin Transaction
```c
struct SimpleCoinTx {
    unsigned int TTL; // 32-bit
    opaque Nonce[1];
    opaque Recipient[20];
    unsigned hyper Amount;
    unsigned hyper GasLimit;
    unsigned hyper GasPrice;
};
```

### Call App Transaction

```c
struct CallAppTx {
    unsigned int TTL; // 32-bit
    opaque Nonce[1];
    opaque AppAddress[20];
    unsigned hyper Amount;
    unsigned hyper GasLimit;
    unsigned hyper GasPrice;
    opaque CallData<>;
};
```

### Spawn Transaction

```c
struct SpwanAppTx {
    unsigned int TTL; // 32-bit
    opaque Nonce[1];
    opaque TemplateAddress[20];
    unsigned hyper Amount;
    unsigned hyper GasLimit;
    unsigned hyper GasPrice;
    opaque CallData<>;
};
```

---

## Transaction Type Data Item
A type data item is a 1-byte enumeration that specifies a transaction type.

The least-significant-bit defines the signature scheme: `0 ⇨ ED25519;  1 ⇨ ED25519++`.

The remaining 7 bits define the type of the internal transaction:

```c
enum TransactionType {
    COIN_TX   = 0, // coin transaction
    EXEC_APP  = 1, // exec app transaction
    SPAWN_APP = 2, // spawn app
    // future types to be added here
};
```

The entire type byte can also be interpreted as a single enumeration, defined as follows:

```c
enum TransactionAndSignatureType {
    COIN_TX_ED       = 0, // coin transaction / ed
    COIN_TX_EDPLUS   = 1, // coin transaction / ed++
    EXEC_APP_ED      = 2, // exec app transaction / ed
    EXEC_APP_EDPLUS  = 3, // exec app transaction / ed++
    SPAWN_APP_ED.    = 4, // spawn app / ed
    SPWAN_APP_EDPLUS = 5, // spawn app / ed++
    // future types to be added here
};
```

The Type Data Item is used in the data structures described below.

---

### Transaction Authentication Message

`TransactionAuthenticationMessage` is a data structure that is never transmitted over the network or stored. It is constructed on-the-fly to sign transactions and verify transactions signature.

```c
struct TransactionAuthenticationMessage {
    opaque NetworkID[32];
    opaque Type[1];
    opaque TransactionData<>;
};
```

- `NetworkID` is a 32-byte unique identifier that is never transmitted, but used to ensure that transactions cannot be valid on more than a single network. This prevent replay attacks and other bugs which may be caused by a node processing a transaction that was not created and signed for the network it is being added to.

- `Type` - Transaction type data item as defined in this spec.

- `TransactionData` - The transaction data item. e.g  one of `SimpleCoinTx`, `CallAppTx` or `SpwanAppTx` as defined in this spec.

----

## Signed Transaction Binary Format

When a transaction is stored or transmitted over the network, the following XDR format is used for a signed transaction:

```c
struct SignedTransaction {
    opaque Type[1];
    opaque Signature[64];
    opaque TransactionData<>;
    opaque *PubKey[32]; // optional, depending on Type.
};
```

- `Type` - Transaction type data item as defined in this spec.

- `Signature` is a digital signature, using the specified signature scheme, of a `TransactionAuthenticationMessage` constructed from the transaction. An ED25519 or an ED25519++ signature is 64 bytes.

- `TransactionData` - The transaction data item. e.g  one of `SimpleCoinTx`, `CallAppTx` or `SpwanAppTx` as defined in this spec.

- `PubKey` - when ED25519 is used (and not ED25519++), the public ed key of the transaction signer. In ED25519++ the public key is extracted from the signed message and the signature.


###  Transaction ID
- The transaction id is not a field in the SignedTransaction object. It is calculated on the fly and used to index and reference transactions.
- Blocks contain a list of `TransactionID`s and therefore this definition is part of the consensus rules.
- The `TransactionID` is the 32-byte `SHA256` hash sum of the `SignedTransaction`.

----

## Signing a Transaction

Input:  `Type`, `TransactionData`, `NetworkID`, a signer.
Output: `SignedTransaction` binary data item.

1. Create `TransactionAuthenticationMessage` for the transaction using the input, and get its XDR encoded binary data.
1. Sign the binary data with the signer, using the signature scheme specified in the given transaction type.
1. Create a `SignedTransaction` and return it XDR binary data.

### Notes
- When ED25519 is used, the public key should be included in `SignedTransaction`.

- `SignedTransaction` doesn't include `NetworkID`. Both the signer and validator should have this data preconfigured.

- `SignedTransaction` is the transaction data that is sent on the Spacemesh network for processing. To submit a transaction, transmit its `SignedTransaction` via the network's gossip network.

---

## Decoding and Verifying a Signed Transaction

Input: `SignedTransaction`, `NetworkId`.
Output: Verified or rejected `TransactionData`.

1. Decode `SignedTransaction` and create an `TransactionAuthenticationMessage` using the input and the decoded data.
1. If the signature theme is ed (not ed++) by the transaction type then use the  public key `PubKey` and `Signature` from `SignedTransaction` to verify `TransactionAuthenticationMessage`. Otherwise, extract the public key from the signature and `TransactionAuthenticationMessage` using the ed++ public key extraction function.
1. Based on the transaction type, decode the transaction data into one of the three relevant native transaction data item as defined in this spec.

---