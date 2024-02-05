# Get Deposit

## Overview

The `POST /deposits/GetDeposit` endpoint is designed to allow merchants to check the current state of an existing deposit. This is essential for tracking the progress of a deposit and for auditing purposes.

## Request

```plaintext
POST https://api.anycoins.io/deposits/GetDeposit
```

This method requires the unique identifier of the deposit in a JSON body.

- `id`: The unique identifier (UUID) of the deposit. **Required.**

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

Replace id in the data with the actual ID of the deposit transaction and the Authorization header value with your API key.

```bash
curl -X POST \
    -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
    -d '{"id": "2fc77d13-88ee-4517-881e-b15daaf7c3b5"}'
    https://api.anycoins.io/deposits/GetDeposit
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
