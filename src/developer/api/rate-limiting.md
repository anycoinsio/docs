# Rate Limiting

To maintain the reliability of the AnyCoins API, we've set default rate limits:

- 5 requests/second

<div class="warning">
Limits apply <strong>per API key</strong>.
</div>

Exceeding them will trigger a response with `429 Too Many Requests` status code.

If you need assistance with rate limiting or encounter any issues, please contact us at [hello@anycoins.io](mailto:hello@anycoins.io).
