Product Note: Transactions Related API Usage Patterns (Spacemesh 0.2)

# Stateful 0.2 Clients

## Overview
- Client should locally store the ids of all transactions it is interested at, and transactions data for transactions with these ids when it got such data. 
- Clients should update this data based on api results. 

Stateful clients such as Smapp should use the following api patterns for working with transactions. 

## New App Session Flow
1. Read `transaction ids set` from local store. 
1. Call `TransactionService::TransactionsState(ids)` with the `transactions ids set` as input.
1. Update local transaction data store based on results of call (see below for more info).
1. Call `MeshService::AccountMeshDataQuery(accountId)` for each of the client's user accounts in order to get any mesh transactions that touch the accounts that the client doesn't may not know about. e.g. they were submitted by another user on another client. Update local transaction data store with the transactions in the results (including its layer number).
1. Subscribe to `Transaction::TransactionsStateStreamRequest(ids)` using `transactions ids set`. Update the locally stored transactions store with new streaming data.
1. Subscribe to `MeshService:: AccountMeshDataStream(accountId)` for all local accounts of interest. Update the locally stored transactions based new streaming results.


## Transactions Local Data Store
- Store should include `transactions ids set` and a set of transactions with data for each transaction.
- When a new transaction is added to the store, its id should be added to the `transactions ids set`.
- Transactions created and submitted by the client should be added to the store.
- Store should be updated with new results from `TransactionService` and `MeshService` api calls. 
- If `TransactionState` is `TRANSACTION_STATE_MESH` or `TRANSACTION_STATE_PROCESSED` in data returned for a transaction from a `TransactionService` api, then client should call `MeshService:: AccountMeshDataQuery()` for that transaction in order to get its layer id from the node and update layer id in the local store.

