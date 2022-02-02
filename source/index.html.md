---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://circlepay.ai/#howtouse'>Sign Up for CirclePay</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the CirclePay API
---

# Introduction

CirclePay is a platform that enables merchants to develop their projects by connecting many electronic payment gateways located in Egypt in one place with the freedom to choose the appropriate payment method.

# Payment Gateway

To process online transactions, you will need both a payment gateway and a payment method. 

<span style="color: red">A payment gateway</span> is the technology that captures and transfers payment data from the customer to the acquirer. 

<span style="color: red">A payment method</span> is a way that customers pay for a product or service. 

<aside class="notice">
Each transaction requires a definition for a payment gateway and a payment method.
</aside>

<img src="https://devathon.com/wp-content/uploads/2020/02/Patement-gateway-process-Devathon.png" >

## List Payment Gateways

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/PaymentGateway/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment gateways list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	[
	 { 
		"id": "610b2c486df621209c85215b",
		"name": "MyFatoorh"
	 },
	 {
		"id": "610b2c486df621209c85215a",
		"name": "Fawry"
	 }  
	]
}
```

Retrieves all payment gateways to the merchant.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
merchant_token |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|contains the security credentials for a login session and identifies the user.

### Returns

Returns payment gateway list.

<aside class="notice">
The error code used when you fail to list payment gateways is <a href="#1110">1110</a>
</aside>

########################################################################

## Retrieve a Payment Gateway

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/PaymentGateway/get/{payment_gateway_ID}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment gateway object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" : 
   {
	 "payment_gateway_ID": "610b2c486df621209c852123",
	 "merchant_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9"
   }
}
```

Retrieves a specific payment gateway.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_gateway_ID |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment gateway object.
merchant_token |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|contains the security credentials for a login session and identifies the user.

### Returns
Return a payment gateway object.

<aside class="notice">
The error codes used when you fail to get specific payment gateway are <a href="#1110">1110</a> , <a href="#7111">7111</a>
</aside>

##############################################################################

# Payment Methods

<span style="color: red">A payment method</span> is a way that customers pay for a product or service. CirclePay gives customers the freedom to choose between payment methods like: cash, credit cards, prepaid cards, debit cards, or mobile payments.


MyFatoorh | Fawry | Paymob | 
--------- | ---------|----------|
Visa|Visa|Visa|
MasterCard|MasterCard|MasterCard
meeza|meeza|Kiosk Payments
Mobile Wallet|E-wallet Payment|Cash Collection
ValU|Reference Number|ValU
SADAD|ValU|Mobile Wallets
mada||SOUHOOLA
ApplePay |   |
Knet|   |
American express|   |     

<aside class="notice">
<span style="color: red">Paymob, Fawry, MyFatoorah</span> are payment gateways. Each of these payment gateways are supporting a number of payment methods. So, a payment method won't be available unless you enable the corresponding payment gateway.
</aside>

## List a Payment Methods

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/PaymentMethod/list/{payment_gateway_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment methods list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	[
	 {
		"id": "610b2c496df621209c852163",
		"name": "Visa",
		"gateway_id": "610b2c486df621209c85215b"
	 },
	 {
		"id": "610b2c496df621209c852168",
		"name": "MasterCard",
		"gateway_id": "610b2c486df621209c85215a"
	 }
	]
}
```

Retrieves all payment methods of the specific gateway.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_gateway_ID |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment gateway object.
merchant_token |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|contains the security credentials for a login session and identifies the user.

### Returns

Returns a payment methods list.

<aside class="notice">
The error codes used when you fail to list payment methods are <a href="#8111">8111</a> , <a href="#7111">7111</a>
</aside>

#################################################################################

## Retrieve a Payment Method

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/PaymentMethod/get/{payment_method_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment method object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "id": "610b2c496df621209c852161",
	 "name": "Visa",
	 "gateway_id": "610b2c486df621209c85215b",
	}
}
```

Retrieves a specific payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_ID |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment method object.
merchant_token |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|contains the security credentials for a login session and identifies the user.

### Returns

Returns a payment method object.

<aside class="notice">
The error codes used when you fail to get a specific payment method are <a href="#8111">8111</a> , <a href="#7113">7113</a>
</aside>

##########################################################################################

# Merchants

<span style="color: red">Merchant</span> is the person or company engaged in the business of selling products or services. For example, wholesaler or retail store owner.

## Create a Merchant

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "first_name"="Ahmed"
     -d "last_name"="Khaled"
     -d "email"="ahmedkahled@gmail.com"
     -d "mobile_number"="+201001414133"
	 -d "Business_Name"="E-commerce"
     -d "Business_Address"="El-maadi"
     'https://circlepay.ai/apis/Merchant/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created a new merchant",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "merchant_id": "1",
	 "merchant_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9"
	}
}
```

This endpoint helps you to create new merchant.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
first_name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's first name. |
last_name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's last name. |
email |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's email. |
mobile_number|String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's phone number. |
Business_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The business name. |
Business_Address |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The business address. |
callback_url |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| A callback URL will be invoked by the API method you're calling after it's done. |

<aside class="notice">
Password will be auto generated.
</aside>

### Returns

Returns the merchant id if the merchant created successfully. Returns an error if create parameters are invalid.

<aside class="notice">
The error codes used when you fail to create a merchant are <a href="#8110">8110</a> , <a href="#1110">1110</a> , <a href="#1112">1112</a>
</aside>

########################################################################################

## Retrieve a Merchant

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully retrieved the merchant",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "first_name": "ahmed",
	 "last_name": "khaled",
	 "email": "ahmed@gmail.com",
	 "mobile_number": "+201001212155",
	 "business_name": "ecommerce",
	 "business_address": "el-maadi",
	 "refund_policy": null,
	 "shipping_policy": null,
	 "status": null,
	}
}
```

Retrieves a specific merchant.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
merchant_token |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|contains the security credentials for a login session and identifies the user.

### Returns

Returns the merchant object for a valid identifier.

#################################################################################

