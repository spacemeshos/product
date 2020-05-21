# Dashboard Spec

## Visual Design - Desktop Class Screens
![](https://raw.githubusercontent.com/spacemeshos/product/master/resources/dashboard_visual_design.png)

## Requirements
- Dynamic webpage designed for desktop-class screens with a fallback to a mobile layout.
- Real time updates from the mesh - update every 5 minutes.
- Dashboard is always connected to a specific network. e.g. Open Testnet 0.1, Mainent, etc...
- We need to be able to deploy and display a dashboard for different testnets and mainnets.

## Dashboard Modules

### Active Smeshers
Main display: Number of active smeshers in the current epoch. Active smeshers are smeshers who have submitted at least one block in one layer in that epoch.

Graph: change over time, x-axis: epoch. y-axis: number of active smeshers.

### Accounts
Main display: Total number of on-mesh accounts with a non-zero coin balance as of the current epoch.
Graph: change over time, x-axis: epoch. y-axis: total number of accounts.

### Smeshing Rewards
Main display: Total amount of Smesh minted as mining rewards as of the last known reward distribution event.
Graph: change over time, x-axis: epoch. y-axis: total smeshing rewards until and including that epoch.

### Circulation
Main display: Total number of Smesh coins in circulation. This is the total balances of all on-mesh accounts.
Graph: change over time, x-axis: epoch. y-axis: total number of smesh coins in circulation as of the end of that epoch.
Note: the difference between this and the rewards module is that circulation includes any pre-minted coins at genesis.

### Age
Main display: Elapsed time since genesis time of the network.

### Layer / Epoch
Main display: Current layer number and current epoch number (0-indexed since genesis)

### Transactions
Main display: total number of transactions processed by the state transition function - e.g. reflected in global state as of the last state transition function (not txs on the mesh in blocks). Should exclude ATX transactions.
Graph: x-axis: epoch. y-axis: total number of txs processed by the state transition function up to the end time of that epoch.

### Security
Main display: total amount of storage committed to the network based on the ATXs in the previous epoch.
Graph: x-axis: epoch. y-axis: total amount of storage as of the epoch start time (atxs in previous epoch).

### Decentralization
TBD - distribution of storage between all active smeshers. Measurement of how long is the tail.

### TX/s / Capacity
Main display: average tx/s rate over capacity considering all layers in the current epoch. Only processed transactions by the state transition function and not transactions in blocks should be counted. Capacity is defined as the theoretical upper-bound on tx/s based on the network params.
Graph: x-axis: epoch. y-axis: same ratio as main display for that epoch.


### Live Smeshers Map View
This is a live heat map of smeshers from around the globe.
For a testnet, smeshers can opt-out from reporting ip address for geo-location via the app settings. For a mainnet, smeshers can opt-in to report ip address for geo-location. Nodes show as hot spots over the world's map. The goal of this module is not to identify specific smeshers but to display a measure of the geographic distribution aspect of decentralization.
