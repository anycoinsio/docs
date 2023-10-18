# Webhook Signature Check --- JavaScript

```js
const crypto = require("crypto");

/**
 * @param {string} signature
 * @param {string} eventJson
 * @param {string} signatureKey
 * @returns {boolean}
 */
function verifySignature(signature, eventJson, signatureKey) {
  return (
    crypto
      .createHmac("sha256", signatureKey)
      .update(eventJson)
      .digest("hex") === signature
  );
}

const eventJson =
  '{"id":"faf7a731-d9ed-4235-8dad-99c16aa9fd8a","event":"DEPOSIT_RECEIVED","happened_at":"2023-10-03 02:10:50 +0300","data":{}}';
const signatureKey = "your_private_signature_key_here";
const signature =
  "29e7a2ce38edebdb56f2320dfce06efbfcabd1c21c5e71f040877fd332993e5a";

const isValid = verifySignature(signature, eventJson, signatureKey);

console.log(`Signature valid? ${isValid}`);
```
