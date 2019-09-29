# Coin Transfer Transactions demonstrate

This document details the states for the open testnet timeframe for coin transfer transactions.

|  code | Label | Label Color | Status Text | Metadata | Terminating? | Possible Next State | Notes |   
|---	|---	|---	|---	|---	|---	|---	|---	|
|   0	|   Rejected	| Red  	|  Transaction is rejected and can't be further processed.	|   	|   	|   	|   	|   	
|   1	|   Insufficient Funds	|  Red 	| Insufficient account balance to execute this transaction. |   	|   	|   	|   	|   	
|   2	|   Conflicting	| Orange  	| Another transaction with the same counter is pending. |   	|   	|   	|   	|   	
|   3	|   Pending	| Lighter Green   	| Waiting for transactions to be added to the mesh...  	|   	|   	|   	|   	|   	
|   4	|   Processing	| Light Green  	| Transaction is processing but not approved yet. |   	|   	|   	|   	|   	
|   5	|   Approved	| Green  	| Transaction is approved and will be confirmed with high probability. |   	|   	|   	|   	|
|   6	|   Confirmed	| Deep Green  	| Transaction is confirmed. |   	|   	|   	|   	|   	
|   7	|   Reserved	|   	|   	|   	|   	|   	|   	|