## Update a Merchant

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d "first_name"="ahmed"
	 -d "last_name"="khaled"
	 -d "email"="ahmed@gmail.com"
	 -d "mobile_number"="+201001215155"
	 -d "business_name"="ecommerce"
	 -d "business_address"="el-maadi"
     'https://circlepay.ai/apis/Merchant/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "first_name": "ahmed",
	 "last_name": "khaled",
	 "email": "ahmed@gmail.com",
	 "mobile_number": "+201001212155",
	 "business_name": "ecommerce",
	 "business_address": "el-maadi",
	 "refund_policy": null,
	 "shipping_policy": null,
	 "status": null,
	}
}
```

Updates the specified merchant by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
first_name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's first name. |
last_name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's last name. |
email |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's email. |
mobile_number|String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's phone number. |
Business_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The business name. |
Business_Address |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The business address. |

### Returns

Returns the merchant object if the update succeeded. Returns an error if update parameters are invalid.

<aside class="notice">
The error codes used when you fail to update a merchant are <a href="#8116">8116</a> , <a href="#1110">1110</a> , <a href="#1112">1112</a>
</aside>

####################################################################################

## Update Document

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d document_id="124234"
     'https://circlepay.ai/apis/Merchant/updateDocument'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant's document",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
     {}
}
```

Updates the specified merchant's doucment by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
File |Object|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's document file. |
document_id |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| Unique identifer of document. |
document_type |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| Document's type (from predefined list). |


### Returns

Returns the merchant's document object if the update succeeded. Returns an error if update parameters are invalid.

<aside class="notice">
The error codes used when you fail to update the merchant's document are <a href="#1110">1110</a> , <a href="#1112">1112</a>
</aside>


#################################################################################

## Update merchant status

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d status="SUSPENDED"
     'https://circlepay.ai/apis/Merchant/updateStatus'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant's status",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
     {}
}
```

Updates the specified merchant's status.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
status |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The merchant's status (ACTIVATED - DEACTIVATED - SUSPENDED)). |

### Returns

Returns the status property(in merchant's object) if the update succeeded. Returns an error if update parameters are invalid.

#################################################################################

## List all merchants

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Merchants list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
   [
	{
	 "first_name": "ahmed",
	 "last_name": "khaled",
	 "email": "ahmed@gmail.com",
	 "mobile_number": "+201001212155",
	 "business_name": "ecommerce",
	 "business_address": "el-maadi",
	 "refund_policy": null,
	 "shipping_policy": null,
	 "status": null,
	},
	{
	 "first_name": "ibrahim",
	 "last_name": "salah",
	 "email": "ibrahim@gmail.com",
	 "mobile_number": "+201001812155",
	 "business_name": "nike",
	 "business_address": "el-maadi",
	 "refund_policy": null,
	 "shipping_policy": null,
	 "status": null,
	}
   ]
}
```

Retrieves all merchants.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
merchant_token |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|contains the security credentials for a login session and identifies the user.

### Returns

Returns an array. Each entry in the array is a separate user object.This request should never return an error.

########################################################################################

## List all documents

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/listDocuments
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Documents list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	[
	 {
	  "document_id": "124234",
	  "file_size": 7969,
	  "upload_date": 22-3-2022,
	  "last_modified": 23-3-2022,
	  "document_type": "national id"
	 },
	 {
	  "document_id": "13534234",
	  "file_size": 7990,
	  "upload_date": 22-2-2022,
	  "last_modified": 23-3-2022,
	  "document_type": "passport"
	 }
	]
}
```

Retrieves all merchants' documents.

### Parameters

No parameters.

### Returns

Returns a document list.

####################################################################################

## Get file

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/getFile/{document_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Document file returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	 {
      "document_Id":"3264",
      "file_stream":"e:\\b.txt",
      "file_ext": ".txt"
	 }
}
```

Retrieves file document.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
document_id |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the document object.

### Returns

Returns the file document object.

####################################################################################

## Set Billing info

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d Bank_Name="cairo bank"
	 -d Bank_Account_Num="242424242424"
     'https://circlepay.ai/apis/Merchant/setBillingInfo'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the billing info",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
     {}
}
```

Updates the billing info by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
Bank_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| Bank's name. |
Bank_Account_Num |Numeric|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The bank account number. |
Bank_Branch_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The bank branch name. |
SWIFT |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| Society for Worldwide Interbank Financial Telecommunications, the SWIFT code can be found on a bank's website, on your bank statement, or through an online search. |
IBAN |Numeric|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| international bank account number, is a standard international numbering system developed to identify an overseas bank account. The number starts with a two-digit country code, then two numbers, followed by several more alphanumeric characters. |

### Returns

Returns the billing info object if the update succeeded. Returns an error if update parameters are invalid.

<aside class="notice">
The error code used when you fail to set the billing info is <a href="#1110">1110</a>
</aside>


#################################################################################

## Configure payment gateway

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d payment_gateway_id="610b2c486df621209c85215b"
     'https://circlepay.ai/apis/Merchant/configurePaymentGateway'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully configured payment gateway",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
     {
	  "payment_gateway_id": "610b2c486df621209c85215b",
     }
}
```

Set the payment gateway keys for a specific merchant to allow CirclePay connect to the merchant account on the Payment Gateway

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_gateway_id |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| Unique identifier of payment gateway. |
Gateway_Config_Object |Object|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The gateway config object. |


### Returns

Returns the payment gateway id.

<aside class="notice">
The error codes used when you fail to configure payment gateway are <a href="#7111">7111</a>, <a href="#8112">8112</a>
</aside>


#################################################################################

## Enable gateway

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/enable/{payment_gateway_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully enabled gateway",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
      "payment_gateway_ID": "610b2c486df621209c85215b"
	}
}
```

This endpoint enable specific payment gateway.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payemnt_gateway_id |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Unique identifier for the payment gateway object. |

### Returns

Returns id of enabled payment gateway.

<aside class="notice">
The error codes used when you fail to enable gateway are <a href="#7110">7110</a> , <a href="#7111">7111</a>
</aside>

####################################################################################

## Disable gateway

```shell
curl -X DELETE --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/disable/{payment_gateway_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully disabled gateway",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	  "payment_gateway_ID":"610b2c486df621209c85215b"
	}
```

This endpoint disable specific gateway and it's related payment methods.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_gateway_ID |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment gateway object.

### Returns

Returns the id of disabled payment gateway.

####################################################################################

## Set payment method fee

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_method_id="610b2c496df621209c852168"
     'https://circlepay.ai/apis/Merchant/setPaymentMethodFee'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully set payment method fee",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	  "payment_method_ID": "610b2c496df621209c852168"
	}
}
```

This endpoint Set the fees for each payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_id |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Unique identifier for the payment method object. |
Fee_Fixed |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The fixed fee. |
Fee_Percent |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The percentage fee. |
Refund_Fee_Fixed |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The Refund fixed fee. |
Refund_Fee_Percent |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The Refund fee percentage. |

### Returns

Returns the payment method id.

