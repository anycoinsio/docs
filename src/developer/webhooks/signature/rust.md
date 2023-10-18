# Webhook Signature Check --- Rust

```rust
extern crate crypto;
extern crate hex;

use crypto::mac::Mac;
use crypto::hmac::Hmac;
use crypto::sha2::Sha256;

fn verify_signature(signature: &str, event_json: &str, signature_key: &str) -> bool {
    let mut hmac = Hmac::new(Sha256::new(), signature_key.as_bytes());
    hmac.input(event_json.as_bytes());
    let result = hmac.result();
    let computed_signature = hex::encode(result.code());
    computed_signature == signature
}

fn main() {
    // Imagine this is the JSON payload received from the webhook
    let event_json = r#"{"id":"faf7a731-d9ed-4235-8dad-99c16aa9fd8a","event":"DEPOSIT_RECEIVED","happened_at":"2023-10-03 02:10:50 +0300","data":{}}"#;

    // Your private signature key provided by AnyCoins
    let signature_key = "your_private_signature_key_here";

    // Assume the signature is obtained from the HTTP headers of the webhook request
    let signature = "29e7a2ce38edebdb56f2320dfce06efbfcabd1c21c5e71f040877fd332993e5a";

    // Verify the signature
    let is_valid = verify_signature(signature, event_json, signature_key);

    println!("Signature valid? {}", is_valid);
}
```
