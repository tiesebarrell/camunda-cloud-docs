---
id: camunda-cloud-console
title: Camunda Cloud Console
---

Camunda Cloud serves as an umbrella for the next generation of Camunda products. The cloud console is the control center for these products.

Zeebe clusters can be created and operated via the cloud console. For each Zeebe cluster, the following products are provided:

- [Zeebe](./zeebecluster_zeebe.md)
- [Operate](./zeebecluster_operate.md)

The products are always delivered in the lastest available stable version. The Zeebe version can be viewed in the cluster details.

The provisioning of a Zeebe cluster takes about two minutes. As soon as a Zeebe cluster is operational, its state jumps from _Creating_ to _Healthy_.

To interact with Zeebe, an application must authenticate itself via OAuth. A [client](./zeebecluster_clients.md) must be created in advance for this purpose.

## Rights concept

When a user signs up to Camunda Cloud, they receive a personal organization. Clusters that the user creates in this organization are assigned to this organization.

If several users need access to the same Zeebe cluster, all users can be assigned to the same organization. If a user is assigned to more than one organization, the organization can be changed in the avatar menu of the navigation bar.

![avatar-menue-multiple-organisations](./assets/avatar-menue-multiple-organisations.png)

## Organization Settings

Organization settings can be accessed via the menu in the navigation bar.


![avatar-menue](./assets/avatar-menue.png)

### Overview

The overview provides a summary of the organization:

- Organization name
- Pricing Plan
- Owner of the organization

### Users

Under this setting members of the current organization can be managed. A user can have one of the following roles:

- Owner: Owner of the organization (currently limited to one user, cannot be changed by the user)
- Admin: Restricted rights for user management
- Member: Can manage Zeebe Clusters and Client and use Operate

The following table illustrates the rights of the each roles:

|                              | Owner | Admin | Member |
| ---------------------------- | ----- | ----- | ------ |
| Manage Zeebe Clusters        | X     | X     | X      |
| Manage Clients               | X     | X     | X      |
| Use Operate                  | X     | X     | X      |
| Users: Manage Members        | X     | X     |        |
| Billing: Manage Reservations | X     | X     |        |
| Billing: Request Paid Plan   | X     | X     |        |
| Users: Manage Admins         | X     |       |        |

Users are invited to a Camunda cloud organisation via their email address, which must be accepted by the user. As long as the invitation has not been accepted, the user remains in the Pending state.

People can also be invited to an organisation that does not yet have a Camunda cloud account. In this case the invited person must first create a Camunda Cloud account and then has access to the organisation.

### Billing

This setting is only visible in the Professional Plan for Owners and Admins. More about it under [Managing Reservations](professional_reservations.md).
