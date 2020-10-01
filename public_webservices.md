# Motivation
We'd like to deploy 3 web Spacemesh web services and maintain them in a production environment. The services will be hosted on Google cloud by Spacemesh. The services are: public api service, dash web app and explore web app. In addition, a small discovery service should always be provided on a well-known friendly url (see below).

## Public API Service - Phase I
The public API service provides some Spacemesh API 2.0 services over the Internet via a json-http interface.
- The service is configured with endpoints to one or more Spacemesh networks such as open testnet and devnets.
- Each end-point should have its own permanent unique url and we'll map a custom domain to it.
- All api services must be provided over https and not http.
- The overall service needs to be configurable to easily add or remove networks. e.g. add a devnet, add a new open testnet.
- Each network API should be provided by one managed full node that connects to a Spacemesh network and is configured to provide the API for that network.
- We need to have monitoring and alerts for each network so backing node can be restarted if needed.
- Required uptime (SLA): 96.7% (up to 24 hours downtime per cal month).
- Each endpoint needs to support up to 20 requests per second from clients.
- We need to add a small `discovery web service` that provides a list of available endpoints on a static public url in json. e.g. `https://apis.sm.io` . Smapp will be configured to use this url to obtain available API for various networks.

```json
[{
    "net-friendly-name": "TweedleDee Open Testnet 118",
    "net-id" : 118,
    "api-url": "https://118.api.sm.io:9091",
    "explorer-url" : "https://118.explore.sm.io",
    "dash-url" : "https://118.dash.sm.io",
}, ...]
```

Note that the discover file also provides the urls for an explorer and dashboard for that network. Each network that has a public API service, should also provide dash and explore for that network.

Note that for explorer and dash we'd like to provide domains in the urls and not the raw public IP address of these services.

- When a new network is started that we'd like to have a public API for, it needs to be added to the API service and the discovery web service needs to be updated to provide the meta-data for the network.
- When a network is terminated, we need to remove the managed node that provided the API, from the API service and the discovery service.

## Explorer and Dash Web Apps - Phase I
- We'd like to provide a public explorer and dashboards for some networks such as open testnet and devnets. Each network which provides a public API should also provide an explorer for that network.
- The explorer and dash urls is part of the discovery meta-data returned by the discovery web-service. We will setup friendly urls for explore and dash on the DNS level and the service needs to be configured to support them. e.g. `https://118.explore.sm.io` for network id 118 explorer.
- The explorer and dash services should be monitored with alerts and its backend should be restarted in case of failure.
- Required uptime (SLA): 96.7% (up to 24 hours downtime per cal month).
- An explorer and dash service should support up to 20 requests per second from clients.
- The Explorer and Dashboard web apps should enable users to switch between all deployed networks via the network dropdown.

## Flow: Starting Services for a new Spacemesh network
1. A new Spacemesh network is started with a new net id. e.g. 167.
2. Spacemesh requests public API, dash and explore to be setup for the new network. It provides the friendly url for the new services. e.g. `https://167.api.sm.io` for API, `https://167.dash.sm.io` for Dash, adn `https://167.explore.sm.io` for explorer. Spacemesh specifies the exact full-node release that should be used on this network and the node network config file for the node (part of node github release).
3. A new dash-backend, explore-backend with supporting nodes, and api-node needs should be deployed and configured and start being monitored.
4. The discovery service should be updated to provide the meta-data for the new network.

## Flow: Stopping Services for a new Spacemesh network
1. Spacemesh decides to terminate a network. It requests that services should be decommissioned for that network.
2. The hardware resources providing the services for this network should be decommissioned and the discovery service should be updated to not include the discovery meta-data for this network.

## Flow: Deploying updated full nodes
1. Spacemesh requests to use a new full-node release for a specific network which has live services.
2. Services needs to be updated to use the new node release in up to 48 hours.

## Flow: Deploying a new Explorer or Dash front-ends
1. Spacemesh requests to deploy new dash and explore front-end github release for all live networks.
2. The dash and explore services needs to be updated with the new release in up to 48 hours.
