# AMPnet API Error Response Docs

# Introduction

AMPnet backend returns error response when errors happen (duh). 
Error response contains:
* `err_code` - structured in a way that should be easy to read and identify on-the-fly. 
* `description` - defined in the tables below
* `message` - generated depending on the problem and provides more information.

Each error code consists of two parts:
1. Two digits for error category
2. Two digits for specific error withing the category

## Example

Specific Error: `Missing wallet`

Error category code: `05`

Error specific code: `01`

Full error code: `0501`

Description: `Missing wallet`

Message: `Wallet missing for owner: 89fb3b1c-9c0a-11e9-a2a3-2a2ae2dbcce4`

JSON Response example: 

```
{
  err_code: "0501",
  description: "Missing wallet",
  message: "Wallet missing for owner: 89fb3b1c-9c0a-11e9-a2a3-2a2ae2dbcce4"
}
```

## Error code categories with prefixes

| Category       | Prefix |
|----------------|--------|
| Registration   | 01     |
| Authentication | 02     |
| User           | 03     |
| ~~Countries~~  | 04     |
| Wallet         | 05     |
| Organization   | 06     |
| Project        | 07     |
| Internal       | 08     |
| Transaction    | 09     |

### Registration - Prefix: 01

| Error Description                               | Error Code |
|-------------------------------------------------|------------|
| Incomplete signup information                   | 01         |
| Signup information complete but invalid         | 02         |
| Signup failed because user exists               | 03         |
| Failed Email confirmation, invalid token format | 04         |
| Failed Email confirmation, token expired        | 05         |
| Social exception                                | 06         |
| Identyum exception                              | 07         |
| Identyum exception: failed to get token         | 08         |
| User Info already exists                        | 09         |

### Authentication - Prefix: 02

| Error Description               | Error Code |
|---------------------------------|------------|
| Invalid login method            | 01         |
| Missing forgot password token   | 02         |
| Forgot password token expired   | 03         |

### Users - Prefix: 03

| Error Description                                             | Error Code |
|---------------------------------------------------------------|------------|
| Non existing user                                             | 01         |
| Invalid bank account data                                     | 02         |
| Different password                                            | 03         |
| Invalid user role                                             | 04         |
| User does not have a privilege                                | 05         |

### Countries - Prefix: 04 - Removed

### Wallet - Prefix: 05

| Error Description                           | Error Code |
|---------------------------------------------|------------|
| Missing wallet                              | 01         |
| Active user cannot create additional wallet | 02         |
| User does not have enough funds on wallet   | 03         |
| Wallet with this hash already exists        | 04         |
| Missing deposit                             | 05         |
| Deposit is already minted                   | 06         |
| Deposit is not approved                     | 07         |
| Unapproved deposit exists                   | 08         |
| Missing withdraw                            | 09         |
| Unapproved withdraw exists                  | 10         |
| Withdraw already approved                   | 11         |
| Withdraw not approved                       | 12         |
| Withdraw already burned                     | 13         |
| Wallet is not activated by the administrator| 14         |
| Missing revenue payout                      | 15         |

### Organization - Prefix: 06

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Non existing organization                                                             | 01         |
| Cannot approve organization without privilege                                         | 02         |
| Failed invite user to organization without organization user role, privilege PW_USERS | 03         |
| User is already a member of this organization                                         | 04         |
| User is already invited                                                               | 05         |
| Organization with this name already exists                                            | 06         |
| ~~Missing a privilege for this organization~~                                         | ~~07~~     |
| Organization membership missing                                                       | 08         |
| Invalid organization invitation                                                       | 07         |

### Project - Prefix: 07

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
| Invalid project ROI                                                                   | 11         |

### Internal - Prefix: 08

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Could not upload document on cloud file storage                                       | 01         |
| Invalid value in request                                                              | 02         |
| Failed gRPC call to blockchain service                                                | 03         |
| Failed gRPC call to user service                                                      | 04         |
| Failed gRPC call to project service                                                   | 05         |
| Failed gRPC call to mail service                                                      | 06         |
| Database exception                                                                    | 07         |
| Invalid request data                                                                  | 08         |
| Failed gRPC call to wallet service                                                    | 09         |
| Could not generate pdf from data                                                      | 10         |

### Transaction - Prefix: 09

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Non existing transaction                                                              | 01         |
| Missing companion data                                                                | 02         |