<aside class="notice">
The error codes used when you fail to set payment method fee are <a href="#7111">7111</a> , <a href="#7113">7113</a> , <a href="#1110">1110</a> , <a href="#7116">7116</a>
</aside>

#######################################################################################

## Enable payment method

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/enablePaymentMethod/{payment_method_ID}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully enabled the payment method",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	  "payment_method_ID": "610b2c496df621209c852168"
	}
}
```

This endpoint enable specific payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_ID |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment method object.

### Returns

Returns id of enabled payment method.

<aside class="notice">
The error codes used when you fail to enable payment method are <a href="#7112">7112</a> , <a href="#7113">7113</a> , <a href="#1110">1110</a>
</aside>

#######################################################################################

## Disable payment method

```shell
curl -X DELETE --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/disablePaymentMethod/{payment_method_ID}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully disabled the payment method",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	  "payment_method_ID": "610b2c496df621209c852168"
	}
}
```

This endpoint disable specific payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_ID |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment method object.

### Returns

Returns id of the disabled payment method.

<aside class="notice">
The error code used when you fail to disable payment method is <a href="#7113">7113</a>
</aside>

#######################################################################################

## List payment methods

```shell
curl -X GET --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/listPaymentMethods'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Merchant's payment methods list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	  [ 
		{
		  "id": "610b2c496df621209c852168",
		  "name": "Visa",
		  "gateway_id": "1",
		  "status": true,
		  "rate": "3" 
		},
		{
		  "id": "610b2c496df621209c8521we",
		  "name": "MasterCard",
		  "gateway_id": "1",
		  "status": true,
		  "rate": "4" 
		}
	  ]
}
```

This endpoint list allowed payment methods to the merchant.

### Parameters

No parameters.

### Returns

Returns a payment methods list of the merchant.

####################################################################################

# Customers

## Create a Customer

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "First_Name"="Ahmed"
     -d "Last_Name"="Khaled"
     -d "email"="ahmedkahled@gmail.com"
     -d "mobile_number"="+201001616166"
	 -d "country"="Egypt"
     -d "city"="cairo"
     'https://circlepay.ai/apis/Customer/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created a new customer",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{  
	 "customer_mobile_number": "+201001616166"
	}
}
```

This endpoint helps you to create new customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
First_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's first name. |
Last_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's last name. |
email |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's email. |
mobile_number|String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's phone number. |
country |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's country. |
governorate |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's governorate. |
city |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's city. |
address |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's address. |
apt_num |Numeric|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's apartment number. |

### Returns

Returns the customer mobile number if the customer's creation succeeded. Returns an error if parameters are invalid.

<aside class="notice">
The error codes used when you fail to create a customer are <a href="#3111">3111</a> , <a href="#1110">1110</a>
</aside>

########################################################################################

## Update a Customer

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "First_Name"="Ahmed"
     -d "Last_Name"="Khaled"
     -d "email"="ahmedkahled@gmail.com"
     -d "mobile_number"="+201001717177"
	 -d "country"="Egypt"
     -d "city"="cairo"
     'https://circlepay.ai/apis/Customer/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the cutomer",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{  
	 "customer_mobile_number": "+201001717177"
	}
}
```

This endpoint helps you to update customer details.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
First_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's first name. |
Last_Name |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's last name. |
email |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's email. |
mobile_number|String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's phone number. |
country |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's country. |
governorate |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's governorate. |
city |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's city. |
address |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's address. |
apt_num |Numeric|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The customer's apartment number. |

### Returns

Returns the customer mobile number if the customer's update succeeded. Returns an error if parameters are invalid.

<aside class="notice">
The error codes used when you fail to update a customer are <a href="#3110">3110</a> , <a href="#1110">1110</a>
</aside>

########################################################################################

## Retrieve a customer

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Customers/get/{customer_mobile_number}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Customer object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{  
	   "first_name": "Ibrahim",
	   "last_name": "Salah",
	   "email": "ibrahim@gmail.com",
	   "mobile_number": "+201001212144",
	   "country": "Egypt",
	   "governorate": "cairo",
	   "city": "nasr",
	   "address": "72 gamal st",
	   "apt_num": "5"
	}
}
```

Retrieves a specific customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
customer_mobile_number |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Customer's mobile number.

### Returns

Returns the Customer object for a valid mobile number.

<aside class="notice">
The error code used when you fail to retrieve a specific customer is <a href="#3110">3110</a>
</aside>

####################################################################################

## List all customers

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Customers/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Customers list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
   [
	{  
	   "first_name": "Ibrahim",
	   "last_name": "Salah",
	   "email": "ibrahim@gmail.com",
	   "mobile_number": "+201001212144",
	   "country": "Egypt",
	   "governorate": "cairo",
	   "city": "nasr",
	   "address": "72 gamal st",
	   "apt_num": "5"
	},
	{  
	   "first_name": "Ahmed",
	   "last_name": "Osman",
	   "email": "ahmedosman@gmail.com",
	   "mobile_number": "+201005212144",
	   "country": "Egypt",
	   "governorate": "cairo",
	   "city": "nasr",
	   "address": "72 gamal st",
	   "apt_num": "5"
	}
   ]
}
```

Retrieves a list of your customers.

### Parameters

No parameters.

<aside class="notice">
List all customers using filters.
</aside>

### Returns

Returns customer list, If no more customers are available, the resulting array will be empty. This request should never return an error.

################################################################################

# Payment Link

## Create a payment link

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "value": 0
     -d "currency": "EGP"
     -d "description": "for grocery delivery"
     -d "expire_date": 22-02-2022
     'https://circlepay.ai/apis/Payment_Link/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created the payment link",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "payment_link_url": "https://bit.ly/3KXl3iA"
	}
}
```

This endpoint helps you to create payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
value |Float|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The value of payment. |
currency |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Currency type used in payment. |
enable_Survey |Boolean|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Switch that helps you to enable or disable survey. |
expire_date |Datetime|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Expire date of the payment link. |
description |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Description of transaction. |
shippingPolicyFlag |Boolean|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The shipping policy flag. |
status |Boolean| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The status of the payment link, to know if the payment link is still valid. |
refundPolicyFlag |Boolean| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The refund policy flag. |
shippingPolicyDetails |String| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The shipping policy Details for example, original sales receipt must accompany returns. |
refundPolicyDetails |String| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The refund policy details for example, refunds and exchanges, Right to cancel your order. |
comments |String| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Comments help merchant and customer to know more about order details and order process. |
name |String| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The name of the customer. |
getCustAddress |Boolean| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The customer's address. |
merchantId |String| <span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Unique identifier for the merchant object. |

