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
| Coop           | 10     |
| Middleware     | 11     |

### Registration - Prefix: 01

| Error Description                               | Error Code |
|-------------------------------------------------|------------|
| Invalid signup data                             | 01         |
| ~~Signup information complete but invalid~~     | 02         |
| Email already used                              | 03         |
| Failed Email confirmation, invalid token format | 04         |
| Failed Email confirmation, token expired        | 05         |
| Social exception                                | 06         |
| ~~Identyum exception~~                          | 07         |
| ~~Identyum exception: failed to get token~~     | 08         |
| ~~User Info already exists~~                    | 09         |
| reCAPTCHA verification failed                   | 10         |

### Authentication - Prefix: 02

| Error Description               | Error Code |
|---------------------------------|------------|
| Invalid login method            | 01         |
| Missing forgot password token   | 02         |
| Forgot password token expired   | 03         |
| Invalid JWT                     | 04         |
| Missing JWT                     | 05         |
| Failed to register JWT          | 06         |
| Invalid username or password    | 07         |

### Users - Prefix: 03

| Error Description                                             | Error Code |
|---------------------------------------------------------------|------------|
| Missing user defined in JWT                                   | 01         |
| Invalid bank account data                                     | 02         |
| Invalid old password                                          | 03         |
| ~~Invalid user role~~                                         | 04         |
| UMissing privilege to access data                             | 05         |
| User missing                                                  | 06         |

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
| ~~Cannot approve organization without privilege~~                                     | 02         |
| ~~Failed invite user to organization without organization user role~~                 | 03         |
| User is already a member of this organization                                         | 04         |
| User is already invited                                                               | 05         |
| Organization with this name already exists                                            | 06         |
| Missing a privilege for this organization                                             | 07         |
| Organization membership missing                                                       | 08         |
| Invalid organization invitation                                                       | 09         |

### Project - Prefix: 07

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Non existing project                                                                  | 01         |
| Invalid date                                                                          | 02         |
| Project has expired                                                                   | 03         |
| User has exceeded max funds per project                                               | 04         |
| ~~Funding is below project minimum~~                                                  | 05         |
| Project has reached expected funding                                                  | 06         |
| Project is not active                                                                 | 07         |
| Min investment per user is higher than max investment per user                        | 08         |
| Expected funding is too high                                                          | 09         |
| Max funding per user is too high                                                      | 10         |
| Invalid project ROI                                                                   | 11         |
| Missing project owner privilege                                                       | 12         |

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
| Missing transaction data                                                              | 02         |

### Coop - Prefix: 10

| Error Description                                                                     | Error Code |
|---------------------------------------------------------------------------------------|------------|
| Missing coop                                                                          | 01         |
| Coop already exists                                                                   | 02         |

### Middleware - Prefix: 11

