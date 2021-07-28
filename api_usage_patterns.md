Product Note: Transactions Related API Usage Patterns (Spacemesh 0.2)

# Stateful 0.2 Clients

## Overview
- Client should locally store the ids of all transactions it is interested in, and transaction data for these transactions.
- Clients should update these data based on api results.

Stateful clients such as Smapp should use the following api patterns for working with transactions:

## New App Session Flow
1. Read `transaction ids set` from local store.
1. Call `TransactionService::TransactionsState(ids)` with the `transactions ids set` as input. The goal is to get the current `TransactionState`. Update local transaction data store based on results of call (see below for more info).
1. Call `MeshService::AccountMeshDataQuery(accountId)` for each of the client's user accounts in order to get mesh transactions the client doesn't know about yet that touch any of the user's accounts, e.g., inbound transactions from another account/user. Update the local transaction data store with the transaction ids in the results (including their layer numbers).
1. Subscribe to `Transaction::TransactionsStateStream(ids)` using `transactions ids set`. Update the locally stored transactions store with new streaming data. This is required to receive updated TransactionState for all transactions that the client is interested in.
1. Subscribe to `MeshService:: AccountMeshDataStream(accountId)` for all local accounts of interest. Update the locally stored transactions based new streaming results. This is required to update `LayerId` for transactions the user cares about. This happens when transactions get included in the mesh or when the mesh is reorganized.

Note: in practice it may make sense to do this in reverse order, i.e., to subscribe to the streams _before_ running the queries, to ensure that no data are missed between the initial queries and the stream subscription.

## Transactions Local Data Store
- Store should include `transactions ids set` and transaction data for each transaction.
- When a new transaction is added to the store, its id should be added to the `transactions ids set`.
- Transactions created and submitted by the client should be added to the store.
- Store should be updated with new results from `TransactionService` and `MeshService` api calls. 
- If `TransactionState` is `TRANSACTION_STATE_MESH` or `TRANSACTION_STATE_PROCESSED` in data returned for a transaction from a `TransactionService` api, then client should call `MeshService:: AccountMeshDataQuery()` for that transaction in order to get its layer id from the node and update layer id in the local store.
