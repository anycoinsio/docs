# Flexible Amount Deposit

## Overview

This endpoint allows for the creation of a deposit request with a flexible amount for any supported coin or token. It's particularly useful for cases where you need to accept varying amounts of a cryptocurrency from your customers.

## Request

```plaintext
POST https://anycoins.io/api/deposits/free_amount
```

This method accepts the following parameters in the JSON body:

```json
{
    "coin_id": "b18d329f-066f-43ea-9c59-53328e473685",
    "customer_id": "420",
    "permanent_address": false
}
```

- `coin_id`: The ID of the coin (or token), which can be obtained from the [`List Supported Assets`](../info/list-supported-assets.md) method. **Required**.
- `customer_id`: A unique string identifier for the customer within your system. **Required**.
- `permanent_address`: A boolean flag (set to `false` by default) that instructs our processing to reserve a static address for the customer. If this flag is not set, the address pool will be used. For economic reasons, we recommend setting this flag only in special cases, such as for your VIP customers.

## Response Schema

- `id`: The ID of the Deposit.
- `address`: A string containing the ent address.
- `coin`: An object with details about the expected deposit coin (or token).

## Example Request

Replace the `Authorization` header value with your API key.

```bash
curl -X POST \
  -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
  -d '{"coin_id": "b18d329f-066f-43ea-9c59-53328e473685","customer_id":"420"}'
  https://anycoins.io/api/deposits/free_amount
```

## Example Response

```json
{
  "id": "16aeb729-46cd-4e98-bcca-d0619e7b1e23",
  "address": "TC1LrufbG1spBUE1v6fKem4PAaCGm7ah7S",
  "coin": {
    "id": "b18d329f-066f-43ea-9c59-53328e473685",
    "name": "Tether (TRC20)",
    "symbol": "USDT",
    "blockchain": "tron",
    "network": "mainnet",
    "is_token": true,
    "token_contract_address": "TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t",
    "price_eur": "0.9488584359",
  }
}
```
