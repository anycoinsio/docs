# List Supported Assets

## Overview

This endpoint returns a list of all assets enabled by AnyCoins for your Merchant's account. You can check it once a minute or so to keep your local asset list up-to-date due to the fact that some assets may be temporarily disabled for maintenance or other reasons.

<div class="warning">
You should use the <code class="hljs">id</code> field returned by this endpoint to identify assets in other endpoints.

**We guarantee that the ID for coins will never change.**
</div>

If you haven't found the asset you were looking for or have any other questions, please contact us at [info@anycoins.io](mailto:info@anycoins.io).

## Request

```plaintext
GET https://anycoins.io/api/coins
```

The method takes no parameters.

## Response Schema

Each element within the coins array is an object representing a particular coin or token, adhering to the following schema:

- `id`: A string that represents a unique identifier for the asset. This is represented as a UUID (Universally Unique Identifier). Example: `1d535909-de36-4d81-98f4-9de3a3cf4b20`.
- `name`: A string describing the full name of the asset. Example: `Bitcoin`.
- `symbol`: A string representing the commonly used symbol of the asset. Example: `BTC`.
- `blockchain`: A string representing the blockchain the asset is issued on. Example: `Bitcoin`.
- `isEnabled`: A boolean value indicating whether the asset is currently enabled for transactions. Example: `true`.
- `swap`: An object containing information about the asset's availability for swap operations. It includes two fields:
  - `isInEnabled`: A boolean indicating if the asset can be swapped in (received) in a transaction. Example: `true`.
  - `isOutEnabled`: A boolean indicating if the asset can be swapped out (sent) in a transaction. Example: `true`.
- `tokenContractAddress`: (Optional) A string representing the contract address of the asset if it is a token on a blockchain like Ethereum or Tron. This is only applicable for tokens. Example: `TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t` for Tether (TRC20).

## Example Request

Replace the `Authorization` header value with your API key.

```bash
curl -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
    https://anycoins.io/api/coins
```

## Example Response

```json
{
    "coins": [
        {
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
        {
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
        {
            "id": "96592fb8-1466-41d9-b204-6eccf61e0745",
            "name": "TRON",
            "symbol": "TRX",
            "blockchain": "Tron",
            "isEnabled": true,
            "swap": {
                "isInEnabled": true,
                "isOutEnabled": true
            }
        }
    ]
}
```
