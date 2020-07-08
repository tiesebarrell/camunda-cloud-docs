---
id: cli-zbctl
title: CLI
---

`zbctl` is the command line interface to interact with Zeebe in the cloud. After installation, a connection can be tested immediately.

## Installation

An installation can be done quickly via the package manager `npm`. The corresponding package is [here](https://www.npmjs.com/package/zbctl).

```bash
npm i -g zbctl
```

You can also download a binary for your Operating System from the [Zeebe GitHub Releases page](https://github.com/zeebe-io/zeebe/releases).

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

## Advanced Workflow

Use [This workflow model](./assets/gettingstarted_quickstart_advanced.bpmn) for the tutorial.

![processId](./assets/zeebe-modeler-advanced-process-id.png)

This workflow includes a Service Task and an XOR Gateway. Select the Service Task and fill in the properties. Set the task-type to 'test-worker'. 

![workflow](./assets/zeebe-modeler-advanced.png)

The worker will return a JSON object as a result, which is used to decide which path to take. 
Now, we can use the JSON object to route your process by filling in the condition expression on the two sequence flows after the XOR gateway. 

Use the following expression for the "Pong" sequence flow: 
```bash
=return="Pong"
```
And for the Else Sequence flow:
```bash
=return!="Pong"
```

![sequenceflows](./assets/zeebe-modeler-advanced-sequence-flows.png)

## Deploy workflow with zbctl

Go back to your cloud account and select your created cluster. Navigate to the client section of the cluster details. Use the button `Show connection info` to display all required export statements for environment variables. 

Set the environment variables accordingly to your operation system. 

OR use the [described flags](https://www.npmjs.com/package/zbctl#usage) (`--address`, `--clientId` and `--clientSecret`). with the zbctl commands

Test the connection by printing out the topology (after setting the enviroment variables):

```bash
zbctl status
```

OR if you haven't set the environment variables use the following pattern: 
```bash
zbctl status --address xxxxx --clientId xxxxx --clientSecret xxxxx
```

As a result, you should see:

```bash
Cluster size: 1
Partitions count: 1
Replication factor: 1
Gateway version: 0.23.1
Brokers:
  Broker 0 - zeebe-0.zeebe-broker-service.0e65413b-cc0d-4b9a-9bfb-7b30f81a739a-zeebe.svc.cluster.local:26501
    Version: 0.23.1
    Partition 1 : Leader
```

Now you can deploy the [workflow](./assets/gettingstarted_quickstart_advanced.bpmn). Navigate to the folder, where you saved your workflow. 

```bash
zbctl deploy gettingstarted_quickstart_advanced.bpmn
```

If the deployment is successful you'll get the following output:

```bash
{
  "key": 2251799813685493,
  "workflows": [
    {
      "bpmnProcessId": "camunda-cloud-quick-start-advanced",
      "version": 1,
      "workflowKey": 2251799813685492,
      "resourceName": "gettingstarted_quickstart_advanced.bpmn"
    }
  ]
}
```

Important here is the `bpmnProcessId`, which you'll need for creating a new instance.

## Register a worker

The workflow uses the worker with the type `test-worker`. Register a new one by using the following command:

```bash
zbctl create worker test-worker --handler "echo {\"return\":\"Pong\"}"
```

## Start a new instance

You can start a new instance with a single command:

```bash
zbctl create instance camunda-cloud-quick-start-advanced
```

As a result, you'll get the following output, which contains, among others, the `workflowInstanceKey`:

```bash
{
  "workflowKey": 2251799813685492,
  "bpmnProcessId": "camunda-cloud-quick-start-advanced",
  "version": 1,
  "workflowInstanceKey": 2251799813685560
}
```

Navigate to Operate to monitor the workflow instance.

![operate-instances](assets/operate-advanced-instances-pong.png)

Because the worker returns

```json
{
  "return": "Pong"
}
```

the workflow ends in the upper end event.

Changing the worker to

```bash
zbctl create worker test-worker --handler "echo {\"return\":\"...\"}"
```

and creating a new instance leads to a second instance in Operate, which you'll see ending in the second end event:

![operate-instance](assets/operate-advanced-instances-other.png)

As a next step you can now connect both workers in parallel and create more workflow instances:

```bash
while true; do zbctl create instance camunda-cloud-quick-start-advanced; sleep 1; done
```

In Operate you will see instances ending in both end events depending on which worker picked up the job.

![operate-instances](assets/operate-advanced-instances.png)
