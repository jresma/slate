# Errors

The inDinero API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The account requested is hidden for administrators only
404 | Not Found -- The specified account could not be found
405 | Method Not Allowed -- You tried to access an account with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The account requested has been removed from our servers
418 | I'm a teapot
429 | Too Many Requests -- You are requesting too many calls! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We are temporarialy offline for maintanance. Please try again later.