### Returns

Returns the payment link url.

<aside class="notice">
The error codes used when you fail to create payment link are <a href="#4101">4101</a> , <a href="#1110">1110</a> , <a href="#4112">4112</a> 
</aside>

####################################################################################

## Retrieves a payment link

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Payment_Link/get/{payment_link_url}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment link object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "link": "https://bit.ly/3KXl3iA",
	 "value": 99.0,
	 "enable_survey": 0,
	 "last_used": 22-02-2022,
	 "editable": 1,
	 "form_id": "31",
	 "description": "for grocery delivery",
	 "currency": "EGP",
	 "expire_date": 22-02-2023,
	 "create_date": 22-01-2022,
	 "status": 1,
	 "totalRevenue": 12,
	 "totalRefund": 1,
	 "totalTransactions": 2,
	 "shippingPolicyFlag": 0,
	 "refundPolicyFlag": 0,
	 "shippingPolicyDetails": "",
	 "refundPolicyDetails": "",
	 "comments": "",
	 "name": "grocery",
	 "getCustAddress": 0
	}
}
```

Retrieves a specific payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|Payment link url.

### Returns

Returns the payment link object.

####################################################################################

## Update a payment link

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "payment_link_url"="https://bit.ly/3KXl3iA"
     'https://circlepay.ai/apis/Payment_Link/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the payment link",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "payment_link_url": "https://bit.ly/3KXl3iA"
	}
}
```
This endpoint helps you to udpate payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
link |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The payment link. |
value |Float|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The value of the payment. |
enable_survey |Boolean|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| to enable survey with payment link.|
last_used |Datetime|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The date of last payment link use. |
editable |Boolean|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| choose if you want to edit or not to edit payment link in the future. |
form_id |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Unique identifier of the form. |
description |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The description of the payment in general. |
currency |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The currency used in payment. |
expire_date |Datetime|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| expire date of the payment link. |
create_date |Datetime|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| creation date of the payment link. |
status |Boolean|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The status of payment link (Active or Not active). |
totalRefund |Float|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| total refund if exists. |
totalTransactions |Numeric|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Total transaction happened. |
shippingPolicyFlag |Boolean|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The shipping policy flag. |
refundPolicyFlag |Boolean|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The refund policy flag. |
shippingPolicyDetails |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The shipping policy Details for example, original sales receipt must accompany returns. |
refundPolicyDetails |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The refund policy details for example, refunds and exchanges, Right to cancel your order. |
comments |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| Comments help merchant and customer to know more about order details and order process. |
name |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Name of the order. |
getCustAddress |Boolean|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| Choose if you want to get customer address or not. |


### Returns

Returns the payment link object.

<aside class="notice">
The error codes used when you fail to update payment link are <a href="#4111">4111</a> , <a href="#1110">1110</a> , <a href="#4112">4112</a> 
</aside>

#################################################################################

## Deactive payment link

```shell
curl -X DELETE --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Payment_Link/list/{payment_link_url}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully deactived payment link",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{}
}
```

Deactivate an active payment link. 

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|payment link url.

### Returns

Deactivate an active payment link. If invalid payment link is provided an error page "Payment Link isn't available" will show.

<aside class="notice">
The error code used when you fail to deactive payment link is <a href="#4111">4111</a>
</aside>


####################################################################################

## List all payment links

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Payment_Link/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment links list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
   [
	{
	 "link": "https://bit.ly/3KXl3iA",
	 "value": 99.0,
	 "enable_survey": 0,
	 "last_used": 22-02-2022,
	 "editable": 1,
	 "form_id": "31",
	 "description": "for grocery delivery",
	 "currency": "EGP",
	 "expire_date": 22-02-2023,
	 "create_date": 22-01-2022,
	 "status": 1,
	 "totalRevenue": 12,
	 "totalRefund": 1,
	 "totalTransactions": 2,
	 "shippingPolicyFlag": 0,
	 "refundPolicyFlag": 0,
	 "shippingPolicyDetails": "",
	 "refundPolicyDetails": "",
	 "comments": "",
	 "name": "grocery",
	 "getCustAddress": 0
	}
   ]
}
```

Retrieves all payment links.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
customer_mobile |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|Customer's mobile number.
Filter |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|Payment links list returned based on this filter object.


### Returns

Returns payment link list which is array contains payment link objects. If no payment links are available, the resulting array will be empty.

<aside class="notice">
The error codes used when you fail to list all payment links are <a href="#3110">3110</a> , <a href="#1110">1110</a>
</aside>


####################################################################################

## Pay payment link

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "payment_link_url"="https://bit.ly/3KXl3iA"
     'https://circlepay.ai/apis/PayPaymentLink/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment links list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{}
}
```

Execute a payment for a specific payment link or an invoice.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The payment link url. |
Customer Object |Object|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The customer object. |
Form_Response Object |Object|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The form response object. |
payment_method_name |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The payment method name. |
payment_gateway_name |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The payment gateway name. |
coupon_code |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The coupon code. |

### Returns

If a payment method is defined, the return the payment intent for the payment method ,if the payment method isn't defined, then return to the checkout page.

<aside class="notice">
- payment method and payment gateway must be together, can't send only one
- response is iframe based on the step to render
- payment_link_url step based on the passed parameters
</aside>

<aside class="notice">
The error codes used when you fail to pay or execute payment link are <a href="#4111">4111</a> , <a href="#4210">4210</a> , <a href="#7112">7112</a> , <a href="#7111">7111</a> , <a href="#4311">4311</a> , <a href="#1110">1110</a>
</aside>

####################################################################################

# Payment

