---
id: cloudapi-endpoints
title: Endpoints
---

For all requests include the access token for Cloud API into the Authorization header: `authorization:Bearer ${TOKEN}`

# Clusters
## GET all Clusters
`GET https://console.cloud.camunda.io/customer-api/clusters/`
Returns detailed Data on all clusters of the Organization

## Get Cluster
`GET https://console.cloud.camunda.io/customer-api/clusters/${uuid}`
Returns detailed Data on one cluster.

## Get Cluster creation parameters
`GET https://console.cloud.camunda.io/customer-api/clusters/parameters`
Returns all options available to create a cluster.

## Delete Cluster
`DELETE https://console.cloud.camunda.io/customer-api/clusters/${uuid}`

## Create Cluster
`POST https://console.cloud.camunda.io/customer-api/clusters/`
With following JSON payload:
```
{
    name: string,           // Name of the Cluster
    channelId: string,      // Software Channel for further upgrades, check Get creation parameters
    generationId: string,   // Software Generation, check Get creation parameters
    regionId: string,       // Region to host the cluster, check Get creation parameters
    planTypeId: string,     // Hardware Plan of the cluster, check Get creation parameters
}
```

# Zeebe Clients
## Get all Zeebe Clients
`GET https://console.cloud.camunda.io/customer-api/clusters/${clusterUuid}/clients/`
List all Zeebe Clients

## Get Zeebe Client Details
`GET https://console.cloud.camunda.io/customer-api/clusters/${clusterUuid}/clients/${clientId}`
Returns the all data needed to connect to a cluster

## Delete Zeebe Client
`DELETE https://console.cloud.camunda.io/customer-api/clusters/${clusterUuid}/clients/${clientId}`
Delete a Zeebe Client

## Create Zeebe Client
`POST https://console.cloud.camunda.io/customer-api/clusters/${clusterUuid}/clients/`
With following JSON payload:
```
{
    clientName: string,     // Name of the ZeebeClient
}
```

This returns:
```
{
    name: string,
    clientId: string,
    clientSecret: string,
}
```

