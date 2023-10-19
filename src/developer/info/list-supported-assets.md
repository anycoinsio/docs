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
GET https://pay.anycoins.io/api/coins
```

The method takes no parameters.

## Response Schema

Each element within the coins array is an object representing a particular coin or token, adhering to the following schema:

- `id`: A string that represents a unique identifier for the asset. This is represented as a UUID (Universally Unique Identifier). Example: "1d535909-de36-4d81-98f4-9de3a3cf4b20".
- `name`: A string describing the full name of the asset. Example: "Bitcoin".
- `symbol`: A string representing the commonly used symbol of the asset. Example: "BTC".
- `blockchain`: A string representing the blockchain the asset is issued on. Example: "bitcoin".
- `price_eur`: A string that denotes the current price of the asset in EUR. The value is serialized as a string to preserve decimal precision. Example: "26215.7033095696".
- `is_token`: A boolean value indicating whether the asset is a token (`true`) or a coin (`false`).

## Example Request

Replace the `Authorization` header value with your API key.

```bash
curl -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
  https://pay.anycoins.io/api/coins
```

## Example Response

```json
{
  "coins": [
    {
      "id": "b18d329f-066f-43ea-9c59-53328e473685",
      "name": "Tether (TRC20)",
      "symbol": "USDT",
      "blockchain": "tron",
      "price_eur": "0.9495665297",
      "is_token": true
    }
  ]
}
```