## Get a payment 

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Payment/get/{transactionId}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "id": 1,
	 "transaction_id": 6,
	 "external_ref_id": 3,
	 "init_date": 22-02-2022,
	 "update_date": 23-02-2022,
	 "customer_mobile": "+201001212888",
	 "status": "pending",
	 "payment_link_url": "https://bit.ly/3KXl3iA",
	 "invoice_num": "CIR_INV_1643670030261",
	 "coupon_code": "HEMACOUPON",
	 "value": 99.0,
	 "net_fees": 1.0,
	 "currency": "EGP",
	 "payment_method_id": "1",
	 "payment_method_name": "Visa",
	 "payment_gateway_name": "MyFatoorh"
	}
}
```

Retrieves the details of an existing payment.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
transaction_id |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the payment object.

### Returns

Returns a payment object if a valid identifier was provided, and returns an error otherwise.

<aside class="notice">
The error code used when you fail to get payment object is <a href="#9111">9111</a>
</aside>

######################################################################################

## List all payments

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "coupon_code": "HEMACOUPON"
     'https://circlepay.ai/apis/Payment/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payments list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	[
	  {
		"id": 1,
		"transaction_id": 6,
		"external_ref_id": 3,
		"init_date": 22-02-2022,
		"update_date": 23-02-2022,
		"customer_mobile": "+201001212888",
		"status": "pending",
		"payment_link_url": "https://bit.ly/3KXl3iA",
		"invoice_num": "CIR_INV_1643670030261",
		"coupon_code": "HEMACOUPON",
		"value": 99.0,
		"net_fees": 1.0,
		"currency": "EGP",
		"payment_method_id": "610b2c496df621209c852168",
		"payment_method_name": "Visa",
		"payment_gateway_name": "MyFatoorh"
	  },
	  {
		"id": 2,
		"transaction_id": 5,
		"external_ref_id": 2,
		"init_date": 22-02-2022,
		"update_date": 23-02-2022,
		"customer_mobile": "+201101212888",
		"status": "pending",
		"payment_link_url": "https://bit.ly/3RXl3iA",
		"invoice_num": "CIR_INV_1643670030264",
		"coupon_code": "AHMEDCOUPON",
		"value": 99.0,
		"net_fees": 1.0,
		"currency": "EGP",
		"payment_method_id": "610b2c496df621209c852162",
		"payment_method_name": "MasterCard",
		"payment_gateway_name": "MyFatoorh"
	  }
	]
}
```

Retrieves all payments.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_code |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| The coupon code. |
customer_mobile |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| Customer's mobile number. |
payment_link_url |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| The payment link url. |
invoice_num |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| The invoice number. |
Filter |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|Payments list returned based on this filter object.

### Returns

Returns a payment list which has the details of the payment like: status, amount paid and payment method.

<aside class="notice">
The error codes used when you fail to list payment objects are <a href="#3110">3110</a> , <a href="#4111">4111</a> , <a href="#5111">5111</a> , <a href="#4311">4311</a> , <a href="#1110">1110</a>
</aside>

######################################################################################

# Refund

Allows you to refund a charge that has previously been created but not yet refunded.

## Request a refund

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d currency="EGP"
	 -d value=33.0
     'https://circlepay.ai/apis/Refund/requestRefund'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully requested a refund",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "refund_id": "1"
	}
}
```
This endpoint helps you to request refund.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
transaction_id |Integer|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Unique identifier for the transaction object.|
value |Float|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| Value of the refund.|
currency |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The currency type used. |


### Returns

Returns the refund id. Status in refund object will be in pending state.

<aside class="notice">
Default value of refund is equal to payment value.
</aside>

<aside class="notice">
The error code used when you fail to request refund is <a href="#9112">9112</a>
</aside>

######################################################################################

## List all refunds

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://bit.ly/3KXl3iA"
     'https://circlepay.ai/apis/Refund/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Refunds list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	[
	 {
	    "refund_id": "1",
		"external_ref_id": 2,
		"init_date": 22-02-2022,
		"update_date": 23-02-2022,
		"value": 40.0,
		"transaction_id": 3,
		"refundFees": 2.0,
		"Payment_Method": ["Visa","MasterCard"],
		"customer_mobile": "+201001313454",
		"status": "pending"
	 },
	 {
	    "refund_id": "2",
		"external_ref_id": 3,
		"init_date": 22-02-2022,
		"update_date": 23-02-2022,
		"value": 90.0,
		"transaction_id": 3,
		"refundFees": 4.0,
		"Payment_Method": ["Visa","MasterCard"],
		"customer_mobile": "+201001323454",
		"status": "paid"
	 }
    ]
}
```
List refund objects.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
transaction_id |Integer|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| Unique identifier of transaction object. |
customer_mobile |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| Customer's mobile number. |
payment_link_url |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| The payment link url. |
invoice_num |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -| The invoice number. |
Filter |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|Refunds list returned based on this filter object.

### Returns

Returns refund object list. If no more refunds are available, the resulting array will be empty.

<aside class="notice">
The error codes used when you fail to list refund list are <a href="#9111">9111</a> , <a href="#3110">3110</a> , <a href="#4111">4111</a> , <a href="#5111">5111</a> , <a href="#1110">1110</a>
</aside>

#######################################################################################

## Get refund 

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/refund/getRefund/{refundId}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Refund object returned successfully ",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "refund_id": "2",
	 "external_ref_id": 3,
	 "init_date": 22-02-2022,
	 "update_date": 23-02-2022,
	 "value": 90.0,
	 "transaction_id": 3,
	 "refundFees": 4.0,
	 "Payment_Method": ["Visa","MasterCard"],
	 "customer_mobile": "+201001323454",
	 "status": "paid"
	}
}
```
Retrieves the refund object.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
refund_id |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the refund object.

### Returns

Returns refund object if a valid refund id is provided.

<aside class="notice">
The error code used when you fail to get refund status is <a href="#9111">9111</a>
</aside>

##############################################################################

# Coupon

## Create a coupon

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d value=11.0
     -d name="AHMEDCOUPON"
	 -d expire_date=22-02-2022
     'https://circlepay.ai/apis/Coupon/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created a coupon",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "coupon_code": "HEMACOUPON"
	}
}
```
This endpoint helps you to create coupon.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The payment link url. |
code |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The code of coupon. |
value |Float|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The value of the payment after discounting. |
name |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The name of the coupon. |
expire_date |Datetime|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Coupon's expire date.|
number_of_uses |Numeric|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Number of uses to this coupon. |
discount_value |Float|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Coupon's discount value. |
discount_type |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| number or percentage. |

### Returns

Returns the coupon code. 

<aside class="notice">
Status of coupon is "active" by default.
</aside>

<aside class="notice">
The error codes used when you fail to create new coupon are <a href="#4115">4115</a> , <a href="#4112">4112</a> , <a href="#4111">4111</a> , <a href="#1110">1110</a>
</aside>

##############################################################################

