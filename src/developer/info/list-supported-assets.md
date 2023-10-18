# List Supported Assets

## Overview

This endpoint returns a list of all assets enabled by AnyCoins for your Merchant's account. You can check it once a minute or so to keep your local asset list up-to-date due to the fact that some assets may be temporarily disabled for maintenance or other reasons.

<div class="warning">
You should use the <code class="hljs">id</code> field returned by this endpoint to identify assets in other endpoints.
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
      "id": "898a4753-2e6e-4d3e-a343-6b6f4de24956",
      "name": "AXS (TRC20)",
      "symbol": "AXS",
      "blockchain": "tron",
      "price_eur": "4.3144751315",
      "is_token": true
    },
    {
      "id": "2f39ce77-1ff2-47e5-ba8c-cd4ad5ba1405",
      "name": "AXS (ERC20)",
      "symbol": "AXS",
      "blockchain": "ethereum",
      "price_eur": "4.3144751315",
      "is_token": true
    },
    {
      "id": "559c4011-bb41-4cd6-ab74-c334e2a28c33",
      "name": "Bitcoin Cash",
      "symbol": "BCH",
      "blockchain": "bitcoin_cash",
      "price_eur": "218.6609692767",
      "is_token": false
    },
    {
      "id": "19e20e44-5699-4d9c-9c6c-b5a211de315c",
      "name": "Binance Coin",
      "symbol": "BNB",
      "blockchain": "binance_smart_chain",
      "price_eur": "203.9080910311",
      "is_token": false
    },
    {
      "id": "38128cf1-0e9c-48c0-8cbd-9f1851190315",
      "name": "Bitcoin",
      "symbol": "BTC",
      "blockchain": "bitcoin",
      "price_eur": "26221.0387136543",
      "is_token": false
    },

    // ...
    // Truncated for brevity
    // ...

    {
      "id": "1d535909-de36-4d81-98f4-9de3a3cf4b20",
      "name": "Zcash",
      "symbol": "ZEC",
      "blockchain": "zcash",
      "price_eur": "25.6526674182",
      "is_token": false
    }
  ]
}
```
