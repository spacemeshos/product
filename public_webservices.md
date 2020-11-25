# Motivation
- We'd like to deploy 3 web Spacemesh web services and maintain them in a production environment for one long-running Spacemesh testnet and at a later phase for the Spacemesh mainnet and Testnet (total of 2 networks).
- The services are: Public Api Service (grpc API 2.0 and json-http(a grpc gateway over https), the dashboard web app, and the explorer web app.
- The services will be hosted on Google cloud by Spacemesh.
- In addition, a small `discovery service` should always be provided on a well-known friendly url (see below) and provide network info.

---

## Discovery Web Service - Phase I
- The discovery web service provides information about 1 Spacemesh testnet network over a well-known url. The information includes the web services urls for each network as well as friendly network name, id and config file.
- The service should be provided over a permanent url and short Spacemesh domain. e.g. `https://discover.sm.io/` .
- Service must be provided over https and not http.
- Smapp will be configured to use the permanent discovery url to obtain network info such as public api urls, explorer and dash. This url will be the only network related data hard-coded into Smapp.
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

Note that until mainnet, there will only be 1 network block in the data. The data should be updated when a new open testnet is launched.

Here's an example json data for a Spacemesh testnet in the json data.

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
    "latest-smapp-release" : "0.1.13",
    "smapp-base-download-url" : "https://downloads.spacemesh.io",
    "node-base-download-url" : "https://downloads.spacemesh.io",
}]
```

- The discovery data should include the urls for an explorer and dashboard for that network, the network friendly name, its config file and the urls of its json and grpc api services.
- All urls should use friendly domain names and include the network id in them, e.g., `118.explore.spacemesh.io`.
- When a new testnet network is started (e.g., a new public testnet) the system should start services, dash and explorer for it, and update the discovery data with the urls of these services. This should be automated. For phase I, only 1 testnet should be supported at a time.

- `min-node-release` - indicates the minimum go-spacemesh full node release that is supported on that network.
- `latest-node-release` - indicates the most recent node release that is supported on that network.
- `min-smapp-release` - indicates what is the minimum Smapp release that is supported on that network.
- `latest-smapp-release` - indicates the most recent Smapp release that is supported on that network.
- `smapp-base-download-url` - indicates the base path to download new smapp and node releases.

- When a Spacemesh testnet network is terminated, the system should stop its supported web services, free all resources which provided the dash, explore and API services for that network and remove the network information from the discovery service data.

----

## Public API Service - Phase I
- When a new Spacemesh open testnet network is configured to be supported, an API service should be created for it. The discovery service will provide the API service urls for that network.
- The public API service provides one Spacemesh API 2.0 services over the Internet. Two channels should be supported: https-json (json grpc gateway) and a grpc channel.
- The service should only for one deployed Spacemesh open testnet network.
- URLs should be unique per network id, e.g., `https://118.api.sm.io:9092` for the grpc end point for net id 118.
- Both grpc and json endpoints must be provided over https and not http.
- The API service should be provided by one managed full node that connects to a Spacemesh network and is configured to provide the API for that network. (In Phase II we should add load-balanced nodes for increased reliability and uptime).
- The node providing the service should not expose all grpc services such as node and smesher services which are designed to operate a local node by a node owner.
- We need to have monitoring and alerts for an API service, so the backing node can be restarted if needed.
- When a Spacemesh testnet network is deprecated and is going down, the API service for that network should be brought down and the resources used to provide it must be reclaimed.
- Required uptime (SLA): 96.7% (up to 24 hours downtime per cal month).
- Performance: each API service endpoint needs to support up to 20 requests per second from clients.

------

## Explorer and Dash Web Apps - Phase I
- We'd like to provide a public explorer and dashboards for an open testnet network.
- The explorer and dash urls should be unique for the testnet's network id.
- The explorer and dash urls is part of the discovery metadata returned by the discovery web-service. We will setup friendly urls for explore and dash on the DNS level and the service needs to be configured to support them, e.g., `https://118.explore.sm.io` for network id 118 explorer.
- The explorer and dash services should be monitored with alerts and its backend should be restarted in case of failure.
- Required uptime (SLA): 96.7% (up to 24 hours downtime per cal month).
- An explorer and dash service should support up to 20 requests per second from clients.

---

## Flow: Starting Services for a new Spacemesh network
1. A new Spacemesh open testnet network is started with a new net id, e.g., 167.
1. Spacemesh requests public API, dash and explore services to be setup for the new network.
- Spacemesh specifies the exact full-node release that should be used on this network (as docker image or Github branch/tag/commit hash) and the node network config file for the node (part of a node Github release).
1. The web services for an older release of the testnet should be gracefully shutdown and all resources reclaimed.
1. A new dash-backend, explore-backend with supporting nodes, and api-node should be deployed and configured with a command and start being monitored.
1. The discovery service should be updated to provide the meta-data for the new network and stop providing info about the previous open testnet.

Input data for a new network should be provided by Spacemesh as part of the deployment of a new network:
1. Permanent node conf file url.
1. Network id (can be extracted from conf file).
1. Full node and smapp github releases that should be used on this network.

---

## Flow: Stopping Services for a Spacemesh network
1. Spacemesh decides to terminate an open testet network. It requests that services should be decommissioned for that network.
1. The hardware resources providing the services for this network should be decommissioned and the discovery service should be updated to not include the discovery metadata for this network.
1. This flow will happen if we decide to bring down an open testnet before a new one is deployed. It should be rare but may happen.

----

## Flow: Deploying updated full nodes
1. Spacemesh requests to use a new full-node release for a specific network which has live services.
1. Services needs to be updated to use the new node release within 48 hours.
1. The latest release info in the discovery service should be updated with the new release number.

## Flow: Updating users to a new version of Smapp
1. Spacemesh requests to update the latest smapp version for a deployed network.
1. The latest release info in the discovery service should be updated with the new release number.

---

## Flow: Deploying a new Explorer or Dash front-ends
1. Spacemesh requests to deploy new dash and explorer front-end github release for an open testnet to include bug fixes and imrovements in these services.
1. The dash and explore services need to be updated with the new release within 48 hours.