## Retrieve a coupon

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Coupon/get/{couponCode}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully retrieved the coupon",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "code": "HEMACOUPON",
	 "value": 99.0,
	 "name": "50% offer",
	 "create_date": "22-02-2022",
	 "expire_date": "27-02-2022",
	 "number_of_uses": 1,
	 "payment_link_url": "https://bit.ly/3KXl3iA",
	 "status": 1,
	 "used_times": 0,
	 "discount_type": "percent" ,
	 "discount_value": "50.0"
	}
}
```
Retrieves a specific coupon.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_code |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Coupon's code.

### Returns

Returns a coupon if a valid coupon Id was provided. Returns an error otherwise.

<aside class="notice">
The error code used when you fail to get a coupon is <a href="#4311">4311</a>
</aside>

##############################################################################

## Update a coupon

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d coupon_code="HEMACOUPON"
     -d name="50% offer"
     'https://circlepay.ai/apis/Coupon/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the coupon",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "code": "HEMACOUPON",
	 "value": 99.0,
	 "name": "50% offer",
	 "create_date": "22-02-2022",
	 "expire_date": "27-02-2022",
	 "number_of_uses": 1,
	 "payment_link_url": "https://bit.ly/3KXl3iA",
	 "status": 1,
	 "used_times": 0,
	 "discount_type": "percent" ,
	 "discount_value": "50.0"
	}
}
```
Updates the metadata of a coupon.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_code |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The code of coupon.|
value |Float|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The value of the payment after discounting. |
name |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The name of the coupon.|
expire_date |Datetime|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|Coupon's expire date.|
number_of_uses |Numeric|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Number of uses for this coupon. |
status |Boolean|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The status of the coupon for example, expired.|
times_per_customer |Numeric|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Times that customer can use the same coupon. |

### Returns

The newly updated coupon object if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

<aside class="notice">
The error codes used when you fail to update a coupon are <a href="#4312">4312</a> , <a href="#4112">4112</a> , <a href="#4311">4311</a> , <a href="#1110">1110</a>
</aside>

##############################################################################

## Activate coupon

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Coupon/activate/{coupon_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully activated the coupon",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "coupon_id": "1"
	}
}
```
Updates status of the coupon to active.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_id |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|Unique identifier of coupon object.|

### Returns

The activated coupon id if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

<aside class="notice">
The error code used when you fail to active the coupon is <a href="#4311">4311</a>
</aside>

##############################################################################

## Deactive coupon

```shell
curl -X DELETE --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Coupon/deactive/{coupon_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully deactivated the coupon",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "coupon_id": "1"
	}
}
```
Updates status of the coupon to deactive.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_id |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|Unique identifier of coupon object.|

### Returns

The deactivated coupon id if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

<aside class="notice">
The error code used when you fail to deactive the coupon is <a href="#4311">4311</a>
</aside>

##############################################################################

## List all coupons

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Coupon/list/{payment_link_url}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Coupons list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	[
	 {
	  "code": "HEMACOUPON",
	  "value": 99.0,
	  "name": "50% offer",
	  "create_date": "22-02-2022",
	  "expire_date": "27-02-2022",
	  "number_of_uses": 1,
	  "payment_link_url": "https://bit.ly/3KXl3iA",
	  "status": 1,
	  "used_times": 0,
	  "discount_type": "percent" ,
	  "discount_value": "50.0"
	 },
	 {
	  "code": "AHMEDCOUPON",
	  "value": 99.0,
	  "name": "50% offer",
	  "create_date": "24-02-2022",
	  "expire_date": "27-02-2022",
	  "number_of_uses": 1,
	  "payment_link_url": "https://bit.ly/3KOl3iA",
	  "status": 1,
	  "used_times": 0,
	  "discount_type": "percent" ,
	  "discount_value": "50.0"
	 }
	]
}
```
Returns a list of your coupons per payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|payment link url.|

### Returns

Returns list of coupons objects. Each entry in the list is a separate coupon object. If no more coupons are available, the resulting array will be empty. This request should never return an error.

<aside class="notice">
The error code used when you fail to list coupons is <a href="#4111">4111</a>
</aside>

##############################################################################

# Form

## Create a form

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://bit.ly/3KXl3iA"
     -d title="About order"
     'https://circlepay.ai/apis/form/create'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  "data":
  {
    "survey": {
      "title": "new_survey",
      "status": false,
      "questions": [
        {
          "qid": 0,
          "question": "how are you",
          "questionType": "Text",
          "options": [
            {
              "oid": 0,
              "name": "goood"
            }
          ],
          "mandatory": true,
          "answer": [{
            "oid": 0, 
            "name": "greaaat"
          }]
        },
        {
          "qid": 1,
          "question": "whos is this",
          "questionType": "Single Choice",
          "options": [
            {
              "oid": 0,
              "name": "me"
            },
            {
              "oid": 1,
              "name": "you"
            },
            {
              "oid": 2,
              "name": "someone else"
            }
          ],
          "mandatory": true,
          "answer": [{
            "oid": 1,
            "name": ""
          }]
        },
        {
          "qid": 2,
          "question": "list projects",
          "questionType": "Multiple Choice",
          "options": [
            {
              "oid": 0,
              "name": "circlehub"
            },
            {
              "0id": 1,
              "name": "circlepay"
            },
            {
              "oid": 2,
              "name": "all"
            },
            {
              "oid": 3,
              "name": "none"
            }
          ],
          "mandatory": true,
          "answer": [
            {
              "oid": 0,
              "name": ""
            },
            {
              "oid": 1,
              "name": ""
            }
          ]
        }
      ],
      "MemberId": "543"
    }
  }
}
```
This endpoint helps you to create form.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Payment link url. |
title |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The title of the form.|
question_list |Array|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The list that has questions objects. |
status |Boolean|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The status of the form for example, "pending".|

### Returns

Returns form object which has the questions array.

<aside class="notice">
Status is "active" by default.
</aside>

<aside class="notice">
We have three types of questions: Text, Single Choice, Multiple Choice. 
</aside>

<aside class="notice">
The error codes used when you fail to create a form are <a href="#4111">4111</a> , <a href="#4115">4115</a> , <a href="#1110">1110</a>
</aside>

##################################################################################

## Retrieve a form

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/form/get/{payment_link_url}'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  "data":
  {
    "survey": {
      "title": "new_survey",
      "status": false,
      "questions": [
        {
          "qid": 0,
          "question": "how are you",
          "questionType": "Text",
          "options": [
            {
              "oid": 0,
              "name": ""
            }
          ],
          "mandatory": true,
          "answer": [{
            "oid": 0, 
            "name": "greaaat"
          }]
        },
        {
          "qid": 1,
          "question": "whos is this",
          "questionType": "Single Choice",
          "options": [
            {
              "oid": 0,
              "name": "me"
            },
            {
              "oid": 1,
              "name": "you"
            },
            {
              "oid": 2,
              "name": "someone else"
            }
          ],
          "mandatory": true,
          "answer": [{
            "oid": 1,
            "name": ""
          }]
        },
        {
          "qid": 2,
          "question": "list projects",
          "questionType": "Multiple Choice",
          "options": [
            {
              "oid": 0,
              "name": "circlehub"
            },
            {
              "0id": 1,
              "name": "circlepay"
            },
            {
              "oid": 2,
              "name": "all"
            },
            {
              "oid": 3,
              "name": "none"
            }
          ],
          "mandatory": true,
          "answer": [
            {
              "oid": 0,
              "name": ""
            },
            {
              "oid": 1,
              "name": ""
            }
          ]
        }
      ],
      "MemberId": "543"
    }
  }
}
```
Retrieves a form object.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Payment link url.

