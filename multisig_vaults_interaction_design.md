# Spacemesh Vaults - Multisig operations Interaction Design

## Background
- We decided to implement vaults using state-less multi-sigs. This means not using vault smart contract to store pending multi-sig transactions prepared by a user for signing by another user.
- We only need to support 2/3 multi-sig vaults smart contracts for Spacemesh 0.2 (aka multi-sig vaults) or single-signer vaults (aka simple vaults).

In the use cases below, we have a multi-sig vault with Alice, Bob and Charlie as the master accounts for the vault (specified in spawn time).

## Use Case 1: Withdrawing from a Multi-sig Vault using Web Service

1. Alice and Bob agreed to withdraw funds from the vault to another account, or at least Alice hopes that Bob or Charley will approve her withdraw request when she ask them to do so)
1. Alice uses a client such as Smapp or CLIWallet to prepare and sign a withdraw request message. The message should contain the following data:
    - Recipient account address.
    - Withdraw amount.
    - Signature scheme (e.g. ed25519 or ed25519++).
    - Alice full public key if signature format is ed25519.
    - Alice signature on the data above (using the private key corresponding to her vault master account address).
1. Alice's client gives Alice an option to use a web service to send the message to one of the other master accounts holders, or to manually copy & paste the message and send it to Bob via another channel such as instant messaging or email.
1. Alice decides she wants to use a web service to send the message to another master account holder.
1. Alice's client prompts Alice to decide who should be the other signer - Bob or Charlie. Alice specifies Bob.

> Note that this makes cleaning pending web service messages a bit simpler as only Bob can remove the message from the web service.  If the message is not specifically to Bob or to Charlie, then it is not clear how messages can be removed from the web service easily without the web service monitoring the mesh for svm transactions. If the message is designated to Bob or Charlie then their clients will request the web service to remove the message on their behalf once they executed the transactions (or rejected it).

> From a product perspective it is perfectly okay for release 0.3 to expect a mutli-sig vault user to request which party should sign a transaction he or she would like to do and not issue request that one of the other parties can sign.

6. Alice's client submits the message to the web service api and displays the follow-up instructions:

> `Please ask Bob to open his wallet (Smapp or Cliwallet) and access your vault. He should see a request to execute this withdrawal and will be able to review and execute it`.

7. The web services stores the message indexed by the vault app address as well as the designated address (bob's master account address).

8. Bob opens his client (Smapp or CLIWallet) and accesses the vault.
9. Bob's client requests the web service for any pending messages designated to Bob for this vault.
10. The web service returns Alice's signed request for withdrawal.
11. Bob's client display the request details such as receiver address, amount and initiator address (Alice).
11. Bob decides to execute the withdraw transaction.
12. Bob's client prepares an SVM withdraw transaction which includes Alice's signed message and submits it to the network.
13. Bob's client sends a message to the web service to remove the message from its store as it was handled by Bob. In addition, messages on the web services that were not removed should expire automatically after a reasonable TTL such as 3 weeks.
14. SVM executes Bob transaction and verifies Alice's signature on the data in the calls params. The transaction is only executed if Alice's signature on the withdraw data can be verified.

---

## Use Case 2: Withdrawing from a Multi-sig Vault without using Web Service

Same flow as use case 1 until step 4.

4. Alice decides she wants to send the message to Bob directly.
5. Alice's client copies the message's bin64 encoding to the clipboard and asks her to paste it in a channel with Bob. e.g. Instant message session or email.
6. Alice's client provide these instructions to Alice:
`Send the message to Bob and ask him to open his vault in his wallet, select the 'Complete Transaction' command` and paste the message he received from you when prompted.
7. Alice sends the bin64-encoded message to Bob and communicates the instructions to him.
8. Bob open his client (CLIWallet or Smapp), accesses the vault and chooses the 'Complete Transaction' command.
9. Bob's client prompts Bob to paste a message.
10. Bob pastes the bin64-encoded message Alice sent him.
11. The interaction continues from User Case 1, Step 11.

---

## Daily Spending Use Cases
The daily spending multi-sig operations such as change daily spending amount and change daily spending account should work in a similar way to the withdraw use cases described above. Bob's client need to know which operation a message confirms in order to present the correct UI and information for Bob to review and to sign.
