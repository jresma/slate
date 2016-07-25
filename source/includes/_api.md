## <a name="resource-bank_account">Bank Account</a>

Stability: `prototype`

Bank account items added to user's company.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **account_name** | *string* | Bank Account name | `"Bank of Asia"` |
| **account_number_string** | *nullable string* | account number string | `null` |
| **balance** | *number* | bank account balance | `5000.0` |
| **checking_account_number** | *nullable string* | checking account number | `null` |
| **coa_number** | *nullable string* | chart of account number | `null` |
| **company_id** | *integer* | Company ID | `301` |
| **created_at** | *nullable date-time* | when the item was created | `null` |
| **currency_code** | *nullable string* | currency code | `"USD"` |
| **discontinued** | *boolean* | discontinued | `false` |
| **id** | *integer* | unique identifier of bank account | `100` |
| **indinero_status** | *nullable integer* | inDinero status | `3` |
| **intuit_id** | *nullable integer* | intuit id | `null` |
| **item_id** | *nullable integer* | item id | `200` |
| **stock_account** | *nullable boolean* |  | `null` |
| **stripe_account_id** | *nullable string* | stripe account id | `null` |
| **svb_account_number** | *nullable string* | SVB account number | `null` |
| **updated_at** | *nullable date-time* | when the item was last updated | `null` |
| **yodlee_id** | *nullable integer* |  | `null` |

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
    "stock_account": true,
    "yodlee_id": 42,
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
| **built_in** | *boolean* | boolean | `true` |
| **id** | *integer* | unique identifier of category | `654321` |
| **mastercategory** | *nullable integer* | master category | `654321` |
| **name** | *string* | unique name of category | `"Category 1"` |
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
    "name": "Category 1",
    "mastercategory": 654321,
    "built_in": true,
    "transaction_type_name": "both"
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

### Company Logged in user's company details

User's company information

```
GET /api/v2/user/company
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/user/company
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

Company Logo

```
GET /api/v2/user/company/logo
```


#### Curl Example

```bash
$ curl -n https://api.indinero.com/api/v2/user/company/logo
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
| **yodlee_id** | *nullable integer* |  | `null` |

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
    "yodlee_id": 42,
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
| **display_error** | *nullable boolean* |  | `null` |
| **id** | *integer* | unique identifier of financial account | `100` |
| **intuit_id** | *nullable integer* | intuit id | `null` |
| **intuit_status_code** | *nullable integer* |  | `null` |
| **last_transaction_date** | *nullable date* |  | `null` |
| **last_update_attempt** | *nullable date-time* | when the item update was last attempted | `null` |
| **last_update_time** | *nullable date-time* | when the item was updated | `null` |
| **linked_item_id** | *nullable integer* |  | `null` |
| **mfa** | *nullable string* |  | `null` |
| **name** | *string* | Financial Account name | `"Bank of Asia"` |
| **poll_status** | *nullable string* |  | `null` |
| **refresh_status_code** | *nullable integer* | refresh status code | `1` |
| **routing_number** | *nullable integer* |  | `null` |
| **send_banklog_email** | *nullable boolean* |  | `null` |
| **service_id** | *integer* | service id | `100` |
| **start_poll_time** | *nullable date-time* |  | `null` |
| **status** | *nullable integer* |  | `null` |
| **updated_at** | *nullable date-time* | when the item was last updated | `null` |
| **yodlee_id** | *nullable integer* |  | `null` |

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
    "yodlee_id": 42,
    "mfa": "example",
    "start_poll_time": "2015-01-01T12:00:00Z",
    "poll_status": "example",
    "linked_item_id": 42,
    "intuit_status_code": 42,
    "routing_number": 42,
    "display_error": true,
    "send_banklog_email": true,
    "status": 42,
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
| **amount** | *number* | receipt amount | `1234.0` |
| **company_id** | *integer* | Company ID | `100` |
| **description** | *string* | receipt description | `"this is a receipt description"` |
| **email** | *nullable string* | receipt email | `"this is a receipt email"` |
| **email_date** | *nullable date-time* | receipt email date | `null` |
| **email_id** | *nullable integer* | receipt email_id | `42` |
| **id** | *integer* | unique identifier of receipt | `1001` |
| **merchant** | *nullable string* | receipt merchant | `"this is a receipt merchant"` |
| **processor** | *nullable string* | receipt processor | `"this is a receipt processor"` |
| **resend_date** | *nullable date-time* | receipt resend date | `null` |
| **status** | *nullable integer* | receipt status | `1` |
| **subject** | *string* | receipt subject | `"this is a receipt subject"` |

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
  "company_id": 100,
  "amount": 1234.0,
  "subject": "this is a receipt subject",
  "description": "this is a receipt description",
  "status": 1,
  "processor": "this is a receipt processor",
  "merchant": "this is a receipt merchant",
  "email": "this is a receipt email",
  "email_id": 42,
  "email_date": "2015-01-01T12:00:00Z",
  "resend_date": "2015-01-01T12:00:00Z"
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
    "company_id": 100,
    "amount": 1234.0,
    "subject": "this is a receipt subject",
    "description": "this is a receipt description",
    "status": 1,
    "processor": "this is a receipt processor",
    "merchant": "this is a receipt merchant",
    "email": "this is a receipt email",
    "email_id": 42,
    "email_date": "2015-01-01T12:00:00Z",
    "resend_date": "2015-01-01T12:00:00Z"
  }
]
```


## <a name="resource-reimbursement">Reimbursement</a>

Stability: `prototype`

Reimbursement

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **cannot_process_reason** | *nullable string* | Reason why the reimbursement was not processed | `"ACH payment failed"` |
| **category:account_number** | *string* | A category's account number | `"4123"` |
| **category:id** | *string* | A category's identifier | `1234` |
| **category:name** | *string* | A category's name | `"Uncategorized"` |
| **company:id** | *integer* | A company's identifier | `42` |
| **created_at** | *nullable date-time* | Time when the reimbursement was created | `null` |
| **description** | *string* | Description of the reimbursement submitted. | `"Github Processing Fee."` |
| **employee** | *nullable object* | Employee who submitted the reimbursement request | `null` |
| **employee:email** | *nullable string* | Employee's email address | `"harrison.redford@example.com"` |
| **employee:full_name** | *nullable string* | Employee's full name | `"Harrison Redford"` |
| **id** | *integer* | Unique identifier of the reimbursement. | `123` |
| **person:full_name** | *nullable string* | Full name of the person | `"John Done"` |
| **receipt** | *nullable object* | Receipt associated with the reimbursement | `null` |
| **receipt:id** | *integer* | Receipt's unique identifier. | `1234` |
| **status** | *integer* | A reimubursements status: Draft: -1, Pending: 0, For processing: 1, Rejected: 2, Processing: 3, Reimbursed: 4, Archived: 5, Cannot Process: 5 | `3` |
| **value** | *number* | Amount to reimburse. | `9.99` |

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
{
  "id": 123,
  "company": {
    "id": 42
  },
  "status": 3,
  "value": 9.99,
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
    "id": 1234,
    "name": "Uncategorized",
    "account_number": "4123"
  },
  "receipt": {
    "id": 1234
  }
}
```

