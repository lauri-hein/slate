# Borderless Accounts

## Get Account Balance

> Example Request:

```shell
curl -X GET https://api.sandbox.transferwise.tech/v2/borderless-accounts?profileId={profileId} \
     -H "Authorization: Bearer <your api token>" 
```

> Example Response:

```json
[
  {
    "id": <your borderless account id>,
    "profileId": <your profile id>,
    "recipientId": 5742982,
    "creationTime": "2016-07-01T16:02:29Z",
    "modificationTime": "2018-10-20T18:37:21.116Z",
    "active": true,
    "eligible": true,
    "balances": [
      {
        "currency": "GBP",
        "amount": {
          "value": 20.61,
          "currency": "GBP"
        },
        "reservedAmount": {
          "value": 16.2,
          "currency": "GBP"
        },
        "bankDetails": [
          {
            "id": 1000038,
            "profileId": <your profile id>,
            "currency": "GBP",
            "accountHolderName": "Oliver Wilson",
            "bankCode": {
              "sortCode": "23-14-70"
            },
            "accountNumber": {
              "default": "11010101"
            },
            "address": {
              "default": {
                "firstLine": "TransferWise",
                "secondLine": "56 Shoreditch High Street",
                "postCode": "E1 6JJ",
                "city": "London",
                "country": "United Kingdom",
                "stateCode": null
              }
            },
            "limits": {
              "daily": {
                "currency": "GBP",
                "value": null
              },
              "yearly": {
                "currency": "GBP",
                "value": null
              }
            },
            "translations": {
              "accountLimits.daily": "24 hour receive limit",
              "accountNumber.default": "Account number",
              "address.default": "Address",
              "bankCode.sortCode": "UK Sort Code",
              "accountLimits.yearly": "Annual receive limit",
              "accountHolderName": "Account Holder"
            },
            "status": "OPEN"
          }
        ]
      },
      {
        "currency": "EUR",
        "amount": {
          "value": 0,
          "currency": "EUR"
        },
        "reservedAmount": {
          "value": 0,
          "currency": "EUR"
        },
        "bankDetails": [
          {
            "id": 8,
            "profileId": <your profile id>,
            "currency": "EUR",
            "accountHolderName": "Oliver Wilson",
            "bankCode": {
              "swiftCode": "DEKTDE7GXXX"
            },
            "accountNumber": {
              "iban": "DE10 7002 1110 6050 0000 00"
            },
            "address": {
              "default": {
                "firstLine": "Handelsbank",
                "secondLine": "Elsenheimer Str. 41",
                "postCode": "80687",
                "city": "München",
                "country": "Germany",
                "stateCode": null
              }
            },
            "limits": {
              "daily": {
                "currency": "EUR",
                "value": null
              },
              "yearly": {
                "currency": "EUR",
                "value": null
              }
            },
            "translations": {
              "accountLimits.daily": "24 hour receive limit",
              "bankCode.swiftCode": "Bank code (SWIFT / BIC)",
              "accountNumber.iban": "IBAN",
              "address.default": "Address",
              "accountLimits.yearly": "Annual receive limit",
              "accountHolderName": "TW Account Holder"
            },
            "status": "OPEN"
          }
        ]
      }
    ]
  }
]
```
Get available balances for all activated currencies in your borderless account.

### Request

**`GET https://api.sandbox.transferwise.tech/v2/borderless-accounts?profileId={profileId}`**

Use profile id obtained earlier to make this call. 

### Response

