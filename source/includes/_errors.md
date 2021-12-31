# Errors

The CirclePay API uses the following error codes:

Error&nbsp;Code   | Meaning
--------- | ----------
400   | Bad Request -- Your request is invalid.
401   | Unauthorized -- Your API key is wrong.
403   | Forbidden -- The payment gateway or method requested is hidden for administrators only.
404   | Not Found -- The specified gateway or payment method could not be found.
405   | Method Not Allowed -- You tried to access a gateway or payment method with an invalid method.
406   | Not Acceptable -- You requested a format that isn't json.
410   | Gone -- The gateway or payment method requested has been removed from our servers.
429   | Too Many Requests -- You're requesting too many gateway or payment methods! Slow down!
500   | Internal Server Error -- We had a problem with our server. Try again later.
503   | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
