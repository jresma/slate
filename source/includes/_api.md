## <a name="resource-attachment">Attachment</a>

Stability: `prototype`

attachment

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **created_at** | *date-time* | when attachment was created | `"2015-01-01T12:00:00Z"` |
| **filename** | *string* | attachment filename | `"image.png"` |
| **id** | *integer* | attachment ID | `1001` |
| **owner** | *object* | attachment category | `{"id":1,"type":["Receipt"]}` |
| **size** | *nullable integer* | attachment size | `123000` |
| **url** | *string* | link to attachment file | `"http://storage.indinero.com/receipts/1/attachments/1/download"` |


## <a name="resource-bank_account">Bank Account</a>

Stability: `prototype`

Bank account items added to user's company.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **account_name** | *string* | Bank Account name | `"Bank of Asia"` |
| **account_number_string** | *nullable string* | Account number in string format | `null` |
| **balance** | *number* | Bank account balance | `5000.0` |
| **checking_account_number** | *nullable string* | Checking account number | `null` |
| **coa_number** | *nullable string* | Chart of account number | `null` |
| **company_id** | *integer* | Company identifier of the company where the account belongs to. | `301` |
| **created_at** | *nullable date-time* | when the item was created | `null` |
| **currency_code** | *nullable string* | Currency code | `"USD"` |
| **discontinued** | *boolean* | Discontinued | `false` |
| **id** | *integer* | Unique identifier of bank account | `100` |
| **indinero_status** | *nullable integer* | inDinero status of the bank account | `3` |
| **intuit_id** | *nullable integer* | Identifier of the account when pulled from Intuit | `null` |
| **item_id** | *nullable integer* | The Financial account the bank account belongs to. | `200` |
| **stripe_account_id** | *nullable string* | Stripe account id | `null` |
| **svb_account_number** | *nullable string* | SVB account number if the account is from SVB | `null` |
| **updated_at** | *nullable date-time* | when the item was last updated | `null` |

### Bank Account List

This endpoint retrieves all bank accounts.

```
GET /api/v2/bank_accounts
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/bank_accounts
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 100,
    "item_id": 200,
    "company_id": 301,
    "account_name": "Bank of Asia",
    "created_at": "2015-01-01T12:00:00Z",
    "updated_at": "2015-01-01T12:00:00Z",
    "currency_code": "USD",
    "balance": 5000.0,
    "indinero_status": 3,
    "svb_account_number": null,
    "intuit_id": null,
    "account_number_string": null,
    "discontinued": false,
    "checking_account_number": null,
    "coa_number": null,
    "stripe_account_id": null
  }
]
```


## <a name="resource-category">Category</a>

Stability: `prototype`

A chart of accounts is a listing of the names of the accounts that a company has identified and made available for recording trransactions in its general ledger. A company has the flexibility to tailor its chart of accounts to best suit its needs, including adding accounts as needed.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **account_number** | *string* | account number | `"5010-00"` |
| **active** | *boolean* | is active | `true` |
| **built_in** | *boolean* | is built in | `true` |
| **deprecated** | *boolean* | is deprecated | `false` |
| **id** | *integer* | unique identifier of category | `654321` |
| **in_trend** | *boolean* | is in trend | `true` |
| **master_category** | *nullable object* | master category | `{"id":123456,"name":"Travel","built_in":true,"transaction_type_name":"both"}` |
| **name** | *string* | unique name of category | `"Auto/Fuel"` |
| **sub_type_id** | *integer* | sub type ID | `32` |
| **transaction_type_name** | *string* | type name | `"both"` |

### Category List

List existing categories.

```
GET /api/v2/categories
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/categories
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 654321,
    "name": "Auto/Fuel",
    "master_category": {
      "id": 123456,
      "name": "Travel",
      "built_in": true,
      "transaction_type_name": "both"
    },
    "built_in": true,
    "transaction_type_name": "both",
    "in_trend": true,
    "deprecated": false,
    "active": true,
    "account_number": "5010-00",
    "sub_type_id": 32
  }
]
```


## <a name="resource-company">Company</a>

Stability: `prototype`

A company in the Indinero App.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **fiscal_year_end** | *string* | Fiscal year end date. | `"12/31"` |
| **id** | *integer* | Unique identity of a company | `401230` |
| **name** | *string* | Name of the company | `"Acme Co"` |

### Company Company Details

Detailed company information

```
GET /api/v2/company
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/company
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 401230,
  "name": "Acme Co",
  "fiscal_year_end": "12/31"
}
```

### Company Company Logo

Logo of the company

```
GET /api/v2/company/logo
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/company/logo
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 401230,
  "name": "Acme Co",
  "fiscal_year_end": "12/31"
}
```


