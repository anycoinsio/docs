# Webhook Signature Check --- PHP

```php
<?php

function verifySignature($signature, $eventJson, $signatureKey) {
    return hash_hmac('sha256', $eventJson, $signatureKey) == $signature;
}

// Imagine this is the JSON payload received from the webhook
$eventJson = '{"id":"faf7a731-d9ed-4235-8dad-99c16aa9fd8a","event":"DEPOSIT_RECEIVED","happened_at":"2023-10-03 02:10:50 +0300","data":{}}';

// Your private signature key provided by AnyCoins
$signatureKey = 'your_private_signature_key_here';

// Assume the signature is obtained from the HTTP headers of the webhook request
$signature = '29e7a2ce38edebdb56f2320dfce06efbfcabd1c21c5e71f040877fd332993e5a';

// Verify the signature
$isValid = verifySignature($signature, $eventJson, $signatureKey);

echo "Signature valid? " . ($isValid ? "true" : "false") . "\n";
?>
```
