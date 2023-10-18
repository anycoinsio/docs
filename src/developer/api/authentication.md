# API Authentication

Authentication is a critical component in interacting with the AnyCoins API, ensuring that only authorized users can fetch, manipulate, and interact with their respective account data.

Every API request must include an Authorization header with a valid API key to be processed successfully. Your API key is confidential and should be stored securely. Do not expose the key in client-side code or public repositories.

<div class="warning">
Sharing your API key can lead to unauthorized access to your account. Always keep your API keys confidential.
</div>

If you need assistance with API key management or encounter any issues, please contact us at [info@anycoins.io](mailto:info@anycoins.io).

## Authentication Process

1. **API Key Generation**:

   - [Obtain an API key](./obtaining-credentials.md) from your AnyCoins account.

2. **Making Authenticated Requests**:

   - Include the `Authorization` header in your HTTP requests with the value being `<Your-API-Key>`.

   ```bash
   curl 'https://pay.anycoins.io/api/coins' \
       -H 'Authorization: Your-API-Key'
   ```

## Revoking API Keys

You can revoke an API key anytime from your AnyCoins account to cease its access to the API.

## Security Best Practices

- **Confidentiality**:

  - It's imperative to keep your API key secret to prevent unauthorized access to your API.
  - Never expose the API key in publicly accessible areas such as client-side code or public repositories.

- **Environment Variables**:

  - Store your API key in environment variables or in a secure configuration file that is ignored by version control systems.

- **Key Rotation**:
  - Regularly rotating API keys minimizes the risk in case a key gets compromised.
