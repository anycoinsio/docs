# Webhooks

Webhooks are an integral part of the AnyCoins platform, designed to provide real-time notifications regarding important events associated with your merchant account. Currently, we support two types of webhook events: `Deposit Completed` and `Withdrawal Completed`. These webhooks help in automating the flow of information and ensure you are promptly informed about crucial transactional activities. Here's an overview of the supported webhook events:

## Deposit Completed

The `Deposit Completed` webhook is triggered whenever a deposit to your AnyCoins account is confirmed by the network. This webhook provides immediate notification, allowing you to track incoming funds efficiently.

### Webhook Payload

- **Deposit ID**: The unique identifier for the deposit in our system.
- **Amount**: The amount deposited.
- **Coin**: The cryptocurrency in which the deposit was made.
- **Timestamp**: The time at which the deposit was confirmed by the network.

### Usage

- Automatically update your system to reflect the received deposit.
- Notify your customer service team or the customer directly regarding the successful deposit.
- Keep accurate real-time records of all deposits.

## Withdrawal Completed

The `Withdrawal Completed` webhook is sent once a withdrawal request from your AnyCoins account has been processed and the funds have been transferred to the specified wallet address.

### Webhook Payload

- **Wthdrawal ID**: The unique identifier for the withdrawal.
- **Amount**: The amount withdrawn.
- **Currency**: The cryptocurrency in which the withdrawal was made.
- **Destination Wallet Address**: The wallet address to which the funds were sent.
- **Timestamp**: The time at which the withdrawal was completed.

### Usage

- Automatically update your financial records to reflect the completed withdrawal.
- Notify concerned parties or systems regarding the successful withdrawal.
- Maintain accurate real-time tracking of all withdrawals.

Webhooks are designed to provide a seamless, automated flow of information, reducing manual effort and ensuring you have timely data to make informed decisions. They play a crucial role in enhancing operational efficiency and ensuring a smooth transactional experience on the AnyCoins platform.

Should you require any further information or assistance regarding webhook configurations or any other aspect of the AnyCoins platform, our support team is readily available to assist.
