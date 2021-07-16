Product Note: Transactions Related API Uusage Pattern

# Stateful Clients

## Overview
Client should locally store the ids of all transactions it is interested at, and transactions data for transactions with these ids when it got such data. Clients should update this data based on api results. 

Stateful clients such as Smapp should use the following api patters for working with transactions. 

## New App Session Flow
1. Read transaction ids set from local store. Call `TransactionService::TransactionsState(ids)` with this set as input.
1. Update local transaction data store based on results of call (see below for more info).
1. Call `MeshService::AccountMeshDataQuery(accountId)` for each of the client's user accounts, to get any mesh transactions that touch the accounts that the client doesn't may not know about. e.g. they were submitted by another user on another client. Update local transaction data store with the transactions (including its layer number).
1. Subscribe to `Transaction::TransactionsStateStreamRequest(ids)` for the locally stored transactions ids set - when a new data returned on the stream - update the locally stored transactions store with the data.
1. Subscribe to `MeshService:: AccountMeshDataStream(accountId)` for all local accounts of interest. Update locally stored transactions based on results.


## Updating Transaction Data in Local Store
- Store should include a set of transactions ids and a set of transactions.
- When a new transaction is added to the store, its id should always be added to the transactions ids set.
- Transactions created and submitted by the client should be added to the store.
- Local store should be updated with new results from `TransactionService` and 'MeshService' api calls. 
- If `TransactionState` is `TRANSACTION_STATE_MESH` or `TRANSACTION_STATE_PROCESSED` in data returned for a transaction from a `TransactionService` method, then client should call `MeshService:: AccountMeshDataQuery()` for that transaction in order to get its layer id from the node and update layer id in the local store.