## <a name="resource-credit_card">Credit Card</a>

Stability: `prototype`

Credit card financial accounts added to company as data source.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **account_name** | *string* | Credit Card Account name | `"Bank of Asia"` |
| **account_number_string** | *nullable string* | account number string | `null` |
| **balance** | *number* | Credit card balance | `5000.0` |
| **coa_number** | *nullable string* | Chart of Accounts number | `null` |
| **company_id** | *integer* | Company ID | `301` |
| **created_at** | *nullable date-time* | when the item was created | `null` |
| **credit_limit** | *nullable string* | The card's credit limit | `5000` |
| **currency_code** | *nullable string* | currency code | `"USD"` |
| **discontinued** | *boolean* | discontinued | `false` |
| **id** | *integer* | unique identifier of credit card | `100` |
| **indinero_status** | *nullable integer* | inDinero status | `3` |
| **intuit_id** | *nullable integer* | intuit id | `null` |
| **item_id** | *nullable integer* | Financial account | `200` |
| **updated_at** | *nullable date-time* | when the item was last updated | `null` |

### Credit Card List

This endpoint retrieves all credit cards.

```
GET /api/v2/credit_cards
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/credit_cards
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 100,
    "item_id": 200,
    "company_id": 301,
    "account_name": "Bank of Asia",
    "created_at": "2015-01-01T12:00:00Z",
    "updated_at": "2015-01-01T12:00:00Z",
    "currency_code": "USD",
    "balance": 5000.0,
    "indinero_status": 3,
    "intuit_id": null,
    "account_number_string": null,
    "discontinued": false,
    "coa_number": null,
    "credit_limit": 5000
  }
]
```


## <a name="resource-financial_account">Financial Account</a>

Stability: `prototype`

Financial account items added to user's company.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **company_id** | *integer* | Company ID | `100` |
| **container_type** | *string* | Container type | `"bank"` |
| **created_at** | *nullable date-time* | when the item was created | `null` |
| **display_error** | *nullable boolean* | For the view, if the error should be displayed or not | `true` |
| **id** | *integer* | unique identifier of financial account | `100` |
| **intuit_id** | *nullable integer* | intuit id | `null` |
| **intuit_status_code** | *nullable integer* | Account status from Intuit | `185` |
| **last_transaction_date** | *nullable date* | Date of the lastest transaction | `null` |
| **last_update_attempt** | *nullable date-time* | when the item update was last attempted | `null` |
| **last_update_time** | *nullable date-time* | when the item was updated | `null` |
| **linked_item_id** | *nullable integer* | Identifier of the financial account linked to this account. | `4010301021` |
| **mfa** | *nullable string* | Serialized multifactor authentication Questions | `"[\"Name of your favorite street?\"]"` |
| **name** | *string* | Financial Account name | `"Bank of Asia"` |
| **poll_status** | *nullable integer* | Status of the poll when updating | `4` |
| **refresh_status_code** | *nullable integer* | refresh status code | `1` |
| **routing_number** | *nullable integer* | Routing number of the financial account | `12345678901` |
| **send_banklog_email** | *nullable boolean* | Setting if the bank log email should be sent for this account | `true` |
| **service_id** | *integer* | service id | `100` |
| **start_poll_time** | *nullable date-time* | Time when the poll for download started | `null` |
| **status** | *nullable integer* | Status of the financial account, whether set to 'automatic' or 'manual' | `"automatic"` |
| **updated_at** | *nullable date-time* | when the item was last updated | `null` |

### Financial Account List

This endpoint retrieves all financial accounts.

```
GET /api/v2/financial_accounts
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/financial_accounts
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 100,
    "intuit_id": null,
    "service_id": 100,
    "company_id": 100,
    "name": "Bank of Asia",
    "container_type": "bank",
    "refresh_status_code": 1,
    "last_update_attempt": "2015-01-01T12:00:00Z",
    "last_update_time": "2015-01-01T12:00:00Z",
    "created_at": "2015-01-01T12:00:00Z",
    "updated_at": "2015-01-01T12:00:00Z",
    "mfa": "[\"Name of your favorite street?\"]",
    "start_poll_time": "2015-01-01T12:00:00Z",
    "poll_status": 4,
    "linked_item_id": 4010301021,
    "intuit_status_code": 185,
    "routing_number": 12345678901,
    "display_error": true,
    "send_banklog_email": true,
    "status": "automatic",
    "last_transaction_date": "example"
  }
]
```


## <a name="resource-receipt">Receipt</a>

Stability: `prototype`

