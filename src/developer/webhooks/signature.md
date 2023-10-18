# Webhook Signature

Securing webhook communications is essential to guarantee the integrity and authenticity of the messages received from AnyCoins. Our webhook signature mechanism employs HMAC (Hash-based Message Authentication Code) with SHA-256, utilizing a private signature key to generate a signature for each event.

This signature is dispatched along with the event in the `X-Any-Coins-Signature` HTTP header, empowering you to validate the event's source and contents.

## Signature Generation

AnyCoins generates the signature for each event using the following process:

1. **Raw POST Data Retrieval**

   Utilize the entire JSON object representing the event as received in the POST request body.

   **Example Event JSON**:

   ```json
   {
     "id": "faf7a731-d9ed-4235-8dad-99c16aa9fd8a",
     "event": "DEPOSIT_RECEIVED",
     "happened_at": "2023-10-03 02:10:50 +0300",
     "data": {
       "customer_id": "1",
       "amount": "603015.07537688",
       "currency": {
         "name": "Shiba Inu",
         "symbol": "SHIB",
         "blockchain": "ethereum",
         "is_token": true
       },
       "amount_eur": 4.2
     }
   }
   ```

2. **Hash Generation**

   - Apply the HMAC algorithm with SHA-256, using the private signature key provided by AnyCoins, to hash the raw JSON string.
   - The resulting hash is the signature for the event.

   **Example**:

   ```plaintext
   8b54e862dde10cafd3443c4108b6e11f86becf8b314972e0f83a3b6c760a3201
   ```

## Signature Verification

Upon receiving a webhook event, follow these steps to verify the signature:

1. **Receive Webhook Event**

   - Receive the webhook event along with the signature in the `X-Any-Coins-Signature` HTTP header.
   - Use the raw JSON string of the received event data.

2. **Hash Generation**

   - Generate the hash using the HMAC-SHA-256 algorithm and the signature key provided by AnyCoins.

3. **Comparison**
   - Compare the generated hash with the signature received in the HTTP headers.
   - If they match, the event is verified and can be safely processed.
   - If they do not match, discard the event as it may have been tampered with or originated from an untrusted source.

Utilizing the private signature key and the HMAC-SHA-256 algorithm for signature verification ensures the security and authenticity of the webhook events received from AnyCoins.

For any further assistance or inquiries regarding webhook signature verification or other security practices, feel free to reach out to our support team.

## Examples in Various Languages

For your convenience, we have provided examples of signature generation and verification in various languages:

- [C#](/developer/webhooks/signature/csharp.md)
- [Go](/developer/webhooks/signature/go.md)
- [JavaScript](/developer/webhooks/signature/javascript.md)
- [PHP](/developer/webhooks/signature/php.md)
- [Python](/developer/webhooks/signature/python.md)
- [Ruby](/developer/webhooks/signature/ruby.md)
- [Rust](/developer/webhooks/signature/rust.md)
