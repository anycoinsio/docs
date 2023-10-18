# Webhook Signature Check --- Ruby

```ruby
require 'openssl'
require 'json'

def verify_signature(signature, event_json, signature_key)
  OpenSSL::HMAC.hexdigest('SHA256', signature_key, event_json) == signature
end

# Imagine this is the JSON payload received from the webhook
event_json = '{"id":"faf7a731-d9ed-4235-8dad-99c16aa9fd8a","event":"DEPOSIT_RECEIVED","happened_at":"2023-10-03 02:10:50 +0300","data":{}}'

# Your private signature key provided by AnyCoins
signature_key = 'your_private_signature_key_here'

# Assume the signature is obtained from the HTTP headers of the webhook request
signature = '29e7a2ce38edebdb56f2320dfce06efbfcabd1c21c5e71f040877fd332993e5a'

# Verify the signature
is_valid = verify_signature(signature, event_json, signature_key)

puts "Signature valid? #{is_valid}"
```
