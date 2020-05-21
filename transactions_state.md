# Coin Transfer Transaction States

## Overview
This document details the possible states of coin transfer transactions for the open testnet timeframe.

## Status
WIP / Early Draft

## Status codes - Summary Table

| status_code 	| State Label and Color 	| User-facing Explanation                                              	| User-facing recommended next step...                                       	| Technical Explanation                                                                                           	| Possible next state                     	| State Metadata                 	|
|-------------	|-----------------------	|----------------------------------------------------------------------	|----------------------------------------------------------------------------	|-----------------------------------------------------------------------------------------------------------------	|-----------------------------------------	|--------------------------------	|
| 0           	| Rejected              	| Transaction was rejected and can't be further processed.             	| Create a new transaction with same dest address and amount.                	| Submmited TX was rejected by the full node due failed validation. It will not be broadcasted to the network.    	| n/a                                     	| Maybe validation error string? 	|
| 1           	| Insufficient Balance  	| Insufficient account balance to execute this transaction.            	| Add funds to your account and send a new tx to dest address w same amount. 	| Once funds are available, tx may continue processing and move to any other state.                               	| ANY                                     	| n/a                            	|
| 2           	| Conflicting           	| Another transaction with the same counter is pending.                	| Wait for change of status for one of these txs ?                           	| One of the transactions may be processed.                                                                       	| Pending, Processing, Confirmed           	| Conflicting tx id              	|
| 3           	| Pending               	| Waiting for transactions to be added to the mesh.                  	  | Wait until tx is processing.                                               	| Submitted to mempool and was not rejected - not in block yet (e.g. was in block, but was not applicable)        	| Processing                              	| n/a                            	|
| 4           	| Processing            	| Transaction is processing and pending approval.                      	| Wait until processing is done for futher status                            	| In at least one block in layer X that was not excluded from hare results (hare didn't complete for layer X yet) 	| Confirmed, Pending, Insufficient Balance 	| Layer # and ID ?               	|
| 5           	| Confirmed              	| Transaction is confirmed and will be finalized with high probability. | Wait until confirmed.                                                     	| TX is in at least one block that was included in hare results                                                   	| Confirmed, Insufficient Balance         	| Layer # and ID ?               	|
| 6           	| Finalized             	| Transaction is confirmed and finalized.                              	| n/a                                                                        	| Played into global state (if conflicting transactions exists - this one was selected)                           	| n/a                                     	| Layer # and ID ?               	|
