# Rate Limiting

To maintain the reliability of the AnyCoins API, we've set default rate limits:

- `POST`: 2 requests/second
- `GET`: 10 requests/second

<div class="warning">
Limits apply <strong>per API key</strong>.
</div>

Exceeding them will trigger a response with `429 Too Many Requests` status code.

If you need assistance with rate limiting or encounter any issues, please contact us at [info@anycoins.io](mailto:info@anycoins.io).