receipt

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **amount** | *nullable number* | receipt amount | `1234.0` |
| **attachments** | *array* | list of receipt attachments | `[{"id":1001,"owner":{"id":1,"type":["Receipt"]},"url":"http://storage.indinero.com/receipts/1/attachments/1/download","filename":"image.png","size":123000,"created_at":"2015-01-01T12:00:00Z"}]` |
| **[category:account_number](#resource-category)** | *string* | account number | `"5010-00"` |
| **[category:active](#resource-category)** | *boolean* | is active | `true` |
| **[category:built_in](#resource-category)** | *boolean* | is built in | `true` |
| **[category:deprecated](#resource-category)** | *boolean* | is deprecated | `false` |
| **[category:id](#resource-category)** | *integer* | unique identifier of category | `654321` |
| **[category:in_trend](#resource-category)** | *boolean* | is in trend | `true` |
| **[category:master_category](#resource-category)** | *nullable object* | master category | `{"id":123456,"name":"Travel","built_in":true,"transaction_type_name":"both"}` |
| **[category:name](#resource-category)** | *string* | unique name of category | `"Auto/Fuel"` |
| **[category:sub_type_id](#resource-category)** | *integer* | sub type ID | `32` |
| **[category:transaction_type_name](#resource-category)** | *string* | type name | `"both"` |
| **[company:fiscal_year_end](#resource-company)** | *string* | Fiscal year end date. | `"12/31"` |
| **[company:id](#resource-company)** | *integer* | Unique identity of a company | `401230` |
| **[company:name](#resource-company)** | *string* | Name of the company | `"Acme Co"` |
| **created_at** | *date-time* | when receipt was created | `"2015-01-01T12:00:00Z"` |
| **description** | *string* | receipt description | `"Gas for getting to client facility"` |
| **email** | *nullable string* | receipt email | `"email@example.com"` |
| **email_date** | *nullable date-time* | receipt email date | `"2015-01-01T12:00:00Z"` |
| **email_id** | *nullable string* | receipt email_id | `42` |
| **id** | *integer* | unique identifier of receipt | `1001` |
| **merchant** | *nullable string* | receipt merchant | `"Shell"` |
| **processor** | *nullable string* | receipt processor | `"mobile_works"` |
| **receipt_type** | *string* | type of receipt | `"Receipt"` |
| **resend_date** | *nullable date* | when receipt resent | `"2015-01-01"` |
| **status** | *nullable integer* | receipt status | `1` |
| **subject** | *nullable string* | receipt email subject | `"Auto/Fuel (upload from iOS app)"` |

### Receipt Create

Create a new receipt.

```
POST /api/v2/receipts
```


#### Curl Example

```bash
$ curl -n -X POST https://api.indinero.com/api/v2/receipts \
  -d '{
}' \
  -H "Content-Type: application/json"
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "id": 1001,
  "category": {
    "id": 654321,
    "name": "Auto/Fuel",
    "master_category": {
      "id": 123456,
      "name": "Travel",
      "built_in": true,
      "transaction_type_name": "both"
    },
    "built_in": true,
    "transaction_type_name": "both",
    "in_trend": true,
    "deprecated": false,
    "active": true,
    "account_number": "5010-00",
    "sub_type_id": 32
  },
  "company": {
    "id": 401230,
    "name": "Acme Co",
    "fiscal_year_end": "12/31"
  },
  "receipt_type": "Receipt",
  "amount": 1234.0,
  "subject": "Auto/Fuel (upload from iOS app)",
  "description": "Gas for getting to client facility",
  "status": 1,
  "processor": "mobile_works",
  "merchant": "Shell",
  "email": "email@example.com",
  "email_id": 42,
  "email_date": "2015-01-01T12:00:00Z",
  "created_at": "2015-01-01T12:00:00Z",
  "resend_date": "2015-01-01",
  "attachments": [
    {
      "id": 1001,
      "owner": {
        "id": 1,
        "type": [
          "Receipt"
        ]
      },
      "url": "http://storage.indinero.com/receipts/1/attachments/1/download",
      "filename": "image.png",
      "size": 123000,
      "created_at": "2015-01-01T12:00:00Z"
    }
  ]
}
```

### Receipt List

list existing receipts.

```
GET /api/v2/receipts
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/receipts
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 1001,
    "category": {
      "id": 654321,
      "name": "Auto/Fuel",
      "master_category": {
        "id": 123456,
        "name": "Travel",
        "built_in": true,
        "transaction_type_name": "both"
      },
      "built_in": true,
      "transaction_type_name": "both",
      "in_trend": true,
      "deprecated": false,
      "active": true,
      "account_number": "5010-00",
      "sub_type_id": 32
    },
    "company": {
      "id": 401230,
      "name": "Acme Co",
      "fiscal_year_end": "12/31"
    },
    "receipt_type": "Receipt",
    "amount": 1234.0,
    "subject": "Auto/Fuel (upload from iOS app)",
    "description": "Gas for getting to client facility",
    "status": 1,
    "processor": "mobile_works",
    "merchant": "Shell",
    "email": "email@example.com",
    "email_id": 42,
    "email_date": "2015-01-01T12:00:00Z",
    "created_at": "2015-01-01T12:00:00Z",
    "resend_date": "2015-01-01",
    "attachments": [
      {
        "id": 1001,
        "owner": {
          "id": 1,
          "type": [
            "Receipt"
          ]
        },
        "url": "http://storage.indinero.com/receipts/1/attachments/1/download",
        "filename": "image.png",
        "size": 123000,
        "created_at": "2015-01-01T12:00:00Z"
      }
    ]
  }
]
```


## <a name="resource-reimbursement">Reimbursement</a>

Stability: `prototype`

Reimbursement

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **attachments** | *array* | List of attachments | `[{"id":1001,"owner":{"id":1,"type":["Receipt"]},"url":"http://storage.indinero.com/receipts/1/attachments/1/download","filename":"image.png","size":123000,"created_at":"2015-01-01T12:00:00Z"}]` |
| **cannot_process_reason** | *nullable string* | Reason why the reimbursement was not processed | `"ACH payment failed"` |
| **[category:account_number](#resource-category)** | *string* | account number | `"5010-00"` |
| **[category:active](#resource-category)** | *boolean* | is active | `true` |
| **[category:built_in](#resource-category)** | *boolean* | is built in | `true` |
| **[category:deprecated](#resource-category)** | *boolean* | is deprecated | `false` |
| **[category:id](#resource-category)** | *integer* | unique identifier of category | `654321` |
| **[category:in_trend](#resource-category)** | *boolean* | is in trend | `true` |
| **[category:master_category](#resource-category)** | *nullable object* | master category | `{"id":123456,"name":"Travel","built_in":true,"transaction_type_name":"both"}` |
| **[category:name](#resource-category)** | *string* | unique name of category | `"Auto/Fuel"` |
| **[category:sub_type_id](#resource-category)** | *integer* | sub type ID | `32` |
| **[category:transaction_type_name](#resource-category)** | *string* | type name | `"both"` |
| **company_id** | *integer* | Company identifier the reimbursement is part of. | `123` |
| **created_at** | *nullable date-time* | Time when the reimbursement was created | `null` |
| **description** | *string* | Description of the reimbursement submitted. | `"Github Processing Fee."` |
| **employee** | *nullable object* | Employee who submitted the reimbursement request | `null` |
| **employee:email** | *nullable string* | Employee's email address | `"harrison.redford@example.com"` |
| **employee:full_name** | *nullable string* | Employee's full name | `"Harrison Redford"` |
| **id** | *integer* | Unique identifier of the reimbursement. | `123` |
| **person:full_name** | *nullable string* | Full name of the person | `"John Done"` |
| **status** | *integer* | A reimbursements status: Draft: -1, Pending: 0, For processing: 1, Rejected: 2, Processing: 3, Reimbursed: 4, Archived: 5, Cannot Process: 6<br/> **one of:**`-1` or `0` or `1` or `2` or `3` or `4` or `5` or `6` | `3` |
| **value** | *string* | Amount to reimburse. | `"9.99"` |

### Reimbursement List

List reimbursements

```
GET /api/v2/reimbursements
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/reimbursements
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 123,
    "company_id": 123,
    "attachments": [
      {
        "id": 1001,
        "owner": {
          "id": 1,
          "type": [
            "Receipt"
          ]
        },
        "url": "http://storage.indinero.com/receipts/1/attachments/1/download",
        "filename": "image.png",
        "size": 123000,
        "created_at": "2015-01-01T12:00:00Z"
      }
    ],
    "status": 3,
    "value": "9.99",
    "description": "Github Processing Fee.",
    "created_at": "2015-01-01T12:00:00Z",
    "cannot_process_reason": "ACH payment failed",
    "employee": {
      "full_name": "Harrison Redford",
      "email": "harrison.redford@example.com"
    },
    "person": {
      "full_name": "John Done"
    },
    "category": {
      "id": 654321,
      "name": "Auto/Fuel",
      "master_category": {
        "id": 123456,
        "name": "Travel",
        "built_in": true,
        "transaction_type_name": "both"
      },
      "built_in": true,
      "transaction_type_name": "both",
      "in_trend": true,
      "deprecated": false,
      "active": true,
      "account_number": "5010-00",
      "sub_type_id": 32
    }
  }
]
```

### Reimbursement Update

Update reimbursement

```
PATCH /api/v2/reimbursements/{reimbursement_id}
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **reimbursement:category_id** | *integer* | unique identifier of category | `654321` |


#### Curl Example

```bash
$ curl -n -X PATCH https://api.indinero.com/api/v2/reimbursements/$REIMBURSEMENT_ID \
  -d '{
  "reimbursement": {
    "category_id": 1234
  }
}' \
  -H "Content-Type: application/json"
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 123,
  "company_id": 123,
  "attachments": [
    {
      "id": 1001,
      "owner": {
        "id": 1,
        "type": [
          "Receipt"
        ]
      },
      "url": "http://storage.indinero.com/receipts/1/attachments/1/download",
      "filename": "image.png",
      "size": 123000,
      "created_at": "2015-01-01T12:00:00Z"
    }
  ],
  "status": 3,
  "value": "9.99",
  "description": "Github Processing Fee.",
  "created_at": "2015-01-01T12:00:00Z",
  "cannot_process_reason": "ACH payment failed",
  "employee": {
    "full_name": "Harrison Redford",
    "email": "harrison.redford@example.com"
  },
  "person": {
    "full_name": "John Done"
  },
  "category": {
    "id": 654321,
    "name": "Auto/Fuel",
    "master_category": {
      "id": 123456,
      "name": "Travel",
      "built_in": true,
      "transaction_type_name": "both"
    },
    "built_in": true,
    "transaction_type_name": "both",
    "in_trend": true,
    "deprecated": false,
    "active": true,
    "account_number": "5010-00",
    "sub_type_id": 32
  }
}
```

### Reimbursement Approve reimbursements

Approve reimbursements

```
POST /api/v2/reimbursements/actions/approve
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **reimbursement_ids** | *array* | List of reimbursement ids. | `[5]` |



#### Curl Example

```bash
$ curl -n -X POST https://api.indinero.com/api/v2/reimbursements/actions/approve \
  -d '{
  "reimbursement_ids": [
    5
  ]
}' \
  -H "Content-Type: application/json"
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 123,
    "company_id": 123,
    "attachments": [
      {
        "id": 1001,
        "owner": {
          "id": 1,
          "type": [
            "Receipt"
          ]
        },
        "url": "http://storage.indinero.com/receipts/1/attachments/1/download",
        "filename": "image.png",
        "size": 123000,
        "created_at": "2015-01-01T12:00:00Z"
      }
    ],
    "status": 3,
    "value": "9.99",
    "description": "Github Processing Fee.",
    "created_at": "2015-01-01T12:00:00Z",
    "cannot_process_reason": "ACH payment failed",
    "employee": {
      "full_name": "Harrison Redford",
      "email": "harrison.redford@example.com"
    },
    "person": {
      "full_name": "John Done"
    },
    "category": {
      "id": 654321,
      "name": "Auto/Fuel",
      "master_category": {
        "id": 123456,
        "name": "Travel",
        "built_in": true,
        "transaction_type_name": "both"
      },
      "built_in": true,
      "transaction_type_name": "both",
      "in_trend": true,
      "deprecated": false,
      "active": true,
      "account_number": "5010-00",
      "sub_type_id": 32
    }
  }
]
```

### Reimbursement Reject reimbursements

Reject reimbursements

```
POST /api/v2/reimbursements/actions/reject
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **reimbursement_ids** | *array* | List of reimbursement ids. | `[5]` |



#### Curl Example

```bash
$ curl -n -X POST https://api.indinero.com/api/v2/reimbursements/actions/reject \
  -d '{
  "reimbursement_ids": [
    5
  ]
}' \
  -H "Content-Type: application/json"
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 123,
    "company_id": 123,
    "attachments": [
      {
        "id": 1001,
        "owner": {
          "id": 1,
          "type": [
            "Receipt"
          ]
        },
        "url": "http://storage.indinero.com/receipts/1/attachments/1/download",
        "filename": "image.png",
        "size": 123000,
        "created_at": "2015-01-01T12:00:00Z"
      }
    ],
    "status": 3,
    "value": "9.99",
    "description": "Github Processing Fee.",
    "created_at": "2015-01-01T12:00:00Z",
    "cannot_process_reason": "ACH payment failed",
    "employee": {
      "full_name": "Harrison Redford",
      "email": "harrison.redford@example.com"
    },
    "person": {
      "full_name": "John Done"
    },
    "category": {
      "id": 654321,
      "name": "Auto/Fuel",
      "master_category": {
        "id": 123456,
        "name": "Travel",
        "built_in": true,
        "transaction_type_name": "both"
      },
      "built_in": true,
      "transaction_type_name": "both",
      "in_trend": true,
      "deprecated": false,
      "active": true,
      "account_number": "5010-00",
      "sub_type_id": 32
    }
  }
]
```


## <a name="resource-transaction">Transaction</a>

Stability: `prototype`

An accounting transaction is a business event having a monetary impact on the financial statements of a business. It is recorded in the accounting records of the business.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **account** | *string* | Bank account items added to user's company. or Credit card financial accounts added to company as data source. |  |
| **amount** | *number* | Amount of the transaction | `42.0` |
| **base_type** | *string* | Base type of the transaction: either credit or debit | `"credit"` |
| **category_id** | *nullable integer* | ID of the category of the transaction | `null` |
| **company_id** | *number* | The ID of the company who owns the transaction | `42.0` |
| **container_type** | *nullable string* | Container type of the transaction - bank or credits | `null` |
| **currency_code** | *nullable string* | Currency code for the transaction amount | `"USD"` |
| **description_auto** | *nullable string* | Transaction description parsed by the app during import | `null` |
| **description_user** | *nullable string* | Transaction description input by a user | `null` |
| **detail** | *string* | Description of transaction based on financial institution statements | `"example"` |
| **id** | *integer* | unique identifier of transaction | `42` |
| **memo** | *nullable string* | Notes about the transaction | `null` |
| **post_date** | *nullable date-time* | Date of posting of the transaction | `null` |
| **real_amount** | *number* | Real amount of the transaction | `42.0` |
| **split_id** | *nullable integer* | ID of the parent transaction if it's split transaction | `null` |

### Transaction List

This endpoint retrieves all transactions.

```
GET /api/v2/transactions
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/transactions
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
[
  {
    "id": 42,
    "company_id": 42.0,
    "amount": 42.0,
    "real_amount": 42.0,
    "account": {
      "id": 100,
      "item_id": 200,
      "company_id": 301,
      "account_name": "Bank of Asia",
      "created_at": "2015-01-01T12:00:00Z",
      "updated_at": "2015-01-01T12:00:00Z",
      "currency_code": "USD",
      "balance": 5000.0,
      "indinero_status": 3,
      "svb_account_number": null,
      "intuit_id": null,
      "account_number_string": null,
      "discontinued": false,
      "checking_account_number": null,
      "coa_number": null,
      "stripe_account_id": null
    },
    "post_date": "2015-01-01T12:00:00Z",
    "container_type": "example",
    "description_user": "example",
    "description_auto": "example",
    "detail": "example",
    "memo": "example",
    "base_type": "credit",
    "currency_code": "USD",
    "split_id": 42,
    "category_id": 42
  }
]
```


## <a name="resource-trends">Trends</a>

Stability: `prototype`

The company's financial analytics, during a certain period.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **data/amount** | *number* | amount per date | `2494.06` |
| **data/date** | *date* | trend date | `"2016-08-01"` |
| **end_date** | *date* | ending day of trend period | `"2016-08-03"` |
| **has_invoice_entries** | *boolean* | if it includes invoices during the trend period | `true` |
| **last_month** | *date-time* | the previous month | `"2016-07-03T21:32:44Z"` |
| **section** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **start_date** | *date* | starting day of trend period | `"2016-05-01"` |
| **subsection** | *string* | trends subsection<br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |
| **two_months_ago** | *date-time* | the previous 2 months | `"2016-06-03T21:32:44Z"` |


## <a name="resource-trends-categories">Trends: Categories</a>

Stability: `prototype`

The company's financial analytics, during a certain period, grouped by category.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **data/amount** | *number* | amount spent per category | `23456.0` |
| **[data/category:account_number](#resource-category)** | *string* | account number | `"5010-00"` |
| **[data/category:active](#resource-category)** | *boolean* | is active | `true` |
| **[data/category:built_in](#resource-category)** | *boolean* | is built in | `true` |
| **[data/category:deprecated](#resource-category)** | *boolean* | is deprecated | `false` |
| **[data/category:id](#resource-category)** | *integer* | unique identifier of category | `654321` |
| **[data/category:in_trend](#resource-category)** | *boolean* | is in trend | `true` |
| **[data/category:master_category](#resource-category)** | *nullable object* | master category | `{"id":123456,"name":"Travel","built_in":true,"transaction_type_name":"both"}` |
| **[data/category:name](#resource-category)** | *string* | unique name of category | `"Auto/Fuel"` |
| **[data/category:sub_type_id](#resource-category)** | *integer* | sub type ID | `32` |
| **[data/category:transaction_type_name](#resource-category)** | *string* | type name | `"both"` |
| **[end_date](#resource-trends)** | *date* | ending day of trend period | `"2016-08-03"` |
| **[has_invoice_entries](#resource-trends)** | *boolean* | if it includes invoices during the trend period | `true` |
| **[last_month](#resource-trends)** | *date-time* | the previous month | `"2016-07-03T21:32:44Z"` |
| **[section](#resource-trends)** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **[start_date](#resource-trends)** | *date* | starting day of trend period | `"2016-05-01"` |
| **[subsection](#resource-trends)** | *string* | trends subsection<br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |
| **[two_months_ago](#resource-trends)** | *date-time* | the previous 2 months | `"2016-06-03T21:32:44Z"` |

### Trends: Categories Request

Get trends by categories.

```
GET /api/v2/trends/categories
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **end_date** | *date* |  | `"2016-08-03"` |
| **section** | *string* | <br/> **default:** `"home"`<br/> **one of:**`"home"` or `"revenue"` or `"spending"` | `"home"` |
| **start_date** | *date* |  | `"2016-05-01"` |
| **subsection** | *string* | <br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/trends/categories
 -G \
  -d section=home \
  -d subsection=overview \
  -d start_date=2016-05-01 \
  -d end_date=2016-08-03
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "data": [
    {
      "category": {
        "id": 654321,
        "name": "Auto/Fuel",
        "master_category": {
          "id": 123456,
          "name": "Travel",
          "built_in": true,
          "transaction_type_name": "both"
        },
        "built_in": true,
        "transaction_type_name": "both",
        "in_trend": true,
        "deprecated": false,
        "active": true,
        "account_number": "5010-00",
        "sub_type_id": 32
      },
      "amount": 23456.0
    }
  ],
  "last_month": "2016-07-03T21:32:44Z",
  "two_months_ago": "2016-06-03T21:32:44Z",
  "section": "revenue",
  "subsection": "overview",
  "start_date": "2016-05-01",
  "end_date": "2016-08-03",
  "has_invoice_entries": true
}
```


## <a name="resource-trends-chart_data">Trends: Chart Data</a>

Stability: `prototype`

The company's graph report, during a certain period.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **[end_date](#resource-trends)** | *date* | ending day of trend period | `"2016-08-03"` |
| **[section](#resource-trends)** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **series/data/amount** | *number* | amount per date | `2494.06` |
| **series/data/date** | *date* | trend date | `"2016-08-01"` |
| **series/name** | *string* | series name<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **[start_date](#resource-trends)** | *date* | starting day of trend period | `"2016-05-01"` |
| **[subsection](#resource-trends)** | *string* | trends subsection<br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |
| **type** | *string* | chart type<br/> **one of:**`"home"` or `"revenue"` or `"spending"` or `"cash"` | `"home"` |

### Trends: Chart Data Request

Get trends chart data.

```
GET /api/v2/trends/chart_date
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **type** | *string* | chart type<br/> **one of:**`"home"` or `"revenue"` or `"spending"` or `"cash"` | `"home"` |


#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **end_date** | *date* | ending day of trend period | `"2016-08-03"` |
| **section** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **start_date** | *date* | starting day of trend period | `"2016-05-01"` |
| **subsection** | *string* | trends subsection<br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/trends/chart_date
 -G \
  -d type=home \
  -d section=revenue \
  -d subsection=overview \
  -d start_date=2016-05-01 \
  -d end_date=2016-08-03
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "series": [
    {
      "name": "revenue",
      "data": [
        {
          "date": "2016-08-01",
          "amount": 2494.06
        }
      ]
    }
  ],
  "type": "home",
  "section": "revenue",
  "subsection": "overview",
  "start_date": "2016-05-01",
  "end_date": "2016-08-03"
}
```


## <a name="resource-trends-home">Trends: Home</a>

Stability: `prototype`

The company's graphical report for the month

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **[last_month](#resource-trends)** | *date-time* | the previous month | `"2016-07-03T21:32:44Z"` |
| **[section](#resource-trends)** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **stats** | *array* | list of statistical data | `[{"type":"revenue","sum":49167.57,"difference":-48197.03}]` |
| **[two_months_ago](#resource-trends)** | *date-time* | the previous 2 months | `"2016-06-03T21:32:44Z"` |

### Trends: Home Request

Get trends home.

```
GET /api/v2/trends/home
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **section** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **type** | *string* | chart type<br/> **one of:**`"home"` or `"revenue"` or `"spending"` or `"cash"` | `"home"` |


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/trends/home
 -G \
  -d type=home \
  -d section=revenue
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "stats": [
    {
      "type": "revenue",
      "sum": 49167.57,
      "difference": -48197.03
    }
  ],
  "section": "revenue",
  "last_month": "2016-07-03T21:32:44Z",
  "two_months_ago": "2016-06-03T21:32:44Z"
}
```


## <a name="resource-trends-spending">Trends: Spending</a>

Stability: `prototype`

Company spending over a period of time.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **data/amount** | *number* | amount spent per date | `2494.06` |
| **data/date** | *date* | spending date | `"2016-08-01"` |
| **[end_date](#resource-trends)** | *date* | ending day of trend period | `"2016-08-03"` |
| **[has_invoice_entries](#resource-trends)** | *boolean* | if it includes invoices during the trend period | `true` |
| **[last_month](#resource-trends)** | *date-time* | the previous month | `"2016-07-03T21:32:44Z"` |
| **[section](#resource-trends)** | *string* | trends main section<br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **[start_date](#resource-trends)** | *date* | starting day of trend period | `"2016-05-01"` |
| **[subsection](#resource-trends)** | *string* | trends subsection<br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |
| **[two_months_ago](#resource-trends)** | *date-time* | the previous 2 months | `"2016-06-03T21:32:44Z"` |

### Trends: Spending Request

Get spending trend.

```
GET /api/v2/trends/spending
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **end_date** | *date* |  | `"2016-08-03"` |
| **section** | *string* | <br/> **default:** `"spending"`<br/> **one of:**`"revenue"` or `"spending"` | `"revenue"` |
| **start_date** | *date* |  | `"2016-05-01"` |
| **subsection** | *string* | <br/> **default:** `"by_category"`<br/> **one of:**`"overview"` or `"cash_overview"` or `"dept_overview"` or `"by_category"` or `"by_merchant"` | `"overview"` |


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/trends/spending
 -G \
  -d section=revenue \
  -d subsection=overview \
  -d start_date=2016-05-01 \
  -d end_date=2016-08-03
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "data": [
    {
      "date": "2016-08-01",
      "amount": 2494.06
    }
  ],
  "last_month": "2016-07-03T21:32:44Z",
  "two_months_ago": "2016-06-03T21:32:44Z",
  "section": "revenue",
  "subsection": "overview",
  "start_date": "2016-05-01",
  "end_date": "2016-08-03",
  "has_invoice_entries": true
}
```


## <a name="resource-user">User</a>

Stability: `prototype`

A user in the Indinero App.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **authy_id** | *nullable integer* | 2FA Authy ID | `9123814` |
| **authy_opted_out** | *nullable boolean* | Setting signifying the user opted out of the 2FA Feature | `true` |
| **[company:fiscal_year_end](#resource-company)** | *string* | Fiscal year end date. | `"12/31"` |
| **[company:id](#resource-company)** | *integer* | Unique identity of a company | `401230` |
| **[company:name](#resource-company)** | *string* | Name of the company | `"Acme Co"` |
| **display_name** | *string* | Display name of the user | `"John Done"` |
| **email** | *string* | Email address of the user | `"john@done.com"` |
| **id** | *number* | Unique identifier of a user | `123` |
| **permissions** | *array* | List of features the user has permissions to. If the user is an admin, it is assumed that the user has access to all features, and checking this is unnecessary. | `["Finance","Transactions","Taxes"]` |
| **role** | *string* | Role of the user in the company | `"Admin"` |

### User Logged in user information

Get logged in user information

```
GET /api/v2/user
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/user
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 123,
  "display_name": "John Done",
  "email": "john@done.com",
  "company": {
    "id": 401230,
    "name": "Acme Co",
    "fiscal_year_end": "12/31"
  },
  "authy_id": 9123814,
  "authy_opted_out": true,
  "role": "Admin",
  "permissions": [
    "Finance",
    "Transactions",
    "Taxes"
  ]
}
```

### User User Profile Photo

Get logged in user profile photo

```
GET /api/v2/user/profile_photo
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/user/profile_photo
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 123,
  "display_name": "John Done",
  "email": "john@done.com",
  "company": {
    "id": 401230,
    "name": "Acme Co",
    "fiscal_year_end": "12/31"
  },
  "authy_id": 9123814,
  "authy_opted_out": true,
  "role": "Admin",
  "permissions": [
    "Finance",
    "Transactions",
    "Taxes"
  ]
}
```

### User User Forgot Password

Reset user's password

```
POST /api/v2/user/forget_password
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **email** | *string* | Email address of the user | `"john@done.com"` |



#### Curl Example

```bash
$ curl -n -X POST https://api.indinero.com/api/v2/user/forget_password \
  -d '{
  "email": "john@done.com"
}' \
  -H "Content-Type: application/json"
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 123,
  "display_name": "John Done",
  "email": "john@done.com",
  "company": {
    "id": 401230,
    "name": "Acme Co",
    "fiscal_year_end": "12/31"
  },
  "authy_id": 9123814,
  "authy_opted_out": true,
  "role": "Admin",
  "permissions": [
    "Finance",
    "Transactions",
    "Taxes"
  ]
}
```

