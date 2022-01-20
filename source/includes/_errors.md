# Errors

Error code is a numeric or alphanumeric code that helps you to determine the nature of an error and why it occurred. The CirclePay API uses the following error codes:

## General

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
1110   | Data missing | {ATTRIBUTE} is missing.
1111   | Invalid request structure | The object structure sent is invalid. If you follow the documentation and still facing the same issue, please contact the support team.
1112   | Invalid request data | The {ATTRIBUTE} has invalid value.
1114   | Field length error | The field {ATTRIBUTE} length must be less than {ATTRIBUTE} and more than {ATTRIBUTE}.
1116   | Invalid email | The email format is invalid.

## Authentication

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
2110   | Merchant key is incorrect | The merchant key might be incorrect or doesnot exist.
2111   | Invalid verification code | The provided verification code is incorrect.
2112   | Password is invalid | The provided password isn't following the password requirements.
2113   | Password isnot matching | The password entered is not matching the first password field.

## Customers

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
3110   | Cannot find the customer | The customer phone number might be incorrect or doesnot exist.
3111   | Customer already exist | Another customer exists with the same phone number.

## Payment Links

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
4101   | Cannot create Payment link | Cannot create a payment link for an unknown reason. Please contact CirclePay support team.
4111   | Cannot find the payment link | The Payment link URL might be incorrect or doesn't exist.
4112   | Expire date cannot be in the past | Cannot add a past date for a payment link {ATTRIBUTE}.
4115   | Payment link is expired | Cannot pay an expired payment link.
4211   | Cannot find form | The form id might be incorrect or doesnot exist.
4212   | Cannot update the form | Cannot update the form as it might include responses.
4311   | Cannot find coupon | The coupon code might be incorrect or doesnot exist.
4312   | Cannot update the coupon | Cannot update the coupon as it might be linked to payments.
4313   | Cannot delete the coupon | Cannot delete the coupon as it might be linked to payments.

## Invoice

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
5101   | Cannot create an invoice | Cannot create an invoice for an unknown reason. Please contact CirlepPay support team.
5111   | Cannot find the invoice | The invoice number might be incorrect or doesn't exist.
5112   | Cannot create the invoice | Cannot add a past date for an invoice {ATTRIBUTE}.
5113   | Cannot delete the invoice | Cannot delete the invoice as it might be linked to other fields.
5114   | Customer phone number is incorrect | Cannot change the customer phone attached to the invoice.


## Invoice

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
7110   | Cannot enable the payment gateway | Cannot enable the payment gate for an unknow reason. Please contact CirclePay support team.
7111   | Cannot find the payment gateway | The payment gateway ID might be incorrect or doesn't exist.
7112   | Cannot enable the payment method | Cannot enable the payment method for an unknow reason. Please contact CirclePay support team.
7113   | Cannot find the payment method | The payment method ID might be incorrect or doesnot exist.
7114   | Cannot set the payment method fee | Cannot set the payment method fee. Please contact the support team.


## Merchant

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
8110   | Cannot create a merchant | The merchant phone number is being used by another account.
8111   | Cannot find the merchant | The merchant key might be incorrect or doesnot exist.
8112   | Config file has incorrect structure | The config JSON file structure is incorrect.
8116   | Cannot update the merchant phone number | Cannot update the merchant phone number as it's being used by another account.


## Transactions

Error&nbsp;Code | Error Text | Error Message
--------- | ----------|------------
9110   | Transaction data request is missing | The transaction data request is missing {ATTRIBUTE}.
9111   | Cannot find the transaction | The transaction ID might be incorrect or doesn't exist.
9112   | Refund request rejected | The payment gateway rejected the refund request for the following reason {ATTRIBUTE}.









