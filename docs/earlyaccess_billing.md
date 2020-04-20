---
id: early-access-billing
title: Billing
---

The Early Access Plan consists of a fixed monthly base fee and a usage-based value. The usage-based part is calculated as follows:

Every day (GMT+2) the maximum set reservations per cluster configuration are determined. These are multiplied by the price (broken down to the daily price of each month) of the respective cluster configuration and added up according to the month. You will receive a monthly invoice from us.

## Example

*Note: Fictitious values are used to better understand calculation.*

**Basis**

- Basic fee: 1000 Euro
- Cluster configuration A: 300 Euro
- Cluster configuration B: 900 Euro

**Reservation updates**

| Day of month                 | Updated reservations for A | Updated reservations for B |
| ---------------------------- | -------------------------- | -------------------------- |
| reservations from last month | 2                          | 1                          |
| 11, 10:00                    | 3                          | 2                          |
| 11, 17:00                    | 5                          | 2                          |
| 21, 09:00                    | 4                          | 3                          |

**Results in the following calculation (for a month with 30 days)**

| Day of month | Price A | Price B | Sum |
| ------------ | ------- | ------- | --- |
| 1            | 20      | 30      | 50  |
| ...          | 20      | 30      | 50  |
| 10           | 20      | 30      | 50  |
| 11           | 50      | 60      | 110 |
| ...          | 50      | 60      | 110 |
| 20           | 50      | 60      | 110 |
| 21           | 40      | 90      | 130 |
| 30           | 40      | 90      | 130 |

**Invoice**

- Basic Fee: 1000 Euro
- Price A: 2900 Euro
