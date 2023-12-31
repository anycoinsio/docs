# Obtaining Credentials

To interact securely with the AnyCoins platform, two types of credentials are utilized: an Access Token and a Signature Key.

To obtain your credentials sign in into your account at [anycoins.io](https://anycoins.io).

## Access Token

The Access Token is essential for making authenticated requests to the AnyCoins API. Once logged in, you can generate an Access Token from your account dashboard, which should be included in the `Authorization` header when making API requests.

You can get started with the AnyCoins API by following the [API Authentication](./authentication.md) guide.

## Signature Key

The Signature Key is crucial for verifying the authenticity of callbacks from AnyCoins. It is used to generate and verify signatures for webhook events. Like the Access Token, you can obtain your Signature Key from the account dashboard.

You can learn more about webhook signatures in the [Webhook Signature](../webhooks/signature.md) guide.
