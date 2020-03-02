# Command Line Interface: `zbctl`

`zbctl` is the command line interface to interact with Zeebe in the cloud. After installation, a connection can be tested immediately.

## Installation

An installation can be done quickly via the package manager `npm`. The corresponding package is [here](https://www.npmjs.com/package/zbctl).

```bash
npm i -g zbctl
```

## Usage

A detailed documentation about zbctl can be found [here](https://github.com/jwulf/zbctl#readme).

Basically: After creating a client, `export` statements are displayed which set all necessary environment variables. If these are known to the system, `zbctl` can communicate directly with its own cluster in the cloud without further configuration.

### Example to get status

```bash
zbctl status
```

As a result you will get a similar result:

```bash
Cluster size: 1
Partitions count: 2
Replication factor: 1
Gateway version: unavailable
Brokers:
  Broker 0 - zeebe-0.zeebe-broker-service.456637ef-8832-428b-a2a4-82b531b25635-zeebe.svc.cluster.local:26501
    Version: unavailable
    Partition 1 : Leader
    Partition 2 : Leader
```

An example for deploying a workflow and creating a new instance is explained in the [Quick start](./gettingstarted_quick-start.md) guide.