Field                             | Description                                   | Format
---------                         | -------                                       | -----------
id                                | Borderless account id                         | Integer
profileId                         | Personal or business profile id               | Integer
recipientId                       | Recipient id you can use for borderless topup transfer  | Integer
creationTime                      | Date when balance account was opened                     | Timestamp
modificationTime                  | Date when balance account setup was modified.            | Timestamp
active                            | Is borderless account active or inactive       | Boolean
eligible                          | Ignore                                         | Boolean
balances[n].currency                 | Currency code      | Text
balances[n].amount.value             | Available balance in specified currency       | Decimal
balances[n].amount.currency          | Currency code       | Text
balances[n].reservedAmount.value     | Reserved amount from your balance | Decimal
balances[n].reservedAmount.currency  | Reserved amount currency code       | Text
balances[n].bankDetails              | Bank account details assigned to your borderless account. Available for EUR, GBP, USD, AUD, NZD  | Group
balances[n].bankDetails.id           | Bank account details id | Integer 
balances[n].bankDetails.currency     | Bank account currency | Text
balances[n].bankDetails.profileId    | Your profileId  | Integer 
balances[n].bankDetails.accountHolderName        | Bank account holder name | Text
balances[n].bankDetails.bankCode                   | Bank codes for these bank details (depends on currency) | Group 
balances[n].bankDetails.bankCode.swiftCode         | BIC/Swift Code (optional) | Text 
balances[n].bankDetails.bankCode.sortCode          | Sort Code (optional) | Text 
balances[n].bankDetails.bankCode.bsb               | Sort Code (optional) | Text 
balances[n].bankDetails.bankCode.achRoutingNumber  | ACH routing number (optional) | Text 
balances[n].bankDetails.bankCode.wireRoutingNumber | Wire routing number (optional) | Text 
balances[n].bankDetails.accountNumber            | Account numbers for these bank details | Group
balances[n].bankDetails.accountNumber.default    | Account number (optional) | Text
balances[n].bankDetails.accountNumber.iban       | IBAN (optional) | Text
balances[n].bankDetails.limits                   | Limits for these bank details | Group
balances[n].bankDetails.limits.daily             | Daily limits | Group
balances[n].bankDetails.limits.daily.currency    | Daily limits currency | Text
balances[n].bankDetails.limits.daily.value       | Daily limit amount (can be null if no limit) | Decimal
balances[n].bankDetails.limits.yearly            | Yearly limits | Group
balances[n].bankDetails.limits.yearly.currency   | Yearly limits currency | Text
balances[n].bankDetails.limits.yearly.value      | Yearly limit amount (can be null if no limit) | Decimal
balances[n].bankDetails.translations             | Labels for all the above fields | Group
balances[n].bankDetails.address                  | Bank address for these bank details | Group
balances[n].bankDetails.address.default.firstLine    | Bank address first line | Text
balances[n].bankDetails.address.default.secondLine   | Bank address second line| Text
balances[n].bankDetails.address.default.city         | Bank address city | Text 
balances[n].bankDetails.address.default.postCode     | Bank address zip code | Text
balances[n].bankDetails.address.default.stateCode    | Bank address state code | Text 
balances[n].bankDetails.address.default.country      | Bank address country | Text 
balances[n].bankDetails.status      | Status of your bank details | Text 



## Get Account Statement

> Example Request:

```shell
curl -X GET https://api.sandbox.transferwise.tech/v3/profiles/{profileId}/borderless-accounts/{borderlessAccountId}/statement.json?
currency=EUR&intervalStart=2018-03-01T00:00:00.000Z&intervalEnd=2018-03-15T23:59:59.999Z&type=COMPACT \
     -H "Authorization: Bearer <your api token>" 
```

> Example Response:

```json
{
  "accountHolder": {
    "type": "PERSONAL",
    "address": {
      "addressFirstLine": "Veerenni 24",
      "city": "Tallinn",
      "postCode": "12112",
      "stateCode": "",
      "countryName": "Estonia"
    },
    "firstName": "Oliver",
    "lastName": "Wilson"
  },
  "issuer": {
    "name": "TransferWise Ltd.",
    "firstLine": "56 Shoreditch High Street",
    "city": "London",
    "postCode": "E1 6JJ",
    "stateCode": "",
    "country": "United Kingdom"
  },
  "bankDetails": null,
  "transactions": [
    {
      "type": "DEBIT",
      "date": "2018-04-30T08:47:05.832Z",
      "amount": {
        "value": -7.76,
        "currency": "EUR"
      },
      "totalFees": {
        "value": 0.04,
        "currency": "EUR"
      },
      "details": {
        "type": "CARD",
        "description": "Card transaction of 6.80 GBP issued by Tfl.gov.uk/cp TFL TRAVEL CH",
        "amount": {
          "value": 6.8,
          "currency": "GBP"
        },
        "category": "Transportation Suburban and Loca",
        "merchant": {
          "name": "Tfl.gov.uk/cp",
          "firstLine": null,
          "postCode": "SW1H 0TL  ",
          "city": "TFL TRAVEL CH",
          "state": "   ",
          "country": "GB",
          "category": "Transportation Suburban and Loca"
        }
      },
      "exchangeDetails": {
        "forAmount": {
          "value": 6.8,
          "currency": "GBP"
        },
        "rate": null
      },
      "runningBalance": {
        "value": 16.01,
        "currency": "EUR"
      },
      "referenceNumber": "CARD-249281"
    },
    {
      "type": "CREDIT",
      "date": "2018-04-17T07:47:00.227Z",
      "amount": {
        "value": 200,
        "currency": "EUR"
      },
      "totalFees": {
        "value": 0,
        "currency": "EUR"
      },
      "details": {
        "type": "DEPOSIT",
        "description": "Received money from HEIN LAURI with reference SVWZ+topup card",
        "senderName": "HEIN LAURI",
        "senderAccount": "EE76 1700 0170 0049 6704 ",
        "paymentReference": "SVWZ+topup card"
      },
      "exchangeDetails": null,
      "runningBalance": {
        "value": 207.69,
        "currency": "EUR"
      },
      "referenceNumber": "TRANSFER-34188888"
    },
    {
      "type": "CREDIT",
      "date": "2018-04-10T05:58:34.681Z",
      "amount": {
        "value": 9.94,
        "currency": "EUR"
      },
      "totalFees": {
        "value": 0,
        "currency": "EUR"
      },
      "details": {
        "type": "CONVERSION",
        "description": "Converted 8.69 GBP to 9.94 EUR",
        "sourceAmount": {
          "value": 8.69,
          "currency": "GBP"
        },
        "targetAmount": {
          "value": 9.94,
          "currency": "EUR"
        },
        "fee": {
          "value": 0.03,
          "currency": "GBP"
        },
        "rate": 1.147806
      },
      "exchangeDetails": null,
      "runningBalance": {
        "value": 9.94,
        "currency": "EUR"
      },
      "referenceNumber": "CONVERSION-1511237"
    }
  ],
  "endOfStatementBalance": {
    "value": 9.94,
    "currency": "EUR"
  },
  "query": {
    "intervalStart": "2018-03-01T00:00:00Z",
    "intervalEnd": "2018-04-30T23:59:59.999Z",
    "currency": "EUR",
    "accountId": 64
  }
}
```

