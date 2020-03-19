---
id: node-client
title: Zeebe Node Client
---

The [Zeebe Node Client](https://github.com/creditsenseau/zeebe-client-node-js) exists for node applications. The client can be used for self-hosted Zeebes as well as for a connection to Camunda Cloud.

The GitHub repository contains detailed documentation on how to use the client. The connection to Camunda Cloud can be established using environment variables with the [Zero-Conf Constructor](https://github.com/creditsenseau/zeebe-client-node-js#zero-conf-constructor).

## Examples

### Get status

As in the [`zbctl` example](./connectzeebe_cli-zbctl.md), a [client](./zeebecluster_clients.md) must first be created. Then the environment variables can be set.

Set up a new `npm` project:

```bash
mkdir zeebe-node-example
cd zeebe-node-example
npm init
```

Now install the node client:

```bash
npm i --save zeebe-node
```

Create an `index.js`:

```bash
touch index.js
```

Use the following code to get the status of your Zeebe cluster:

```js
const ZB = require("zeebe-node");

const zbc = new ZB.ZBClient();

async function getStatus() {
  const topology = await zbc.topology();
  console.log(JSON.stringify(topology, null, 2));
}

getStatus();
```

Execute the code (note: remember to set the environment variables first, otherwise you'll get a 403)

```bash
node index.js
```

You should now receive a similar output:

```json
{
  "brokers": [
    {
      "partitions": [
        {
          "partitionId": 2,
          "role": "LEADER"
        },
        {
          "partitionId": 1,
          "role": "LEADER"
        }
      ],
      "nodeId": 0,
      "host": "zeebe-0.zeebe-broker-service.e2f9117e-e2cc-422d-951e-939732ef515b-zeebe.svc.cluster.local",
      "port": 26501
    }
  ],
  "clusterSize": 1,
  "partitionsCount": 2,
  "replicationFactor": 1
}
```

## Create a service task worker

If you want to implement a custom worker you can find documentation [in the repository](https://github.com/creditsenseau/zeebe-client-node-js#create-a-task-worker). A simple worker, that produces console output, looks like this:

```js
const ZB = require("zeebe-node");

const zbc = new ZB.ZBClient();

zbc.createWorker(null, "custom-worker", (job, complete) => {
  // Task worker business logic goes here
  console.log("Task variables", job.variables);
  complete.success(`custom worker!`);
});
```
