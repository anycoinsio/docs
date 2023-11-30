# API Authentication

Authentication is a critical component in interacting with the AnyCoins API, ensuring that only authorized users can fetch, manipulate, and interact with their respective account data.

Every API request must include an Authorization header with a valid Access Token to be processed successfully. Your Access Token is confidential and should be stored securely. Do not expose the key in client-side code or public repositories.

<div class="warning">
Sharing your Access Token can lead to unauthorized access to your account. Always keep your Access Tokens confidential.
</div>

If you need assistance with Access Token management or encounter any issues, please contact us at [info@anycoins.io](mailto:info@anycoins.io).

## Authentication Process

1. **Access Token Generation**:

   - [Obtain an Access Token](./obtaining-credentials.md) from your AnyCoins account.

2. **Making Authenticated Requests**:

   - Include the `Authorization` header in your HTTP requests with the value being `<Your-API-Key>`.

   ```bash
   curl 'https://api.anycoins.io/coins/ListCoins' \
       -H 'Authorization: Your-API-Key'
   ```

## Revoking Access Tokens

You can revoke an Access Token anytime from your AnyCoins account to cease its access to the API.

## Security Best Practices

- **Confidentiality**:

  - It's imperative to keep your Access Token secret to prevent unauthorized access to your API.
  - Never expose the Access Token in publicly accessible areas such as client-side code or public repositories.

- **Environment Variables**:

  - Store your Access Token in environment variables or in a secure configuration file that is ignored by version control systems.

- **Key Rotation**:
  - Regularly rotating Access Tokens minimizes the risk in case a key gets compromised.
