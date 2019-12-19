# Coin Transfer Transactions States

## Overview
This document details the possible states of coin transfer transactions for the open testnet timeframe.

## Status
WIP / Earlty Draft

## Status codes - Summary Table

|  code | Label | Label Color | Status Text | Metadata | Finality | Notes |   
|---	|---	|---	|---	|---	|--- | :--- |
|   0	|   Rejected	| Red  	|  Transaction is rejected and can't be further processed.	|   N/A	|  Final. | This is to notify users that a tx they attempted to submit from the wallet was rejected by the full node for any reason - failed validation before broadcast....	| N/A |   	
|   1	|   Insufficient Funds	|  Red 	| Insufficient account balance to execute this transaction. |  N/A | Not final. Any other next state is possible. | Once funds are available, tx may continue processing and move to any state	|   	
|   2	|   Conflicting	| Orange | Another transaction with the same counter is pending. | Conflicting TX ID | Not final. Possible next states: Pending, Processing, Approved |    |   	
|   3	|   Pending	| White | Waiting for transactions to be added to the mesh... | N/A | Not final. Next possible states: Processing | Submitted to mempool and was not rejected - not in block yet (e.g. was in block, but was not applicable)  	|   	
|   4	|   Processing	| Blue  	| Transaction is processing but not approved yet. | Layer # (and ID ?)| Not final. Next possible state: Approved, Pending, Insufficient Balance | TX is in at least one block in layer X that was not excluded from hare results (hare didn't complete for layer X yet)	|   	
|   5	|   Approved	| Green  	| Transaction is approved and will be confirmed with high probability. | Layer # (and ID ?)  	|  Not final. Next possible states: Confirmed, Insufficient Balance 	| TX is in at least one block that was included in HARE results  	|
|   6	|   Confirmed	| Deep Green  	| Transaction is confirmed. | N/A  	| Final.  	| Played into global state (if conflicting transactions exist - this one was selected)   	|   	
|   7	|   Reserved	|   	|   	|   	|   	|   	|