Get borderless account statement for one currency and for specified time range. 
The period between intervalStart and intervalEnd cannot exceed 469 days (around 1 year 3 month).

### Request

**`GET https://api.sandbox.transferwise.tech/v3/profiles/{profileId}/borderless-accounts/{borderlessAccountId}/statement.json?`**

**`currency=EUR&intervalStart=2018-03-01T00:00:00.000Z&intervalEnd=2018-03-15T23:59:59.999Z&type=COMPACT`**

Field                             | Description                                   | Format
---------                         | -------                                       | -----------
borderlessAccountId                   | Your borderlessAccountId is included in [Get Account Balance](#borderless-accounts-get-account-balance) response as field "id".                        | Integer
currency                              | Currency code              | Text
intervalStart                         | Statement start time in UTC time             | Zulu time. Don't forget the 'Z' at the end. 
intervalEnd                           | Statement start time in UTC time             | Zulu time. Don't forget the 'Z' at the end.
type (optional)                       | COMPACT (default) for a single statement line per transaction. FLAT for accounting statements where transaction fees are on a separate line. | Text 

Note that you can also download statements in PDF and CSV formats if you replace statement.json with statement.csv or statement.pdf respectively in the above URL.

### Response

Field                             | Description                                   | Format
---------                         | -------                                       | -----------
accountHolder.type                      | Account holder type: PERSONAL or BUSINESS                        | Text
accountHolder.address.addressFirstLine  | Account holder address street          | Text
accountHolder.address.city              | Account holder address city          | Text
accountHolder.address.postCode          | Account holder address zipc ode | Text
accountHolder.address.stateCode         | Account holder address state | Text
accountHolder.address.countryName       | Account holder address country | Text
accountHolder.firstName                 | Account holder first name | Text
accountHolder.lastName                  | Account holder last name | Text
issuer.name                             | Account issuer name | Text
issuer.firstLine                        | Account issuer address street | Text
issuer.city                             | Account issuer address city | Text
issuer.postCode                         | Account issuer address zip code | Text
issuer.stateCode                        | Account issuer address state | Text
issuer.country                          | Account issuer address country | Text
bankDetails              | Your borderless account bank details       | Group
transactions[n].type                 | DEBIT or CREDIT              | Text
transactions[n].date                 | Time of transaction           | Zulu time
transactions[n].amount.value                 | Transaction amount           | Decimal
transactions[n].amount.currency                 | Transaction currency code             | Text
transactions[n].totalFees.value                 | Transaction fee amount           | Decimal
transactions[n].totalFees.currency                 | Transaction fee currency code             | Text
transactions[n].details.type                 | CARD, CONVERSION, DEPOSIT, TRANSFER, MONEY_ADDED              | Text
transactions[n].details.description                 | Human readable explanation about the transaction           | Text
transactions[n].details.amount.value                 | Amount in original currency (card transactions abroad)              | Decimal
transactions[n].details.amount.currency                 | Original currency code              | Text
transactions[n].details.sourceAmount.value                 | Amount in source currency (conversions)              | Decimal
transactions[n].details.sourceAmount.currency                 | Source currency code              | Text
transactions[n].details.targetAmount.value                 | Amount in target currency (conversions)              | Decimal
transactions[n].details.targetAmount.currency                 | Target currency code              | Text
transactions[n].details.fee.value                 | Conversion fee amount             | Decimal
transactions[n].details.fee.currency                 | Conversion fee currency code              | Text
transactions[n].details.rate                 | Conversion exchange rate            | Decimal
transactions[n].details.senderName                 | Deposit sender name                | Text
transactions[n].details.senderAccount              | Deposit sender bank account details                  | Text
transactions[n].details.paymentReference                 | Deposit payment reference text                  | Text
transactions[n].details.category             |  Card transaction category                 | Text
transactions[n].details.merchant.name             |  Card transaction merchant name                 | Text
transactions[n].details.merchant.firstLine             |  Merchant address street          | Text
transactions[n].details.merchant.postCode             |  Merchant address zipcode                 | Text
transactions[n].details.merchant.city             | Merchant address city                 | Text
transactions[n].details.merchant.state             | Merchant address state              | Text
transactions[n].details.merchant.country            | Merchant address country                 | Text
transactions[n].details.merchant.category             |  Merchant category                 | Text
transactions[n].exchangeDetails.forAmount.value             |  Currency exchange amount                | Decimal
transactions[n].exchangeDetails.forAmount.currency             |  Currency code                 | Text
transactions[n].exchangeDetails.rate             | Exchange rate                 | Decimal
transactions[n].runningBalance.value             | Running balance after the transaction   | Decimal
transactions[n].runningBalance.currency             |  Running balance currency code                | Text
transactions[n].referenceNumber            |TransferWise assigned unique transaction reference number | Text
endOfStatementBalance.value                | Closing balance for specified time period   | Decimal
endOfStatementBalance.currency             | Closing balance currency code | Text
query.intervalStart                | Query parameter repeated             | Zulu time
query.intervalEnd                | Query parameter repeated                 | Zulu time
query.currency                | Query parameter repeated          | Text
query.accountId                | Query parameter repeated         | Integer



## Convert Currencies

> Example Request:

```shell
curl -X POST https://api.sandbox.transferwise.tech/v2/borderless-accounts/{borderlessAccountId}/conversions \
     -H "Authorization: Bearer <your api token>"  \
     -H "Content-Type: application/json" \
     -H "X-idempotence-uuid: <your generated uuid> \
     -d '{ 
            "quoteId": <conversion quote id>
         }'
```

> Example Response:

```json
{
  "id": <conversion transaction id>,
  "type": "CONVERSION",
  "state": "COMPLETED",
  "balancesAfter": [
    {
      "value": 10000594.71,
      "currency": "GBP"
    },
    {
      "value": 9998887.01,
      "currency": "EUR"
    }
  ],
  "creationTime": "2017-11-21T09:55:49.275Z",
  "steps": [
    {
      "id": 369588,
      "type": "CONVERSION",
      "creationTime": "2017-11-21T09:55:49.276Z",
      "balancesAfter": [
        {
          "value": 9998887.01,
          "currency": "EUR"
        },
        {
          "value": 10000594.71,
          "currency": "GBP"
        }
      ],
      "channelName": null,
      "channelReferenceId": null,
      "tracingReferenceCode": null,
      "sourceAmount": {
        "value": 113.48,
        "currency": "EUR"
      },
      "targetAmount": {
        "value": 100,
        "currency": "GBP"
      },
      "fee": {
        "value": 0.56,
        "currency": "EUR"
      },
      "rate": 0.88558
    }
  ],
  "sourceAmount": {
    "value": 113.48,
    "currency": "EUR"
  },
  "targetAmount": {
    "value": 100,
    "currency": "GBP"
  },
  "rate": 0.88558,
  "feeAmounts": [
    {
      "value": 0.56,
      "currency": "EUR"
    }
  ]
}
```
Convert funds between your borderless account currencies.
Quote which is used in this call must have type "BALANCE_CONVERSION".

Note that this call needs an extra field in header called "X-idempotence-uuid".


### Request

**`POST https://api.sandbox.transferwise.tech/v2/borderless-accounts/{borderlessAccountId}/conversions`**

Field                             | Description                                   | Format
---------                         | -------                                       | -----------
borderlessAccountId               | Your borderlessAccountId is included in [Get Account Balance](#borderless-accounts-get-account-balance) response as field "id".                        | Integer
X-idempotence-uuid                | Unique identifier assinged by you. Used for idempotency check purposes. Should your call fail for technical reasons then you can use the same value again for making retry call. | UUID



## Get Available Currency Codes

Get list of currencies that your can hold in your borderless account.

> Example Request:

```shell
curl -X GET https://api.sandbox.transferwise.tech/v2/borderless-accounts-configuration/profiles/<your_profile_id>/available-currencies \
     -H "Authorization: Bearer <your api token>" 
     
```

> Example Response:

```json
[
    "EUR",
    "GBP",
    "USD",
...
    "UAH",
    "ARS",
    "NPR"
]
```

#### Request

**`GET https://api.sandbox.transferwise.tech/v2/borderless-accounts-configuration/profiles/<your_profile_id>/available-currencies`**

#### Response

Array of 3-letter currency codes according to the [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) 

## Get Available Currency Information

Get list of currencies that your can hold in your borderless account. Also shows which currencies have the option to get bank account details.

> Example Request:

```shell

curl -X GET https://api.sandbox.transferwise.tech/v2/borderless-accounts-configuration/profiles/<your_profile_id>/available-currencies \
     -H "Prefer: return=information" \
     -H "Authorization: Bearer <your api token>"
```

> Example Response:

```json
[
    {
        "code": "EUR",
        "hasBankDetails": true,
        "payInAllowed": true,
        "sampleBankDetails": {...}
    },
    {
        "code": "GBP",
        "hasBankDetails": true,
        "payInAllowed": true,
        "sampleBankDetails": {...}
    },
    {
        "code": "USD",
        "hasBankDetails": false,
        "payInAllowed": true,
        "sampleBankDetails": {...}
    },
...
    {
        "code": "UAH",
        "hasBankDetails": false,
        "payInAllowed": false,
        "sampleBankDetails": null
    },
    {
        "code": "ARS",
        "hasBankDetails": false,
        "payInAllowed": false,
        "sampleBankDetails": null
    },
    {
        "code": "NPR",
        "hasBankDetails": false,
        "payInAllowed": false,
        "sampleBankDetails": null
    }
]
```

#### Request

**`
GET -H "Prefer: return=information" https://api.sandbox.transferwise.tech/v2/borderless-accounts-configuration/profiles/<your_profile_id>/available-currencies`**

#### Response

Field                             | Description             | Format
---------                         | -------                 | -----------
code                              | Currency code           | Text
hasBankDetails                    | Does currency have bank details opening option   | Boolean
payInAllowed                      | Can you send this currency to your borderless account  | Boolean
sampleBankDetails                 |      | 

<br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/>

## Get Currency Pairs

> Example Request:

```shell
curl -X GET https://api.sandbox.transferwise.tech/v1/currency-pairs \
     -H "Authorization: Bearer <your api token>" 
```

> Example Response:

```json
{
    "sourceCurrencies": [
        {
            "currencyCode": "GBP",
            "maxInvoiceAmount": 1000000,
            "targetCurrencies": [
                {
                    "currencyCode": "EUR",
                    "minInvoiceAmount": 1,
                    "fixedTargetPaymentAllowed": true
                },
                {
                    "currencyCode": "INR",
                    "minInvoiceAmount": 1,
                    "fixedTargetPaymentAllowed": true
                },
                {
                    "currencyCode": "USD",
                    "minInvoiceAmount": 1,
                    "fixedTargetPaymentAllowed": true
                },
...
                {
                    "currencyCode": "VND",
                    "minInvoiceAmount": 1,
                    "fixedTargetPaymentAllowed": true
                },
                {
                    "currencyCode": "ZAR",
                    "minInvoiceAmount": 1,
                    "fixedTargetPaymentAllowed": true
                }
            ],
            "totalTargetCurrencies": 47
        }
    ],
    "total": 19
}
```

Get list of allowed currency pairs that your can setup your transfers. 

### Request

**`GET https://api.sandbox.transferwise.tech/v1/currency-pairs`**


### Response

Field                                      | Description                                                       | Format
---------                                  | -------                                                           | -----------
sourceCurrencies.currencyCode              | Source currency code                                              | Text
sourceCurrencies.maxInvoiceAmount          | Maximum allowed transfer amount in source currency                | Decimal
targetCurrencies.currencyCode              | Target currency code                                              | Text
targetCurrencies.minInvoiceAmount          | Minimum allowed transfer amount in source currency for this pair. | Decimal
targetCurrencies.fixedTargetPaymentAllowed | Can you setup fixed rate payments or not.                         | Boolean

<br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/>
<br/><br/><br/><br/><br/><br/><br/>
