# AMPnet API Error Code Docs

# Introduction

AMPnet backend returns error codes when errors happen (duh). The codes are structured in a way that should be easy to read and identify on-the-fly.

Each error code consists of two parts
1. Two digits for error category
2. Two digits for specific error withing the category

## Example

Error description: `Active user cannot create an additional wallet`

Full Error: `com.ampnet.crowdfundingbackend.exception.ResourceAlreadyExistsException`

Error category: `ampnet.SignupError`

Specific Error: `InvalidRequestException`

Error category code: `05`

Error specific code: `01`

Full error code: `0501`

## Error code categories and prefixes

| Category       | Prefix |
|----------------|--------|
| Registration   | 01     |
| Authentication | 02     |
| Users          | 03     |
| Countries      | 04     |
| Wallet         | 05     |
| Organization   | 06     |

