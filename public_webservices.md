# Motivation
- We'd like to deploy 3 web Spacemesh web services and maintain them in a production environment for each Spacemesh network (such as devnet or open tetnet).
- The services are: Public Api Service (grpc and json over  https), dashboard web app, and explorer web app.
- The services will be hosted on Google cloud by Spacemesh.
- In addition, a small `discovery service` should always be provided on a well-known friendly url (see below).
- The services should be managed by a system that enables auto deployment of the services for a new Spacemesh network, auto removal of services for a network that is being shut down, and auto updates to the discovery service to indicate the currently supported networks and their services.

---

## Discovery Web Service - Phase I
- The discovery web service provides a list of available Spacemesh networks, the web services urls for each network as well as friendly network name, id and config file.
- The service should be provided over a permanent url and short Spacemesh domain. e.g. `https://discover.sm.io/` .
- Service must be provided over https and not http.
- Smapp will be configured to use this url to obtain a list of available networks and the urls for a network's public api, explorer and dash. This url will be the only network related data hard-coded into Smapp.
- The service should return json data in a well-known format such as:

```json
[{
    // net-1-data...
    },
    {
        // net-2-data...
    }, ...
]
```

Here's an example of an entry for a Spacemesh network in the json data:

```json
[{
    "net-name": "TweedleDee Open Testnet 118",
    "net-id" : 118,
    "conf": "https://sm.io/nets/118/conf.json"
    "api-json": "https://118.api.sm.io:9091",
    "api-grpc": "https://118.api.sm.io:9092",
    "explorer" : "https://118.explore.sm.io/",
    "dash" : "https://118.dash.sm.io/",
    "min-node-release" : "0.1.1",
    "latest-node-release" : "0.1.2",
    "min-smapp-release": "0.1.12",
    "latest-smapp-release" : "0.1.13"
}, ...]
```

- The discovery data should include the urls for an explorer and dashboard for that network, the network friendly name, its config file and the urls of its json and grpc api services.
<<<<<<< HEAD
- All urls should use friendly domain names and include the network id in them, e.g., `118.explore.spacemesh.io`.
- When a new supported network is started (e.g., a new public testnet) the system should start services, dash and explorer for it, and update the discovery data with the urls of these services. This should be automated.
- Min-node-version indicates what is the minimum go-spacemesh full node release that is supported on that network.
- Note that we don't include node release URLs here as Smapp full node updates is handled via a different mechanism. We include the min-version to ensure that Smapp will enable users to join a network only if they have compatible node software installed.
=======
- All urls should use friendly domain names and include the network id in them. e..g `118.explore.spacemesh.io`.
- When a new supported network is started (e.g a new public testnet) the system should start services, dash and explorer for it, and update the discovery data with the urls of these services. This should be automated.
- `min-node-release` indicates what is the minimum go-spacemesh full node release that is supported on that network.
- `latest-node-release` indicates the most recent node release that is supported on that network.
- `min-smapp-release` indicates what is the minimum Smapp release that is supported on that network.
- `latest-smapp-release` indicates the most recent Smapp release that is supported on that network.

- Note that we don't include node release ulrs here as Smapp full node updates is handled via a different mechanism. We include the min-version to ensure that Smapp will enable users to join a network only if they have a compatible managed node installed.
>>>>>>> 6802404 (Update to include release versions)
- When a Spacemesh network is terminated, we need to stop its supported services, free all resources which provided the dash, explore and API services for that network and remove the network information from the discovery service data.

----

## Public API Service - Phase I
- When a new Spacemesh network is configured to be supported, an API service should be created for it. The discovery service will provide the API service urls for that network.
- The public API service provides one or more Spacemesh API 2.0 services over the Internet via both https-json and https-grpc channels.
- The service should be provided for each supported Spacemesh network, e.g., a devnet or a testnet.
- It should have its own permanent unique url and we'll map a custom domain to it, e.g., `https://118.api.sm.io:9092` for the grpc service for net id 118.
- Both grpc and json endpoints must be provided over https and not http.
- The API service should be provided by one managed full node that connects to a Spacemesh network and is configured to provide the API for that network. (In Phase II we should add load-balanced nodes for increased reliability and uptime).
- We need to have monitoring and alerts for an API service, so the backing node can be restarted if needed.
- When a Spacemesh network is deprecated and is going down, the API service for that network should be brought down and the resources used to provide it must be reclaimed.
- Required uptime (SLA): 96.7% (up to 24 hours downtime per cal month).
- Each API service endpoint needs to support up to 20 requests per second from clients.

------

## Explorer and Dash Web Apps - Phase I
- We'd like to provide a public explorer and dashboards for some networks such as open testnet and devnets. Each network which provides a public API should also provide an explorer for that network.
- The explorer and dash urls is part of the discovery metadata returned by the discovery web-service. We will setup friendly urls for explore and dash on the DNS level and the service needs to be configured to support them, e.g., `https://118.explore.sm.io` for network id 118 explorer.
- The explorer and dash services should be monitored with alerts and its backend should be restarted in case of failure.
- Required uptime (SLA): 96.7% (up to 24 hours downtime per cal month).
- An explorer and dash service should support up to 20 requests per second from clients.
- The Explorer and Dashboard web apps should enable users to switch between all deployed networks via the network dropdown.

---

## Flow: Starting Services for a new Spacemesh network
1. A new Spacemesh network is started with a new net id, e.g., 167.
1. Spacemesh requests public API, dash and explore to be setup for the new network.
- Spacemesh specifies the exact full-node release that should be used on this network (as docker image or Github branch/tag/commit hash) and the node network config file for the node (part of a node Github release).
1. A new dash-backend, explore-backend with supporting nodes, and api-node should be deployed and configured with a command and start being monitored.
1. The discovery service should be updated to provide the meta-data for the new network.

Input data for a new network should be provided by Spacemesh as part of the deployment of a new network:
1. Permanent node conf file url.
1. Network id (can be extracted from conf file).
1. Full node github release that should be used on this network.

---

## Flow: Stopping Services for a Spacemesh network
1. Spacemesh decides to terminate a network. It requests that services should be decommissioned for that network.
1. The hardware resources providing the services for this network should be decommissioned and the discovery service should be updated to not include the discovery metadata for this network.

----

## Flow: Deploying updated full nodes
1. Spacemesh requests to use a new full-node release for a specific network which has live services.
1. Services needs to be updated to use the new node release within 48 hours.

---

## Flow: Deploying a new Explorer or Dash front-ends
1. Spacemesh requests to deploy new dash and explorer front-end github release for all live networks.
1. The dash and explore services need to be updated with the new release within 48 hours.
