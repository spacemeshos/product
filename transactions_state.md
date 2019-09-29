# Coin Transfer Transactions States

This document details the possible states of coin transfer transactions for the open testnet timeframe.

|  code | Label | Label Color | Status Text | Metadata | Terminating? | Possible Next State | Notes |   
|---	|---	|---	|---	|---	|---	|---	|---	|
|   0	|   Rejected	| Red  	|  Transaction is rejected and can't be further processed.	|   N/A	|   Y	|  n/a 	|   This is to notify users that a tx they attempted to submit from the wallet was rejected by the full node for any reason - failed validation before broadcast....	| N/A |   	
|   1	|   Insufficient Funds	|  Red 	| Insufficient account balance to execute this transaction. |  n/a | Y |  any  	|   Once funds are available, tx may continue processing and move to any state	|   	
|   2	|   Conflicting	| Orange | Another transaction with the same counter is pending. | Conflicting TX ID | N   	| Pending, Processing, Approved   	|    |   	
|   3	|   Pending	| Lighter Green | Waiting for transactions to be added to the mesh... | N/A | N | Processing | Submitted to mempool and was not rejected - not in block yet (e.g. was in block, but was not applicable)  	|   	
|   4	|   Processing	| Light Green  	| Transaction is processing but not approved yet. | Layer # (and ID ?)| N  	| Approved, Pending, Insufficient Balance 	| TX is in at least one block in layer X that was not excluded from hare results (hare didn't complete for layer X yet)	|   	
|   5	|   Approved	| Green  	| Transaction is approved and will be confirmed with high probability. | Layer # (and ID ?)  	|  N 	|  Confirmed, Insufficient Balance 	| TX is in at least one block that was included in HARE results  	|
|   6	|   Confirmed	| Deep Green  	| Transaction is confirmed. | N/A  	| Y  	| N/A  	| Played into global state (if conflicting transactions exist - this one was selected)   	|   	
|   7	|   Reserved	|   	|   	|   	|   	|   	|   	|
