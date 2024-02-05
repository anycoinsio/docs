# Flexible Amount Deposit

## Overview

This endpoint allows for the creation of a deposit request with a flexible amount for any supported coin or token. It's particularly useful for cases where you need to accept varying amounts of a cryptocurrency from your customers.

## Request

```plaintext
POST https://api.anycoins.io/deposits/CreateFreeAmountDeposit
```

This method accepts the following parameters in the JSON body:

```json
{
    "inCoinId": "b18d329f-066f-43ea-9c59-53328e473685",
    "outCoinId": "b18d329f-066f-43ea-9c59-53328e473685",
    "merchantCustomerId": "420",
    "merchantDepositId": "23069",
    "permanentAddress": false
}
```

- `inCoinId`: The ID of the coin (or token), which can be obtained from the [`List Supported Assets`](../info/list-supported-assets.md) method. **Required.**
- `outCoinId`: The ID of the coin (or token), which can be obtained from the [`List Supported Assets`](../info/list-supported-assets.md) method. **Required.**
- `merchantCustomerId`: A unique string identifier for the customer within your system. **Required**
- `merchantDepositId`: A unique string identifier for the deposit within your system. **Required.**
- `permanentAddress`: A boolean flag (set to `false` by default) that instructs our processing to reserve a static address for the customer. If this flag is not set, new address will be generated for every deposit.

## Response Schema

The response includes details about the deposit transaction:

- `id`: A unique identifier for the deposit
- `inCoin`: An object containing details about the input coin.
- `outCoin`: An object containing details about the output coin.
- `inAddress`: The address to send the input coin to.
- `state`: The current state of the deposit.

   Valid states are:

   - `Pending` - is awaiting to be paid
   - `Processing` - paid, swapping to `out` coin
   - `Completed` - paid (+ swapped, if needed)
   - `Expired` - canceled on timeout (24 hours for now)

- `merchantCustomerId`: ID of the customer on merchant's side.
- `merchantDepositId`: ID of the deposit on merchant's side.
- `createdAt`: Timestamp of when the deposit was created.
- `stateChangedAt`: Timestamp of when the deposit state was last time changed.

## Example Request

Replace the `Authorization` header value with your API key.

```bash
curl -X POST \
    -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
    -d '{"inCoinId": "96592fb8-1466-41d9-b204-6eccf61e0745", "outCoinId": "96592fb8-1466-41d9-b204-6eccf61e0745", "merchantCustomerId": "420", "merchantDepositId": "23069"}' \
    https://api.anycoins.io/deposits/CreateFreeAmountDeposit
```

## Example Response

```json
{
  "id": "2fc77d13-88ee-4517-881e-b15daaf7c3b5",
  "kind": "FreeAmount",
  "inCoin": {
    "id": "130f1fe6-09ad-4118-89f7-ab8e5612b13d",
    "name": "Tether USD",
    "symbol": "USDT",
    "blockchain": "Tron",
    "decimals": 6,
    "tokenContractAddress": "TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t",
    "deposit": {
      "isInEnabled": true,
      "isOutEnabled": true
    },
    "swap": {
      "isInEnabled": true,
      "isOutEnabled": true
    }
  },
  "outCoin": {
    "id": "130f1fe6-09ad-4118-89f7-ab8e5612b13d",
    "name": "Tether USD",
    "symbol": "USDT",
    "blockchain": "Tron",
    "decimals": 6,
    "tokenContractAddress": "TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t",
    "deposit": {
      "isInEnabled": true,
      "isOutEnabled": true
    },
    "swap": {
      "isInEnabled": true,
      "isOutEnabled": true
    }
  },
  "inAddress": "TYWjHGvEu4rrCeqvtTwcQC58NWTgWuM5cb",
  "state": "Pending",
  "merchantCustomerId": "420",
  "merchantDepositId": "23069",
  "createdAt": "2024-02-05T20:09:25.385987Z"
}
```
