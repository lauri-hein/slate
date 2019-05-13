# Activities Integration Guide

## API access

### TEST and LIVE environments

* Sandbox API is located at https://api.sandbox.transferwise.tech
* LIVE API is located at https://api.transferwise.com

## Get the current state of activity tracker

### Request
 #### Path Params
 - profileId(Required): The profile id that owns the activity
 - activityId(Required): The activity id to be tracked
 #### Headers
  - Accept-Language(Optional): The language tag to be applied to messages(Locale default to en-US)
  - Content-Type(Required): The api supports only 'application/json'
  - Authorization(Required): Bearer token  
 
> Example Request:

```shell
curl --get 'https://api.sandbox.transferwise.tech/v1/profiles/123/activities/987564/tracker' \
     --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIwMDAwMCIsImNsaWVudF9rZXkiOiJ0dy10ZXN0IiwiaXNzIjoidHciLCJleHAiOjE1NTc4NDQ4MTksImxvY2FsZSI6ImVuX1VTIiwiY2xpZW50X2lkIjoidHctdGVzdCJ9.grw5N0qbCliC-4MDpgaP_Xbzc502VduiBMgeD2ezhsE' \
     --header 'Content-Type: application/json' \
     --header 'Accept-Language: en-US' \
```

### Response  
#### Json Body
  - currentStep: the index of the step current on steps list
  - status: status of the activity(IN_PROGRESS, PROBLEMATIC, FINISHED) 
  - step.id: The id to identify the step 
  - step.title: information about the step with few details about the transfer
  - step.subtitle: additional information about the step
  - step.when: the date the event happened/will happen 

> In progress transfer response example:
```json
{
    "currentStep": 2,
    "status": "IN_PROGRESS",
    "steps": [
        {
            "id": "TRANSFER_CREATED",
            "subtitle": null,
            "title": "You set up your transfer",
            "when": "2019-05-13T14:22:05.442Z"
        },
        {
            "id": "MONEY_RECEIVED",
            "subtitle": null,
            "title": "You used your EU balance",
            "when": "2019-05-13T14:23:00.442Z"
        },
        {
            "id": "CONVERTING_MONEY",
            "subtitle": "We'll pay it out in the next <strong>2 hours</strong>.",
            "title": "Your money's being processed",
            "when": null
        },
        {
            "id": "ESTIMATED_MONEY_SENT_OUT",
            "subtitle": null,
            "title": "We pay out your GBP",
            "when": "2019-05-13T14:24:00Z"
        },
        {
            "id": "ESTIMATED_TRANSFER_COMPLETE",
            "subtitle": null,
            "title": "Your money's due to arrive today",
            "when": "2019-05-13T16:30:00Z"
        }
    ]
}

```

> Completed transfer response example:

```json
{
  "currentStep": 3,
  "status": "FINISHED",
  "steps": [
    {
      "id": "TRANSFER_CREATED",
      "subtitle": null,
      "title": "You set up your transfer",
      "when": "2019-05-13T14:22:05.442Z"
    },
    {
      "id": "MONEY_RECEIVED",
      "subtitle": null,
      "title": "You used your EU balance",
      "when": "2019-05-13T14:23:05.442Z"
    },
    {
      "id": "MONEY_SENT_OUT",
      "subtitle": null,
      "title": "We paid out your EU",
      "when": "2019-04-09T14:24:00.179Z"
    },
    {
      "id": "TRANSFER_COMPLETED",
      "subtitle": "We sent <strong>49.50 EU</strong> to TW recipient.",
      "title": "Your transfer's complete",
      "when": "2019-05-13T16:30:00Z"
    }
  ]
}
```
#### Possible Steps
 - TRANSFER_CREATED 
    > Always present. <br /> 
    Contains id, title and when the transfer was created<br />
    Cannot be the current step   
  - WAITING_FOR_MONEY
    > Present only when the customer said the money have been sent to transferwise and we didn't receive the money yet. <br />
    Contains id, title, subtitle based on payment method <br />
    Can be the current step   
  - MONEY_RECEIVED
    > Present only when we already received the payment <br />
    Contains id, title based on payment method and when we received the money <br />
    Cannot be the current step 
  - DELAYED_MONEY_RECEIVE 
    > Present only when we estimated we should have received the money but we didn't yet <br />
    Contains id, title and subtitle based on payment method <br />
    Can be the current step 
  - ESTIMATED_MONEY_RECEIVE
    > Present only when we didn't receive the money yet <br />
    Contains id, title and when we estimated we'll receive the money** <br /> 
    Cannot be the current step
  - VERIFICATION_IN_PROGRESS
    > Present only when there's a verification in progress for this transfer <br />
    Contains id, title and subtitle <br />
    Can be the current step
  - VERIFICATION_COMPLETED
    > Present only when there's a verification completed for this transfer <br />
    Contains id, title and when the verification has been done <br />
    Cannot be the current step
  - ADDITIONAL_CHECKS_IN_PROGRESS
    > Present only when there's an additional check in progress for this transfer <br />
    Contains id, title and subtitle <br />
    Can be the current step
  - ADDITIONAL_CHECKS_COMPLETED
    > Present only when there's an additional check completed for this transfer <br />
    Contains id, title and when the additional check has been done <br />
    Cannot be the current step
  - CONVERTING_MONEY
    > Present only when the transfer is ready to be transferred to the recipient and there's no delays on the pay out or no verifications <br />
    Contains id, title and subtitle <br />
    Can be the current step   
  - MONEY_SENT_OUT
    > Present only when we have already transferred the money to the recipient account and it's not a balance top up to a transferwise card <br />
    Contains id, title and when we transferred the money <br />
    Cannot be the current step
  - DELAYED_MONEY_SENT_OUT 
    > Present only when we estimated we should have transfer the money but we didn't yet <br />
    Contains id, title and subtitle <br />
    Can be the current step 
  - ESTIMATED_MONEY_SENT_OUT
    > Present only when we didn't transferred the money yet <br />
    Contains id, title and when we estimated we'll transfer the money** <br /> 
    Cannot be the current step
  - DELIVERING_MONEY
    > Present only when we transferred the money to the recipient account, it's not a balance top up to a transferwise card and the estimated delivery date for the transfer has not been reached yet***. <br />
    Contains id, title, subtitle <br />
    Can be the current step 
  - TRANSFER_COMPLETED
    > Present only when we transferred the money to the recipient account and the estimated delivery date for the transfer been reached***. <br />
    Contains id, title, subtitle and when we estimated the money will be delivered to the recipient account<br />
    Can be the current step
  - ESTIMATED_TRANSFER_COMPLETE
    > Present only when we transferred the money to the recipient account and the estimated delivery date for the transfer been not been reached yet***. <br />
    Contains id, title and when we estimate the money will be delivered to the recipient account <br />
    Can be the current step
    
    ** We won't provide estimation dates if there's a delay in the transfer for payment or verification issues.   
    ** We take into account more information to consider a transfer complete other than just the estimated delivery date.   

