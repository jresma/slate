## <a name="resource-category">Category</a>

Stability: `prototype`

A chart of accounts is a listing of the names of the accounts that a company has identified and made available for recording trransactions in its general ledger. A company has the flexibility to tailor its chart of accounts to best suit its needs, including adding accounts as needed.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **built_in** | *boolean* | boolean | `true` |
| **id** | *integer* | unique identifier of category | `654321` |
| **mastercategory** | *integer* | master category | `654321` |
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


## <a name="resource-transaction">Transaction</a>

Stability: `prototype`

An accounting transaction is a business event having a monetary impact on the financial statements of a business. It is recorded in the accounting records of the business.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **account_id** | *integer* |  | `42` |
| **amount** | *float* |  |  |
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
| **real_amount** | *float* |  |  |
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
    "amount": null,
    "real_amount": null,
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