| Error Description                                                                                                  | Error Code |
|--------------------------------------------------------------------------------------------------------------------|------------|
| Transaction not signed. Aborting.                                                                                  | 01         |
| Transaction not mined.                                                                                             | 02         |
| Invalid contract called! Contract not part of Cooperative contracts collection.                                    | 03         |
| Transaction verification error.                                                                                    | 04         |
| Transaction not found.                                                                                             | 05         |
| Wallet not found!                                                                                                  | 10         |
| Wallet creation transaction failed!                                                                                | 11         |
| Wallet creation transaction still pending!                                                                         | 12         |
| Wallet already exists!                                                                                             | 13         |
| Error while creating Group. Invalid Coop contract provided as argument!                                            | 20         |
| Error while creating Project. Invalid Group contract provided as argument!                                         | 30         |
| Error while creating Sell Offer. Invalid Project contract provided as argument!                                    | 31         |
| Ae Sdk error was thrown.                                                                                           | 40         |
| Unknown error occured while dry running transaction. Contact system administrator!                                 | 50         |
| Claim ownership feature is disabled. Aborting.                                                                     | 600        |
| Trying to claim ownership more than once. Aborting.                                                                | 601        |
| Token not initalized!                                                                                              | 602        |
| Only Platform Manager can make this action!                                                                        | 603        |
| Sender wallet not activated. Activate your blockchain wallet before sending funds.                                 | 604        |
| Receiver wallet not activated. Transfer aborted.                                                                   | 605        |
| Wallet not activated. Activate your wallet before approving funds withdrawal.                                      | 606        |
| Amount of funds to be approved for withdrawal must be grater than 0.                                               | 607        |
| Amount of funds to transfer must be grater than 0.                                                                 | 608        |
| Insufficient funds on user's wallet to make the transfer.                                                          | 609        |
| Sender wallet not activated. Sender has to have activated blockchain wallet before approving funds for transfer.   | 610        |
| Receiver wallet not activated. Receiver has to have activated blockchain wallet before receiving any funds.        | 611        |
| Only registered platform users with active wallets can get their deposits approved. Aborting.                      | 612        |
| Only registered platform users with active wallets can withdraw funds. Aborting.                                   | 613        |
| Value to be withdrawn is bigger than allowed.                                                                      | 614        |
| Value to be withdrawn is not present.                                                                              | 615        |
| Only Token Issuer can make this action!                                                                            | 616        |
| Only registered platform user with activated wallet can make this action!                                          | 617        |
| Can not create organization. Creator must be registered platform user with activated wallet.                       | 618        |
| Member to be added to organization has to be registered platform user with active wallet.                          | 619        |
| Trying to accept organization invite which does not exist!                                                         | 620        |
| Trying to accept organization invite but it was already accepted!                                                  | 621        |
| Only organization owner can make this action!                                                                      | 622        |
| Only registered platform member with active wallet can make this action.                                           | 623        |
| In order to make this action organization must have active wallet!                                                 | 624        |
| Must be organization owner to be able to create project for funding.                                               | 625        |
| Organization must have an active wallet before it can create new project for funding.                              | 626        |
| Only organization owner can allow or disallow unconditional investment cancellation!                               | 627        |
| Only platform manager can manually add new investments!                                                            | 628        |
| Can not add new investments. Project already completely funded.                                                    | 629        |
| Can not add new investments. Project expired before it was completely funded.                                      | 630        |
| Can not cancel investment!                                                                                         | 631        |
| Project investment cap not reached! Can not withdraw funds.                                                        | 632        |
| Only organization owner can request withdrawal of project funds.                                                   | 633        |
| Can not withdraw funds while revenue share payout is in process.                                                   | 634        |
| Revenue share payout has to be started before actual payout process is executed.                                   | 635        |
| Can not invest, project already completely funded.                                                                 | 636        |
| Can not invest zero tokens!                                                                                        | 637        |
| Can not invest. Insufficient funds.                                                                                | 638        |
| User's investment will surpass maximum per user investment for this project. Aborting.                             | 639        |
| User's investment does not meet required minimum per user investment for this project. Aborting.                   | 640        |
| User's investment will make total funds raised greater than project's investment cap. Aborting.                    | 641        |
| User's investment will leave tiny fraction of project non-funded. Enlarge your investment. Aborting.               | 642        |
| Project funding has ended.                                                                                         | 643        |
| Only organization owner can initiate revenue shares payout.                                                        | 644        |
| Can not start revenue share payout on project which is still in funding phase.                                     | 645        |
| Revenue is zero. Aborting.                                                                                         | 646        |
| Can not start revenue share payout. Project balance too low. Mint revenue to project wallet and try again.         | 647        |
| Can not start revenue share payout. It is already started!                                                         | 648        |
| Wallet not activated. Wallet has to be activated before making this action.                                        | 649        |
| Amount of shares to be approved for transfer must be grater than 0.                                                | 650        |
| Shares balance too low!                                                                                            | 651        |
| Can not transfer shares. Project is still in funding phase.                                                        | 652        |
| Can not transfer shares. Project is in revenue share payout state.                                                 | 653        |
| Can not transfer shares. Insufficient amount of shares to transfer.                                                | 654        |
| Can not transfer shares. Need approval.                                                                            | 655        |
| Can not transfer shares. Sender not active Cooperative member.                                                     | 656        |
| Can not transfer shares. Receiver not active Cooperative member.                                                   | 657        |
| Can not place sell offer. Associated project not funded completely.                                                | 658        |
| Can not place sell offer. Not enough shares to sell.                                                               | 659        |
| Sell offer already settled.                                                                                        | 660        |
| Insufficient funds.                                                                                                | 661        |
| Only seller can accept counter offer.                                                                              | 662        |
| Tried to accept non-existing counter offer.                                                                        | 663        |
| Only seller can cancel offer.                                                                                      | 664        |
| Cooperative does not exist!                                                                                        | 70         |
| Error while deploying Contract. Malformed code. Can only deploy official AMPnet Contracts.                         | 90         |
| Unknown error occured.                                                                                             | 99         |
