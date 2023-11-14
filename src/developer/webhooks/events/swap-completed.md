# Swap Completed

The `Swap Completed` webhook is sent once a swap request has been processed and the funds have been transferred to the specified output address.

<div class="warning">
Do not forget to <a href="../signature.html">check the webhook signature</a> before processing!
</div>

## Webhook Payload

The payload of the `Swap Completed` webhook contains detailed information about the completed swap. The following fields are included:

- `id`: The unique identifier for the swap in our system.
- `state`: The current state of the swap, which will be `Completed` for this event.
- `inCoin`: Details of the input coin, including its ID, name, symbol, and blockchain information.
- `outCoin`: Details of the output coin, similar to InCoin.
- `inAddress`: The input address where the coins were sent from.
- `outAddress`: The output address where the coins were sent to.
- `amountIn`: The amount of input coins that were swapped.
- `amountOut`: The amount of output coins that were received.
- `createdAt`: Timestamp of when the swap was created.
- `stateChangedAt`: Timestamp of when the swap state changed to `Completed`.

## Usage

The `Swap Completed` webhook can be used for:

- Automatically updating the status of a swap in your system to reflect its completion.
- Triggering notifications or emails to inform users that their swap has been completed.
- Initiating post-swap processes, such as accounting entries or further transactions.
- Logging or auditing swap activities for compliance and monitoring purposes.

---

## Example Webhook

### Headers

| Header                | Value                                                              |
|-----------------------|--------------------------------------------------------------------|
| Content-Type          | `application/json`                                                 |
| User-Agent            | `AnyCoins Webhook`                                                 |
| X-Any-Coins-Signature | `d1825cd741c7363d00a984774a62813d4d341aadb34325732cfa2e3e8c03e55e` |

### Body

#### Raw

```
{"id":"d17f5192-f56f-4cf8-8e89-f1dca83c3f69","event":"SwapCompleted","happenedAt":"2023-11-13T21:34:31.183171Z","data":{"id":"7a382ff7-d7d1-457b-b3bc-b5102f2d4dfb","inCoin":{"id":"611ba4b6-09e4-4ead-bc0e-6c6b970810f7","name":"Bitcoin","symbol":"BTC","blockchain":"Bitcoin","isEnabled":true,"swap":{"isInEnabled":true,"isOutEnabled":true}},"outCoin":{"id":"130f1fe6-09ad-4118-89f7-ab8e5612b13d","name":"Tether (TRC20)","symbol":"USDT","blockchain":"Tron","isEnabled":true,"tokenContractAddress":"TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t","swap":{"isInEnabled":true,"isOutEnabled":true}},"inAddress":"1PdzMQepZGS6TQmfB6vWMxhmE8kWtv833m","outAddress":"TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t","state":"Completed","amountIn":"0.0042","amountOut":"0.069","createdAt":"2023-11-11T01:17:17.841176Z","stateChangedAt":"2023-11-13T21:34:31.183171Z"}}
```

#### Pretty

```json
{
  "id": "d17f5192-f56f-4cf8-8e89-f1dca83c3f69",
  "event": "SwapCompleted",
  "happenedAt": "2023-11-13T21:34:31.183171Z",
  "data": {
    "id": "7a382ff7-d7d1-457b-b3bc-b5102f2d4dfb",
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
    "inAddress": "1PdzMQepZGS6TQmfB6vWMxhmE8kWtv833m",
    "outAddress": "TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t",
    "state": "Completed",
    "amountIn": "0.0042",
    "amountOut": "0.069",
    "createdAt": "2023-11-11T01:17:17.841176Z",
    "stateChangedAt": "2023-11-13T21:34:31.183171Z"
  }
}
```