### Returns

Returns a form object if founded, else an error will be thrown.

<aside class="notice">
At least one attribute to be provided	
</aside>

<aside class="notice">
The error code used when you fail to get a form is <a href="#4111">4111</a>
</aside>

##################################################################################

## Update a form

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://bit.ly/3KXl3iA"
     -d title="About you"
     'https://circlepay.ai/apis/form/update'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  "data":
  {
    "survey": {
      "title": "new_survey",
      "status": false,
      "questions": [
        {
          "qid": 0,
          "question": "how are you",
          "questionType": "Text",
          "options": [
            {
              "oid": 0,
              "name": ""
            }
          ],
          "mandatory": true,
          "answer": [{
            "oid": 0, 
            "name": "greaaat"
          }]
        },
        {
          "qid": 1,
          "question": "whos is this",
          "questionType": "Single Choice",
          "options": [
            {
              "oid": 0,
              "name": "me"
            },
            {
              "oid": 1,
              "name": "you"
            },
            {
              "oid": 2,
              "name": "someone else"
            }
          ],
          "mandatory": true,
          "answer": [{
            "oid": 1,
            "name": ""
          }]
        },
        {
          "qid": 2,
          "question": "list projects",
          "questionType": "Multiple Choice",
          "options": [
            {
              "oid": 0,
              "name": "circlehub"
            },
            {
              "0id": 1,
              "name": "circlepay"
            },
            {
              "oid": 2,
              "name": "all"
            },
            {
              "oid": 3,
              "name": "none"
            }
          ],
          "mandatory": true,
          "answer": [
            {
              "oid": 0,
              "name": ""
            },
            {
              "oid": 1,
              "name": ""
            }
          ]
        }
      ],
      "MemberId": "543"
    }
  }
}
```
Updates details in a form object.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| Payment link url. |
title |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -|The title of the form.|
question_list |Array|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -|The list that has questions objects. |
status |Boolean|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The status of the form for example, "pending".|

### Returns

Returns The newly updated form object if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
At least one attribute to be provided for the payment link. 
</aside>

<aside class="notice">
Questions list can't be updated after receiving responses
</aside>

<aside class="notice">
The error codes used when you fail to update a form are <a href="#4111">4111</a>, <a href="#1110">1110</a>
</aside>

#################################################################################

## Activate form

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/form/activate/{payment_link_url}'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  "data":
	{
	  "payment_link_url": "https://bit.ly/3KXl3iA"
	}
```
Activate a form to collect responses in the checkout.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -| Payment link url.

### Returns

Returns The payment link url of activated form if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
The error code used when you fail to activate form is <a href="#4111">4111</a>
</aside>

#################################################################################

## Deactivate form

```shell
curl -X DELETE --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/form/deactivate/{payment_link_url}'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  "data":
    {
      "payment_link_url": "https://bit.ly/3KXl3iA"
	}   
  }
```
Deactivate the form.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|payment link url.

### Returns

Returns the payment link of deactivated form if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
The error code used when you fail to activate form is <a href="#4111">4111</a>
</aside>

#################################################################################

## List form responses

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://bit.ly/3KXl3iA"
     'https://circlepay.ai/apis/form/listResponses'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "form responses list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
   [  
    {
     "id": "1",
     "customer_mobile": "+201000121213",
     "form_id": "6",
     "answers": ""
    },
	{
     "id": "2",
     "customer_mobile": "+201100121213",
     "form_id": "6",
     "answers": ""
	}
   ]
```
List all form responses.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| The url of the payment link. |
customer_mobile |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| Customer's mobile number. |

### Returns

Returns response object list if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
at least one attribute to be provided. 
</aside>

<aside class="notice">
The error codes used when you fail to update a coupon are <a href="#4111">4111</a> , <a href="#3110">3110</a> 
</aside>

####################################################################################

# Settlements

Means that payments or transactions finally settle and clear for customer use.

## Retrieve a settlement

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/settlements/get/{settlement_id}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Settlement object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "transfer_date": 22-02-2022,
	 "transfer_value": 99.0,
	 "currency": "EGP",
	 "external_settlement_id": "5",
	 "status": 0,
	 "update_date": 23-02-2022
	}
}
```
Retrieves the details of settlement.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
settlement_id |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|Unique identifier for the settlement object.

### Returns

Returns a settlement object. 

####################################################################################

## List all settlements

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d filter[status]="pending"
	 -d filter[date_time_range]=5
     'https://circlepay.ai/apis/settlements/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Settlements list returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
  [
	{
	 "transfer_date": 23-02-2022,
	 "transfer_value": 99.0,
	 "currency": "EGP",
	 "external_settlement_id": "5",
	 "status": 0,
	 "update_date": 26-02-2022
	},
	{
	 "transfer_date": 22-02-2022,
	 "transfer_value": 99.0,
	 "currency": "EGP",
	 "external_settlement_id": "6",
	 "status": 1,
	 "update_date": 23-02-2022
	}
  ]
}
```
Retrieve all settlements.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
Filter |Object|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| This is the filter object.|
Filter.date_time_range |Integer|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -|The time range you allowed to settle. |
Filter.status |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -|The status of the settlement for example, "pending".|

### Returns

Returns a settlement object list. The list has a separate settlement objects. If no more settlements are available, the resulting array will be empty. 

####################################################################################

# Invoice

An invoice is an itemized list that records the products or services you provided to your customers, the total amount due, and a method for them to pay you for those items or services. Invoices can be paid in one payment or in installments.

## Create an invoice

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "customer[email]"="ahmed@gmail.com"
     -d "customer[city]"="mansoura"
     -d "invoice[invoice_number]"=55
     'https://circlepay.ai/apis/invoice/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created an invoice",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "invoice_number": "CIR_INV_1643670030261",
	 "items": [{"name":"shoe","description":"","quantity": 4,"price":90.0}],
	 "customer_mobile": "+201001212333",
	 "status": 1,
	 "create_date": 10-12-2022,
	 "due_date": 14-12-2022,
     "pref_payment_method": "CARD/PayMob",
	 "shipping_fees": 4.0,
	 "discount_value": 11.0,
	 "discount_type": "percent",
     "discount_value_calculated": 9.9,
     "tax": 10.0,
     "tax_value": 9.0,
     "shipping_policy": "shipping options you offer (overnight, standard, air mail, international)",
     "return_policy": "Amazon.com and most sellers on Amazon.com offer returns for items within 30 days of receipt of shipment.",
     "extra_notes":
	}
}
```
This endpoint creates an invoice for a given customer. The invoice created will be in "pending" status.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
customer |Object|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The details of the customer object. |
invoice |Object|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -|The details of the invoice object. |

