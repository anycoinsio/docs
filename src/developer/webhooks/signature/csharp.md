# Webhook Signature Check --- C#

```csharp
using System;
using System.Security.Cryptography;
using System.Text;

class Program
{
    static bool VerifySignature(string signature, string eventJson, string signatureKey)
    {
        using (var hmacsha256 = new HMACSHA256(Encoding.UTF8.GetBytes(signatureKey)))
        {
            byte[] hashmessage = hmacsha256.ComputeHash(Encoding.UTF8.GetBytes(eventJson));
            return BitConverter.ToString(hashmessage).Replace("-", "").ToLower() == signature;
        }
    }

    static void Main(string[] args)
    {
        // Imagine this is the JSON payload received from the webhook
        string eventJson = @"{""id"":""faf7a731-d9ed-4235-8dad-99c16aa9fd8a"",""event"":""DEPOSIT_RECEIVED"",""happened_at"":""2023-10-03 02:10:50 +0300"",""data"":{}}";

        // Your private signature key provided by AnyCoins
        string signatureKey = "your_private_signature_key_here";

        // Assume the signature is obtained from the HTTP headers of the webhook request
        string signature = "29e7a2ce38edebdb56f2320dfce06efbfcabd1c21c5e71f040877fd332993e5a";

        // Verify the signature
        bool isValid = VerifySignature(signature, eventJson, signatureKey);

        Console.WriteLine($"Signature valid? {isValid}");
    }
}
```
