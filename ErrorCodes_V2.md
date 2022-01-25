# AMPnet API Error Response Docs

# Introduction

AMPnet backend returns error response when errors happen (duh). 
Error response contains:
* `err_code` - structured in a way that should be easy to read and identify on-the-fly, 
* `description` - defined in the tables below,
* `message` - generated depending on the problem and provides more information.

Each error code consists of two parts:
1. Two digits for error category,
2. Two digits for specific error withing the category.

## Example

Specific Error: `Registration incomplete`

Error category code: `01`

Error specific code: `01`

Full error code: `0101`

Description: `Invalid signup data`

Message: `Missing UserInfo with session id: 44927492-8799-406e-8076-933bc9164ebc`

JSON Response example: 

```
{
  err_code: "0101",
  description: "Invalid signup data",
  message: "Missing UserInfo with session id: 44927492-8799-406e-8076-933bc9164ebc"
}
```

## Error code categories with prefixes

| Category       | Prefix |
|----------------|--------|
| Registration   | 01     |
| Authentication | 02     |
| User           | 03     |
| Blockchain     | 04     |
| IPFS           | 05     |
| Payout         | 06     |

### Registration - Prefix: 01

| Error Description                               | Error Code |
|-------------------------------------------------|------------|
| Invalid signup data                             | 01         |
| Failed email confrimation, token expired        | 05         |
| Missing Veriff session                          | 11         |

### Authentication - Prefix: 02

| Error Description               | Error Code |
|---------------------------------|------------|
| Invalid JWT                     | 04         |
| Missing JWT                     | 05         |
| Failed to register JWT          | 06         |
| Invalid refresh token           | 08         |
| Payload missing                 | 09         |
| Signed payload invalid          | 10         |

### Users - Prefix: 03

| Error Description                                             | Error Code |
|---------------------------------------------------------------|------------|
| Missing user defined in JWT                                   | 01         |
| Failed to get Pinata JWT for user                             | 02         |
| User is not asset owner                                       | 03         |

### Blockchain - Prefix: 04
| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Blockchain id not supported                                                           | 01         |
| Blockchain data is not provided                                                       | 02         |
| Blockchain contract version is not supported                                          | 03         |
| Blockchain contract read error                                                        | 04         |
| Blockchain contract event read error                                                  | 05         |

### IPFS - Prefix: 05
| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| IPFS upload failed                                                                    | 01         |

### Payout - Prefix: 06
| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Merkle tree not found for specified payout parameters                                 | 01         |
| Payout does not exist for specified account                                           | 02         |

# Web3Provider

Web3Provider service is a proxy caching service to the blockchain. Providers take JSON-RPC requests and return a response.
Specification for error codes can be found on https://eth.wiki/json-rpc/json-rpc-error-codes-improvement-proposal.
