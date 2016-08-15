# Errors

The inDinero API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The account requested is hidden for administrators only
404 | Not Found -- The specified account could not be found
405 | Method Not Allowed -- You tried to access an account with an invalid method
406 | Not Acceptable -- You requested a format that isn't JSON.
410 | Gone -- The account requested has been removed from our servers
418 | I'm a teapot
429 | Too Many Requests -- You are requesting too many calls! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We are temporarily offline for maintenance. Please try again later.

# JSON Error Format

In cases where appropriate, the API could return structured error messages. The
structure of the JSON response should contain the following fields:

Error Key | Meaning
--------- | -------
type | The primary type of the error (application_error, permission_error, etc.)
subtype | The subcategory of the error (invalid_credentials, invalid_input_data, unknown_error, etc.)
details | Human readable error message
additional_data | An array of key-value pairs about the errors

## Error Types

### Application Errors

#### Invalid Input Data

The `additional_data` field contains an array of objects with the erroneous data.

```javascript
{
  type: 'application_error',
  subtype: 'invalid_input_data',
  details: 'Input data is missing or invalid.',
  additional_data: [
    {
      reimbursement_ids: null,
      errors: 'reimbursement_ids is required'
    }
  ]
}
```

#### Unknown Error

A generic error subtype returned when an unexpected error occurs. The API will
send a notification to the API support team containing necessary information
to fix the issue.

### Permission Error

#### Invalid Credentials

The access token used in the request is either expired or has been revoked.
