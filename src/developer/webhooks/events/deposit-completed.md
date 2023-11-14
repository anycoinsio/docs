# Deposit Completed

The `Deposit Completed` webhook is triggered whenever a deposit to your AnyCoins account is confirmed by the network. This webhook provides immediate notification, allowing you to track incoming funds efficiently.

<div class="warning">
Do not forget to <a href="../signature.html">check the webhook signature</a> before processing!
</div>

## Webhook Payload

- `depositId`: The unique identifier for the deposit in our system.
- `customerId`: The unique identifier of customer in merchant's system.
- `amount`: The amount deposited.
- `coin`: The cryptocurrency in which the deposit was made.

## Usage

- Automatically update your system to reflect the received deposit.
- Notify your customer service team or the customer directly regarding the successful deposit.
- Keep accurate real-time records of all deposits.

---

## Example Webhook

### Body

#### Pretty

```json
{
  "id": "faf7a731-d9ed-4235-8dad-99c16aa9fd8a",
  "event": "DepositCompleted",
  "happenedAt": "2023-10-04T03:46:18+03:00",
  "data": {
    "depositId": "faf7a731-d9ed-4235-8dad-99c16aa9fd8a",
    "customerId": "420",
    "amount": "603015.07537688",
    "coin": {
      "id": "611ba4b6-09e4-4ead-bc0e-6c6b970810f7",
      "name": "Bitcoin",
      "symbol": "BTC",
      "blockchain": "Bitcoin",
      "isEnabled": true,
      "swap": {
        "isInEnabled": true,
        "isOutEnabled": true
      }
    }
  }
}
```
