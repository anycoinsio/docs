# Flexible Amount Deposit

## Overview

## Request

```plaintext
POST https://anycoins.io/api/deposits/free_amount
```

The method takes the following parameters in a JSON body:

```json
{
    "coin_id": "b18d329f-066f-43ea-9c59-53328e473685",
    "customer_id": "420",
    "permanent_address": false
}
```

- `coin_id`: ID of coin (token) from the [[List Supported Assets]] method
