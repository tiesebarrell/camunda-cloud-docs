# Camunda Cloud Console

## Console Overview

Camunda Cloud serves as a umbrella for the next generation of Camunda products. The Cloud Console is the control centre for these products.

Components of the Console

Zeebe clusters can be created and operated via the cloud console. For each Zeebe cluster, the following products are provided:

* [Zeebe](./zeebecluster_zeebe.md)
* [Operate](./zeebecluster_operate.md)
* [HTTP Worker](./zeebecluster_embedded-http-worker.md)

The products are always delivered in the last available stable version. The Zeebe version can be viewed in the cluster details.

The provisioning of a Zeebe cluster takes about two minutes. As soon as a Zeebe cluster is operational, its state jumps from *Unhealthy* to *Healthy*.

To interact with Zeebe, an application must authenticate itself via OAuth. A [client](.zeebecluster_clients.md) must be created in advance for this purpose.

## Rights concept

When a user signs up to Camunda Cloud, he or she receives a personal organization. Clusters that the user creates in this organization are assigned to this organization.

If several users need access to the same Zeebe cluster, all users can be assigned to the same organization. A corresponding organisation management for users is planned, but not yet implemented. If it is already necessary for your project, please contact the Camunda Cloud Team.

If a user is assigned to more than one organization, the organization can be changed in the avatar menu of the navigation bar.
