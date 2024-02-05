# Deposit Canceled

The `Deposit Canceled` webhook is triggered whenever a pending deposit was canceled by merchant (e.g. manually "expiring" a pending deposit).

<div class="warning">
Do not forget to <a href="../signature.html">check the signature</a> before processing a webhook!
</div>

## Webhook Payload

- `id`: A unique identifier for the deposit
- `inCoin`: An object containing details about the input coin.
- `outCoin`: An object containing details about the output coin.
- `inAddress`: The address to send the input coins to.
- `state`: The current state of the deposit.
- `merchantCustomerId`: ID of the customer on merchant's side.
- `merchantDepositId`: ID of the deposit on merchant's side.
- `createdAt`: Timestamp of when the deposit was created.
- `stateChangedAt`: Timestamp of when the deposit state was last time changed.

---

## Example Webhook

### Headers

| Header                | Value                                                              |
|-----------------------|--------------------------------------------------------------------|
| Content-Type          | `application/json`                                                 |
| User-Agent            | `AnyCoins Webhook`                                                 |
| X-Any-Coins-Signature | `d1825cd741c7363d00a984774a62813d4d341aadb34325732cfa2e3e8c03e55e` |

### Body

#### Pretty

```json
{
  "id": "faf7a731-d9ed-4235-8dad-99c16aa9fd8a",
  "event": "DepositCanceled",
  "happenedAt": "2023-10-04T03:46:18+03:00",
  "data": {
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
    "state": "Canceled",
    "merchantCustomerId": "420",
    "merchantDepositId": "23069",
    "createdAt": "2024-02-05T20:09:25.385987Z",
    "stateChangedAt": "2024-02-05T20:12:23.129481Z"
  }
}
```
