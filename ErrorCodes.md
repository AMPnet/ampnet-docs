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

## Authentication - Prefix: 02

| Error Description       | Error Code |
|-------------------------|------------|
| Invalid credentials     | 01         |
| Invalid login method    | 02         |
| Non existing user login | 03         |

## Users - Prefix: 03

| Error Description                                             | Error Code |
|---------------------------------------------------------------|------------|
| Failed fetch list of users (not admin)                        | 01         |
| Failed to fetch list of users because incomplete user profile | 02         |
| Failed to update others profile                               | 03         |

## Countries - Prefix: 04

| Error Description            | Error Code |
|------------------------------|------------|
| No country with specified ID | 01         |

## Wallet - Prefix: 05

| Error Description                           | Error Code |
|---------------------------------------------|------------|
| Active user cannot create additional wallet | 01         |

## Organization - Prefix: 06

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Cannot approve organization without privilege                                         | 01         |
| Failed invite user to organization without organization user role, privilege PW_USERS | 02         |