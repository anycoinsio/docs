# Create Swap

## Overview

The `POST /swaps/CreateSwap` endpoint facilitates the creation of asset swap transactions between different cryptocurrencies. This feature is vital for users who need to exchange one type of coin or token for another seamlessly.

## Request

```plaintext
POST https://api.anycoins.io/swaps/CreateSwap
```

This method requires the following JSON parameters in the request body:

```json
{
    "inCoinId": "1d535909-de36-4d81-98f4-9de3a3cf4b20",
    "outCoinId": "b18d329f-066f-43ea-9c59-53328e473685",
    "outAddress": "TC1LrufbG1spBUE1v6fKem4PAaCGm7ah7S"
}
```

- `inCoinId`: The ID of the coin being swapped from. This must be an asset with enabled swapping-in functionality. **Required.**
- `outCoinId`: The ID of the coin being swapped to. This must be an asset with enabled swapping-out functionality. **Required.**
- `outAddress`: The destination address for the output coin. **Required.**

## Response Schema

The response includes details about the swap transaction:

- `id`: A unique identifier for the swap transaction.
- `inCoin`: An object containing details about the input coin.
- `outCoin`: An object containing details about the output coin.
- `inAddress`: The address to send the input coin to.
- `outAddress`: The address where the output coin will be received.
- `state`: The current state of the swap transaction.
- `inAmount`: The amount of input coins that will be swapped (`0` in a case of a swap creation)
- `outAmount`: The amount of output coins that will be received (`0` in a case of a swap creation)
- `createdAt`: Timestamp of when the swap was created.
- `stateChangedAt`: Timestamp of when the swap state was last time changed.

## Example Request

Replace the `Authorization` header value with your API key.

```bash
curl -X POST \
    -H 'Authorization: 7e319c2a-28f7-48a1-988f-7dea7cc4c3fa' \
    -d '{"inCoinId": "1d535909-de36-4d81-98f4-9de3a3cf4b20", "outCoinId": "b18d329f-066f-43ea-9c59-53328e473685", "outAddress": "TC1LrufbG1spBUE1v6fKem4PAaCGm7ah7S"}'
    https://api.anycoins.io/swaps/CreateSwap
```

## Example Response

```json
{
    "id": "e3f7921d-5d64-4d6f-a462-f1a4d2f1b4f0",
    "inCoin": {
        "id": "1d535909-de36-4d81-98f4-9de3a3cf4b20",
        "name": "Bitcoin",
        "symbol": "BTC",
        "blockchain": "Bitcoin"
    },
    "outCoin": {
        "id": "b18d329f-066f-43ea-9c59-53328e473685",
        "name": "Tether (TRC20)",
        "symbol": "USDT",
        "blockchain": "Tron"
    },
    "inAddress": "1BoatSLRHtKNngkdXEeobR76b53LETtpyT",
    "outAddress": "TC1LrufbG1spBUE1v6fKem4PAaCGm7ah7S",
    "state": "Pending",
    "inAmount": "0.0",
    "outAmount": "0.0",
    "createdAt": "2023-04-05T12:34:56.789Z",
    "stateChangedAt": "2023-04-05T12:34:56.789Z"
}
```

## Notes

- Ensure that both `inCoinId` and `outCoinId` are valid and have swap functionalities enabled.
- The `outAddress` must be compatible with the `outCoinId` specified.

## Next Steps

- Transfer the desired amount of coins to the `inAddress`. The swap will automatically start after your transaction is confirmed.
- You will receive a [`Swap Completed`](../webhooks/events/swap-completed.md) webhook once the swap is processed.

## Best Practices

- Before executing a swap, verify the compatibility and requirements of both input and output coins.
- Implement error handling for cases where the swap might fail due to issues like network congestion or invalid addresses.
