# Get Swap

## Overview

The `GET /api/swaps/:id` endpoint is designed to allow users to check the current state of an existing swap. This is essential for tracking the progress of a swap transaction and for auditing purposes.

## Request

```plaintext
GET https://anycoins.io/api/swaps/:id
```

This method requires the unique identifier of the swap transaction as a URL parameter.

- `:id`: The unique identifier (UUID) of the swap transaction. **Required.**

## Response Schema

The response for this endpoint returns a SwapResponse object, which includes the following fields:

- `id`: The unique identifier (UUID) of the swap transaction.
- `inCoin`: An object containing details about the input coin for the swap.
- `outCoin`: An object containing details about the output coin for the swap.
- `inAddress`: A string representing the address for sending the input coin.
- `outAddress`: A string representing the address where the output coin will be sent.
- `state`: A string indicating the current state of the swap (e.g., `pending`, `completed`, `failed`).
- `inAmount`: The amount of input coins that were swapped.
- `outAmount`: The amount of output coins that were received.
- `createdAt`: A timestamp indicating when the swap was created.
- `stateChangedAt`: Timestamp of when the swap state was last time changed.

## Example Request

Replace `:id` in the URL with the actual ID of the swap transaction and the Authorization header value with your API key.

```bash
curl -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
    https://anycoins.io/api/swaps/16aeb729-46cd-4e98-bcca-d0619e7b1e23
```

## Example Response

```json
{
  "id": "16aeb729-46cd-4e98-bcca-d0619e7b1e23",
  "inCoin": {
    "id": "611ba4b6-09e4-4ead-bc0e-6c6b970810f7",
    "name": "Bitcoin",
    "symbol": "BTC",
    "blockchain": "Bitcoin",
    "isEnabled": true,
    "swap": {
        "isInEnabled": true,
        "isOutEnabled": true
    }
  },
  "outCoin": {
    "id": "130f1fe6-09ad-4118-89f7-ab8e5612b13d",
    "name": "Tether (TRC20)",
    "symbol": "USDT",
    "blockchain": "Tron",
    "isEnabled": true,
    "tokenContractAddress": "TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t",
    "swap": {
        "isInEnabled": true,
        "isOutEnabled": true
    }
  },
  "inAddress": "1BoatSLRHtKNngkdXEeobR76b53LETtpyT",
  "outAddress": "0xde0B295669a9FD93d5F28D9Ec85E40f4cb697BAe",
  "state": "Pending",
  "inAmount": "0.0042",
  "outAmount": "0.069",
  "createdAt": "2023-11-11T12:00:00Z",
  "stateChangedAt": "2023-11-11T12:00:00Z",
}
```
