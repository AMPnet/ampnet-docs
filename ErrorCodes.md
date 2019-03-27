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

JSON Response example: 

```
{
  description: "ABCDEFG",
  err_code: '0501'
}
```

## Error code categories with prefixes

| Category       | Prefix |
|----------------|--------|
| Registration   | 01     |
| Authentication | 02     |
| Users          | 03     |
| Countries      | 04     |
| Wallet         | 05     |
| Organization   | 06     |

## Registration - Prefix: 01

| Error Description                               | Error Code |
|-------------------------------------------------|------------|
| Incomplete signup information                   | 01         |
| Signup information complete but invalid         | 02         |
| Signup failed because user exists               | 03         |
| Failed Email confirmation, invalid token format | 04         |
| Failed Email confirmation, non existing token   | 05         |
| Failed Email confirmation, token expired        | 06         |
| Social exception                                | 07         |

## Authentication - Prefix: 02

| Error Description       | Error Code |
|-------------------------|------------|
| Invalid login method    | 01         |

## Users - Prefix: 03

| Error Description                                             | Error Code |
|---------------------------------------------------------------|------------|
| Non existing user                                             | 01         |

## Countries - Prefix: 04

| Error Description            | Error Code |
|------------------------------|------------|
| No country with specified ID | 01         |

## Wallet - Prefix: 05

| Error Description                           | Error Code |
|---------------------------------------------|------------|
| User does not have a wallet                 | 01         |
| Active user cannot create additional wallet | 02         |
| User does not have enough funds on wallet   | 03         |
| Wallet with this hash already exists        | 04         |

## Organization - Prefix: 06

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Non existing organization                                                             | 01         |
| Cannot approve organization without privilege                                         | 02         |
| Failed invite user to organization without organization user role, privilege PW_USERS | 03         |
| User is already a member of this organization                                         | 04         |
| User is already invited                                                               | 05         |
| Organization with this name already exists                                            | 06         |


## Project - Prefix: 07

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Non existing project                                                                  | 01         |
| Invalid date                                                                          | 02         |
| Project has expired                                                                   | 03         |
| User has exceeded max funds per project                                               | 04         |
| Funding is below project minimum                                                      | 05         |
| Project has reached expected funding                                                  | 06         |
| Project is not active                                                                 | 07         |
| Min investment per user is higher than max investment per user                        | 08         |
| Expected funding is too high                                                          | 09         |
| Max funding per user is too high                                                      | 10         |


## Internal - Prefix: 08

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Could not upload document to IPFS                                                     | 01         |
| Failed gRPC call                                                                      | 02         |

## Transaction - Prefix: 09

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Non existing transaction                                                              | 01         |
| Missing companion id                                                                  | 02         |