### Reimbursement Approve reimbursements

Approve reimbursements

```
POST /api/v2/reimbursements/approve
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **reimbursement_ids** | *array* | List of reimbursement ids. | `[5]` |


#### Curl Example

```bash
$ curl -n -X POST https://api.indinero.com/api/v2/reimbursements/approve \
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
    "company": {
      "id": 42
    },
    "status": 3,
    "value": 9.99,
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
      "id": 1234,
      "name": "Uncategorized",
      "account_number": "4123"
    },
    "receipt": {
      "id": 1234
    }
  }
]
```

### Reimbursement Deny reimbursements

Deny reimbursements

```
POST /api/v2/reimbursements/deny
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **reimbursement_ids** | *array* | List of reimbursement ids. | `[5]` |


#### Curl Example

```bash
$ curl -n -X POST https://api.indinero.com/api/v2/reimbursements/deny \
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
    "company": {
      "id": 42
    },
    "status": 3,
    "value": 9.99,
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
      "id": 1234,
      "name": "Uncategorized",
      "account_number": "4123"
    },
    "receipt": {
      "id": 1234
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
| **account_id** | *integer* |  | `42` |
| **amount** | *number* |  | `42.0` |
| **base_type** | *string* |  | `"example"` |
| **category_id** | *integer* |  | `42` |
| **company_id** | *integer* |  | `42` |
| **container_type** | *string* |  | `"example"` |
| **currency_code** | *nullable string* |  | `null` |
| **description_auto** | *string* |  | `"example"` |
| **description_user** | *string* |  | `"example"` |
| **detail** | *string* |  | `"example"` |
| **id** | *integer* |  | `42` |
| **memo** | *nullable string* |  | `null` |
| **post_date** | *string* |  | `"example"` |
| **real_amount** | *number* |  | `42.0` |
| **split_id** | *integer* |  | `42` |

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
    "company_id": 42,
    "amount": 42.0,
    "real_amount": 42.0,
    "account_id": 42,
    "post_date": "example",
    "container_type": "example",
    "description_user": "example",
    "description_auto": "example",
    "detail": "example",
    "memo": null,
    "base_type": "example",
    "currency_code": null,
    "split_id": 42,
    "category_id": 42
  }
]
```


## <a name="resource-user">User</a>

Stability: `prototype`

A user in the Indinero App.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **company_id** | *number* | Identifier of the company a user belongs to | `1234` |
| **display_name** | *string* | Display name of the user | `"John Done"` |
| **email** | *string* | Email address of the user | `"john@done.com"` |
| **id** | *number* | Unique identifier of a user | `123` |

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
  "company_id": 1234
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
  "company_id": 1234
}
```