### Returns

Returns an invoice object that has been created. Returns error if the customer ID provided is invalid.

<aside class="notice">
The error codes used when you fail to create an invoice are <a href="#5101">5101</a> , <a href="#1110">1110</a>
</aside>

####################################################################################

## Retrieve an invoice

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/invoice/get/{invoice_number}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Invoice object returned successfully",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "invoice_number": "CIR_INV_1643670030261",
	 "items": [{"name":"shoe","description":"","quantity": 4,"price":90.0}],
	 "customer_mobile": "+201001212333",
	 "status": 1,
	 "create_date": 10-12-2022,
	 "due_date": 14-12-2022,
     "pref_payment_method": "CARD/PayMob",
	 "shipping_fees": 4.0,
	 "discount_value": 11.0,
	 "discount_type": "percent",
     "discount_value_calculated": 9.9,
     "tax": 10.0,
     "tax_value": 9.0,
     "shipping_policy": "shipping options you offer (overnight, standard, air mail, international)",
     "return_policy": "Amazon.com and most sellers on Amazon.com offer returns for items within 30 days of receipt of shipment.",
     "extra_notes":
	}
}
```
Retrieves the invoice with the given invoice number.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
invoice_number |String|<span style="color: red;">required</span>|&nbsp;&nbsp; &nbsp; -|The invoice number.

### Returns

Returns an invoice object if a valid invoice number was provided. Returns an error otherwise.

<aside class="notice">
The error code used when you fail to retrieve an invoice is <a href="#5111">5111</a>
</aside>

####################################################################################

## list invoices

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/invoice/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully returned invoice list",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
   [
	{
	 "invoice_number": "CIR_INV_1643670030261",
	 "items": [{"name":"shoe","description":"","quantity": 4,"price":90.0}],
	 "customer_mobile": "+201001212333",
	 "status": 1,
	 "create_date": 10-12-2022,
	 "due_date": 14-12-2022,
     "pref_payment_method": "CARD/PayMob",
	 "shipping_fees": 4.0,
	 "discount_value": 11.0,
	 "discount_type": "percent",
     "discount_value_calculated": 9.9,
     "tax": 10.0,
     "tax_value": 9.0,
     "shipping_policy": "shipping options you offer (overnight, standard, air mail, international)",
     "return_policy": "Amazon.com and most sellers on Amazon.com offer returns for items within 30 days of receipt of shipment.",
     "extra_notes":
	},
		{
	 "invoice_number": "CIR_INV_16436702430261",
	 "items": [{"name":"grocery","description":"","quantity": 4,"price":90.0}],
	 "customer_mobile": "+201001242333",
	 "status": 1,
	 "create_date": 10-12-2022,
	 "due_date": 14-12-2022,
     "pref_payment_method": "CARD/PayMob",
	 "shipping_fees": 4.0,
	 "discount_value": 11.0,
	 "discount_type": "percent",
     "discount_value_calculated": 9.9,
     "tax": 10.0,
     "tax_value": 9.0,
     "shipping_policy": "shipping options you offer (overnight, standard, air mail, international)",
     "return_policy": "Amazon.com and most sellers on Amazon.com offer returns for items within 30 days of receipt of shipment.",
     "extra_notes":
	}
   ]
}
```
This endpoint list invoices for a given customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
customer_mobile |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|Customer's mobile number.
Filter |String|<span style="color: lightblue;">optional</span>|&nbsp;&nbsp; &nbsp; -|invoices list returned based on this filter object.

### Returns

Returns list of invoice objects.

<aside class="notice">
The error code used when you fail to list invoices are <a href="#3110">3110</a>
</aside>

########################################################################################

## Delete an invoice

```shell
curl -X DELETE --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/invoice/delete/{invoice_number}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully deleted an invoice",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "invoice_number": "CIR_INV_16436702430261"
	}
}
```
Delete an invoice ONLY IF the invoice has no transactions.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
invoice_num |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Invoice's number.|

### Returns

Returns the deleted invoice number.

<aside class="notice">
The error code used when you fail to delete an invoice is <a href="#5111">5111</a>
</aside>

####################################################################################

## Pay an invoice

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d invoice_number="CIR_INV_16436702430261"
     'https://circlepay.ai/apis/invoice/payInvoice'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully pay the invoice",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{}
}
```

Pay an invoice.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
invoice_number |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Invoice's number.|
Customer |Object|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| Customer object (needed to update the current customer).|
payment_method_name |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The payment method name.|
payment_gateway_name |String|<span style="color: lightblue;">optional</span> |&nbsp;&nbsp; &nbsp; -| The payment gateway name.|

<aside class="notice">
Payment method and payment gateway must be together, can't send only one.
</aside>

<aside class="notice">
The error codes used when you fail to pay an invoice are <a href="#5111">5111</a> , <a href="#5114">5114</a> , <a href="#7113">7113</a> , <a href="#7111">7111</a> 
</aside>

### Returns

Pay the invoice if a valid invoice number was provided. Returns an error otherwise.

####################################################################################

## Settle an invoice

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d invoice_number="CIR_INV_16436702430261"
     'https://circlepay.ai/apis/invoice/setInvoiceToPaid'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully settled the invoice",
 "isError" : False,
 "errorCode" : null,
 "errorDetails" : null,
 "data" :
	{
	 "status": "Paid",
	 "invoice_number": "CIR_INV_16436702430261"
	}
}
```
Settle the invoice with the given id.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
invoice_number |String|<span style="color: red;">required</span> |&nbsp;&nbsp; &nbsp; -| Invoice's number.|

### Returns

Returns the settled invoice number and status if a valid invoice number was provided. Returns an error otherwise.

####################################################################################