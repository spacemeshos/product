# Spacemesh API design and methodology

[Master API](https://docs.google.com/spreadsheets/d/1P89OVWdgJocPy0CGM43Ge7Sx_6dabCBEagaVQfOk9us/edit)

	Facade Design Method																												
	1. Seperate full node and archive node mesh data apis even if the facade is similar. e.g. mesh data and not just make some methods available in a facade based on node mode.																												
	2. Carve out facades that modify behavior for security considirations - nodes operators will need to enable them explicitly when they want them to be used...																												
		any facade that can modify node behavior should be expliclity turned on by a node via cli flag. On the api design level it means seperate from other readonly facades																											
																													
	Interesting questoins...																												
	- Are receipts and events only stored by archive nodes? Issue if they are needed to validate a layer state... (in eth they are part of consensus)																												
	- What about layer and epoch hashes...																												
																													
	Large data sets support																												
	- Every method which returns list of data must support pagination - only return a default # of items + return a field with the number of items returned and support calling it with an offset to retreieve additional items... NTH: User can specify how many results to retrieve up to a max of say 100 and if he's not specifying it a default is used. e.g. 50. Otherwise: always return up to 20 items (constant) at an offset....																												
																													
	Naming pattern:	component.sub-scomponent.method-name																											
																													
	Design Idea																												
	- Full nodes store historical data of up to n=200 layer or something like that but older information must be retrieved from archive nodes....																												
	- So wallets for example, will not have full TX history of account, only recent one and if you want to see older ones you need to look at public explorer which gets data from archive nodes...																												
	- W/o this design full node may need to have very large indexes. e.g. all tx by each account since genesis.... all rewards to every smesher since genesis!																												
																													
	Lots of the API design isssues are due to lack of decision on layer and epoch canonical state and rewards as part of consensus.  We have to resolve this.																												
	Is canical state part of layer data? epoch data?																												
	Also - if smart contract txs events and receipts are NOT part of canonical state - how can a node know that the data he's getting from other nodes is correct?																												
	We need self-authenticated data structures like in eth - where all data is pretty much secured by 1 state root hash which is part in the canonical state - I don't know of a way around this....																												
Stream: GRPC only - no json / http
