# Transaction Signing Formal Specification

The process of performing a state-changing blockchain transaction on AMPnet is the following. 

1. User makes an action on the fronted (e.g. "Invest $1000 into a project with ID 120")
2. The frontend sends the request for the action to the backend.
3. The backend generates the parameters for the transaction
4. The backend returns the parameters to the frontend
5. Frontend converts the parameters into a QR code and displays them to the user
6. User scans the QR code with the AMPnet Signer mobile app
7. The app presents the transaction details to the user
8. The app signs the transaction and opens a predefined link
9. The backend posts the transaction to the blockchain
10. The frontend polls a predefined route to see the transaction status
11. After the transaction has been mined - the frontend displays the action as completed.

The outcomes of this document are to define the format of the QR Code and the routes called by the Signer app and the fronted
polling functionallity

## QR Code Specification

QR code will be a text encoded .json format

This is an example of the transaction
```
{
  "tx" : {
   "amount":0,
   "callData":"cb_AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACBoPV8aKjz7jyvC9VB7SMH8SDmH6BPI7MqYTKloBqmOkwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAC5RbVVYaDJmRFJKdTVQUDh3V3Z0VTU1VlBDZXJ1ekZKcGJCcVdQRkJQQUtLRVhoAAAAAAAAAAAAAAAAAAAAAAAAM4IA0Q==",
   "callerId":"ak_2BnpcMtnLMX1s2gUAKCdCQ2SMtsUPB2wt6bxVJuHxXiRPHHasz",
   "contractId":"ct_2ccJZsoN5D4iWuueX7k4HSTt3QxBGATqzRo1GfeGj2A5GHCTHr",
   "fee":2036620,
   "gas":1579000,
   "gasPrice":1,
   "nonce":2,
   "type":"ContractCallTx",
   "version":1,
   "vmVersion":"0x01"  
  },
  "tx_id" : number,
  "info" : {
    "tx_type" : "CreateOrgTx | CreateProjectTx | InvestAllowanceTx | InvestTx",
    "title" : "string",
    "desctiption" : "string"
  },
  "info_sig" : "string"
}
```

## Deploy Route Specification

After a transaction has been signed, a call will be made to a predetermined route on the backend. 

"example.io/tx_broadcast?tx_id=number&tx_sig=string"







