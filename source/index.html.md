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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	[
	 { 
		"id": 1,
		"name": "ahmed",
		"payment_methods": []
	 },
	 {
		"id": 1,
		"name": "ahmed",
		"payment_methods": []
	 }  
	]
}
```

Retrieves all payment gateways to the merchant.

### Parameters

No parameters.

### Returns

Returns payment gateway list.

<aside class="notice">
The error code used when you fail to list payment gateways is <a href="#1110">1110</a>
</aside>

########################################################################

## Retrieve a Payment Gateway

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d gateway_id=2
     'https://circlepay.ai/apis/PaymentGateway/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment gateway object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" : 
   {
	 "id": 1,
	 "name": "ahmed",
	 "payment_methods": []
   }
}
```

Retrieves a specific payment gateway.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
gateway_id |  |<span style="color: lightblue;">optional</span>| |Unique identifier for the payment gateway object.


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
etisalatCash|3D Secure Card Payment|Cash Collection
orangeCash|Authorize and Capture Payment|ValU
VodavoneCash|E-wallet Payment|Mobile Wallets
ValU|Payment Request using Reference Number|Bank Installments
SADAD|ValU|Premium Card
mada|Installment Payment|SOUHOOLA
ApplePay |   |GET_GO
Knet|   |
American express|   |     

<aside class="notice">
<span style="color: red">Paymob, Fawry, MyFatoorah</span> are payment gateways. Each of these payment gateways are supporting a number of payment methods. So, a payment method won't be available unless you enable the corresponding payment gateway.
</aside>

## List a Payment Methods

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d gateway_id=2 
     'https://circlepay.ai/apis/PaymentMethod/list/'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment methods list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	[
	 {
		"id": 1,
		"name": "ahmed",
		"type": "card",
		"gateway": "paymob",
		"rate": 1
	 },
	 {
		"id": 1,
		"name": "ahmed",
		"type": "card",
		"gateway": "paymob",
		"rate": 1
	 }
	]
}
```

Retrieves all payment methods of the merchant.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
gateway_id |  |<span style="color: red;">required</span>| |Unique identifier for the payment gateway object.

### Returns

Returns a payment methods list.

<aside class="notice">
The error codes used when you fail to list payment methods are <a href="#8111">8111</a> , <a href="#7111">7111</a>
</aside>

#################################################################################

## Retrieve a Payment Method

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d gateway_id=2
     'https://circlepay.ai/apis/PaymentMethod/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment method object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "name": "ahmed",
	 "type": "card",
	 "gateway": "paymob",
	 "rate": 1
	}
}
```

Retrieves a specific payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
gateway_id ||<span style="color: lightblue;">optional</span>| |Unique identifier for the payment gateway object. |

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
     -d "mobile_number"="923847"
	 -d "Business_Name"="CirclePay"
     -d "Business_Address"="El-maadi"
     'https://circlepay.ai/apis/Merchant/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created a new merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "firstName": "ahmed",
	 "lastName": "khaled",
	 "email": "hi@bye.com",
	 "phone_number": "22222",
	 "picture": null,
	 "id_card": null,
	 "payment_method": null,
	 "circles": [],
	 "billing_info": null,
	 "documents": null,
	 "alert": null,
	 "settlement": null,
	 "business_individual": null,
	 "type_of_business": null
	}
}
```

This endpoint helps you to create new merchant.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
first_name ||<span style="color: red;">required</span>|| The merchant's first name. |
last_name ||<span style="color: red;">required</span>|| The merchant's last name. |
email ||<span style="color: red;">required</span>|| The merchant's email. |
mobile_number||<span style="color: red;">required</span>|| The merchant's phone number. |
Business_Name ||<span style="color: red;">required</span>|| The business name. |
Business_Address ||<span style="color: red;">required</span>|| The business address. |

<aside class="notice">
Password will be auto generated.
</aside>

### Returns

Returns the merchant object if the update succeeded. Returns an error if create parameters are invalid.

<aside class="notice">
The error codes used when you fail to create a merchant are <a href="#8110">8110</a> , <a href="#1110">1110</a> , <a href="#1112">1112</a>
</aside>

########################################################################################

## Retrieve a Merchant

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully retrieve the merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "firstName": "ahmed",
	 "lastName": "khaled",
	 "email": "hi@bye.com",
	 "phone_number": "22222",
	 "picture": null,
	 "id_card": null,
	 "payment_method": null,
	 "circles": [],
	 "billing_info": null,
	 "documents": null,
	 "alert": null,
	 "settlement": null,
	 "business_individual": null,
	 "type_of_business": null
	}
}
```

Retrieves a specific merchant.

### Returns

Returns the merchant object for a valid identifier.

#################################################################################

## Update a Merchant

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "firstName": "ahmed",
	 "lastName": "khaled",
	 "email": "hi@bye.com",
	 "phone_number": "22222",
	 "picture": null,
	 "id_card": null,
	 "payment_method": null,
	 "circles": [],
	 "billing_info": null,
	 "documents": null,
	 "alert": null,
	 "settlement": null,
	 "business_individual": null,
	 "type_of_business": null
	}
}
```

Updates the specified merchant by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
first_name ||<span style="color: red;">required</span>|| The merchant's first name. |
last_name ||<span style="color: red;">required</span>|| The merchant's last name. |
email ||<span style="color: red;">required</span>|| The merchant's email. |
mobile_number||<span style="color: red;">required</span>|| The merchant's phone number. |
Business_Name ||<span style="color: red;">required</span>|| The business name. |
Business_Address ||<span style="color: red;">required</span>|| The business address. |

### Returns

Returns the merchant object if the update succeeded. Returns an error if update parameters are invalid.

<aside class="notice">
The error codes used when you fail to update a merchant are <a href="#8116">8116</a> , <a href="#1110">1110</a> , <a href="#1112">1112</a>
</aside>

####################################################################################

## Update Document

```shell
curl -X PUT --header 'Accept: application/json'
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
 "message" : "You successfully update the merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
     {
      "document_id": "124234",
      "file_size": 7969,
      "upload_date": 22-3-2022,
      "last_modified": 23-3-2022,
      "document_type": "national id"
     }
}
```

Updates the specified merchant's doucment by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
File ||<span style="color: red;">required</span>|| The merchant's document file. |
document_id ||<span style="color: red;">required</span>|| Unique identifer of document. |
document_type ||<span style="color: red;">required</span>|| Document's type (predefined list). |


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
- Status ((ACTIVATED - DEACTIVATED - SUSPENDED))

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
     {
       "status": "SUSPENDED"
     }
}
```

Updates the specified merchant's status.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
status ||<span style="color: red;">required</span>|| The merchant's status. |

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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
   [
	{
	 "id": 1,
	 "firstName": "ahmed",
	 "lastName": "khaled",
	 "email": "hi@bye.com",
	 "phone_number": "22222",
	 "picture": null,
	 "id_card": null,
	 "payment_method": null,
	 "circles": [],
	 "billing_info": null,
	 "documents": null,
	 "alert": null,
	 "settlement": null,
	 "business_individual": null,
	 "type_of_business": null
	},
	{
	 "id": 1,
	 "firstName": "ahmed",
	 "lastName": "khaled",
	 "email": "hi@bye.com",
	 "phone_number": "22222",
	 "picture": null,
	 "id_card": null,
	 "payment_method": null,
	 "circles": [],
	 "billing_info": null,
	 "documents": null,
	 "alert": null,
	 "settlement": null,
	 "business_individual": null,
	 "type_of_business": null
	}
   ]
}
```

Retrieves all merchants.

### Parameters

No parameters.

### Returns

Returns an array. Each entry in the array is a separate user object.This request should never return an error.

########################################################################################

## List all documents

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/Merchant/listDocuments'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Documents list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
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
	  "file_size": 799,
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
     'https://circlepay.ai/apis/Merchant/getFile'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Documents list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	 {
      "document_Id":"3264",
      "file_stream":"e:\\b.txt",
      "file_ext": ".txt"
	 }
}
```

Retrieves file document.

### Parameters

No parameters.

### Returns

Returns file document.

####################################################################################

## Set Billing info

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d Bank_Name="cairo bank"
	 -d Bank_Account_Num="24234234"
     'https://circlepay.ai/apis/Merchant/setBillingInfo'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
     {
	  "Bank_Name": "cairo bank",
	  "Bank_Account_Num": 234242,
	  "Bank_Branch_Name": "maadi branch",
	  "SWIFT": "BCAIEGCXXXX",
	  "IBAN": "GB98 MIDL 0700 9312 3456 78"
     }
}
```

Updates the billing info by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
Bank_Name ||<span style="color: red;">required</span>|| Bank's name. |
Bank_Account_Num ||<span style="color: red;">required</span>|| The bank account number. |
Bank_Branch_Name ||<span style="color: red;">required</span>|| The bank branch name. |
SWIFT ||<span style="color: red;">required</span>|| Society for Worldwide Interbank Financial Telecommunications, the SWIFT code can be found on a bank's website, on your bank statement, or through an online search. |
IBAN ||<span style="color: lightblue;">optional</span>|| international bank account number, is a standard international numbering system developed to identify an overseas bank account. The number starts with a two-digit country code, then two numbers, followed by several more alphanumeric characters. |


### Returns

Returns the billing info object if the update succeeded. Returns an error if update parameters are invalid.

<aside class="notice">
The error code used when you fail to set the billing info is <a href="#1110">1110</a>
</aside>


#################################################################################

## Configure payment gateway

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d payment_gateway_id="34534534"
     'https://circlepay.ai/apis/Merchant/configurePaymentGateway'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully update the merchant",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
     {
	  "payment_gateway_id": "2089472",
     }
}
```

Set the payment gateway keys for a specific merchant to allow CirclePay connect to the merchant account on the Payment Gateway

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_gateway_id ||<span style="color: red;">required</span>|| Unique identifier of payment gateway. |
Gateway_Config_Object ||<span style="color: red;">required</span>|| The gateway config object. |


### Returns

Returns the payment gateway id.

<aside class="notice">
The error codes used when you fail to configure payment gateway are <a href="#7111">7111</a>, <a href="#8112">8112</a>
</aside>


#################################################################################

## Enable gateway

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d gateway_id=4
     'https://circlepay.ai/apis/Merchant/enable'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully enabled gateway",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{ }
}
```

This endpoint enable specific gateway.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
gateway_id ||<span style="color: red;">required</span> || Unique identifier for the payment gateway object. |

### Returns

Returns success message if gateway enabled.

<aside class="notice">
The error codes used when you fail to enable gateway are <a href="#7110">7110</a> , <a href="#7111">7111</a>
</aside>

####################################################################################

## Disable gateway

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d gateway_id=4
     'https://circlepay.ai/apis/Merchant/disable'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully disabled gateway",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{}
```

This endpoint disable specific gateway and it's related payment methods.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
gateway_id ||<span style="color: red;">required</span> || Unique identifier for the payment gateway object. |

### Returns

Returns success message if gateway disabled.

####################################################################################

## Set payment method fee

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_method_id=4
     'https://circlepay.ai/apis/Merchant/setPaymentMethodFee'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully enabled the payment method",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	  "status": true,
	  "totalRevenue": 0,
	  "paymentFeePercentage": 0,
	  "paymentFeeAmount": 0,
	  "refundFeePercentage": 0,
	  "refundFeeAmount": 0,
	  "id": 0,
	  "MerchantId": 0,
	  "PaymentMethodId": 0,
	  "createdAt": 23-2-2022,
	  "updatedAt": 24-2-2022
	}
}
```

This endpoint Set the fees for each payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_id ||<span style="color: red;">required</span> || Unique identifier for the payment method object. |
Fee_Fixed ||<span style="color: red;">required</span> || The fixed fee. |
Fee_Percent ||<span style="color: red;">required</span> || The percentage fee. |
Refund_Fee_Fixed ||<span style="color: red;">required</span> || The Refund fixed fee. |
Refund_Fee_Percent ||<span style="color: red;">required</span> || The Refund fee percentage. |

### Returns

Returns the payment method object.

<aside class="notice">
The error codes used when you fail to set payment method fee are <a href="#7111">7111</a> , <a href="#7113">7113</a> , <a href="#1110">1110</a> , <a href="#7116">7116</a>
</aside>

#######################################################################################

## Enable payment method

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_method_id=4
     'https://circlepay.ai/apis/Merchant/enablePaymentMethod'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully enabled the payment method",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	  "status": true,
	  "totalRevenue": 0,
	  "paymentFeePercentage": 0,
	  "paymentFeeAmount": 0,
	  "refundFeePercentage": 0,
	  "refundFeeAmount": 0,
	  "id": 0,
	  "MerchantId": 0,
	  "PaymentMethodId": 0,
	  "createdAt": 23-2-2022,
	  "updatedAt": 24-2-2022
	}
}
```

This endpoint enable specific payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_id ||<span style="color: red;">required</span> || Unique identifier for the payment method object. |

### Returns

Returns the payment method object.

<aside class="notice">
The error codes used when you fail to enable payment method are <a href="#7112">7112</a> , <a href="#7113">7113</a> , <a href="#1110">1110</a>
</aside>

#######################################################################################

## Disable payment method

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_method_id=4
     'https://circlepay.ai/apis/Merchant/disablePaymentMethod'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully disabled the payment method",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	  "status": false,
	  "totalRevenue": 0,
	  "paymentFeePercentage": 0,
	  "paymentFeeAmount": 0,
	  "refundFeePercentage": 0,
	  "refundFeeAmount": 0,
	  "id": 0,
	  "MerchantId": 0,
	  "PaymentMethodId": 0,
	  "createdAt": 23-2-2022,
	  "updatedAt": 24-2-2022
	}
}
```

This endpoint disable specific payment method.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_method_id ||<span style="color: red;">required</span> || Unique identifier for the payment method object. |

### Returns

Returns the payment method object.

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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "payment_methods":
	  [ 
		{
		  "name": "payment method-1",
		  "id": 2
		},
		{
		  "name": "payment method-2",
		  "id": 3
		}
	  ]
	}
}
```

This endpoint list allowed payment methods to the merchant.

### Parameters

No parameters.

### Returns

Returns a payment methods list.

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
     -d "mobile_number"="923847"
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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{  
	 "id": 3,
	 "first_name": "Ahmed",
	 "last_name": "khaled",
	 "email":"ahmedkhaled@gmail.com",
	 "phone_number": "0238432",
	 "transaction_id": {},
	 "refund_id": {},
	 "circle_id": {}
	}
}
```

This endpoint helps you to create new customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
First_Name ||<span style="color: red;">required</span>|| The customer's first name. |
Last_Name ||<span style="color: red;">required</span>|| The customer's last name. |
email ||<span style="color: red;">required</span>|| The customer's email. |
mobile_number||<span style="color: red;">required</span>|| The customer's phone number. |
country ||<span style="color: red;">required</span>|| The customer's country. |
governorate ||<span style="color: red;">required</span>|| The customer's governorate. |
city ||<span style="color: red;">required</span>|| The customer's city. |
address ||<span style="color: red;">required</span>|| The customer's address. |
apt_num ||<span style="color: red;">required</span>|| The customer's apartment number. |

### Returns

Returns the customer object if the customer's creation succeeded. Returns an error if parameters are invalid.

<aside class="notice">
The error codes used when you fail to create a customer are <a href="#3111">3111</a> , <a href="#1110">1110</a>
</aside>

########################################################################################

## Update a Customer

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "First_Name"="Ahmed"
     -d "Last_Name"="Khaled"
     -d "email"="ahmedkahled@gmail.com"
     -d "mobile_number"="923847"
	 -d "country"="Egypt"
     -d "city"="cairo"
     'https://circlepay.ai/apis/Customer/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated cutomer",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{  
	 "id": 3,
	 "first_name": "Ahmed",
	 "last_name": "khaled",
	 "email":"ahmedkhaled@gmail.com",
	 "phone_number": "0238432",
	 "transaction_id": {},
	 "refund_id": {},
	 "circle_id": {}
	}
}
```

This endpoint helps you to create new customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
First_Name ||<span style="color: red;">required</span>|| The customer's first name. |
Last_Name ||<span style="color: red;">required</span>|| The customer's last name. |
email ||<span style="color: red;">required</span>|| The customer's email. |
mobile_number||<span style="color: red;">required</span>|| The customer's phone number. |
country ||<span style="color: red;">required</span>|| The customer's country. |
governorate ||<span style="color: red;">required</span>|| The customer's governorate. |
city ||<span style="color: red;">required</span>|| The customer's city. |
address ||<span style="color: red;">required</span>|| The customer's address. |
apt_num ||<span style="color: red;">required</span>|| The customer's apartment number. |

### Returns

Returns the customer object if the customer's update succeeded. Returns an error if parameters are invalid.

<aside class="notice">
The error codes used when you fail to update a customer are <a href="#3110">3110</a> , <a href="#1110">1110</a>
</aside>

########################################################################################

## Retrieve a customer

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d mobile_number=239487
     'https://circlepay.ai/apis/Customers/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Customer object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{  
	 "id": 3,
	 "first_name": "Ahmed",
	 "last_name": "khaled",
	 "email":"ahmedkhaled@gmail.com",
	 "phone_number": "0238432",
	 "transaction_id": {},
	 "refund_id": {},
	 "circle_id": {}
	}
}
```

Retrieves a specific customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
mobile_number ||<span style="color: red;">required</span> || The mobile number of the customer. |

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
     -d user_id=2
     'https://circlepay.ai/apis/Customers/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Customers list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{  
	 "id": 3,
	 "first_name": "Ahmed",
	 "last_name": "khaled",
	 "email":"ahmedkhaled@gmail.com",
	 "phone_number": "0238432",
	 "transaction_id": {},
	 "refund_id": {},
	 "circle_id": {}
	}
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
     -d "description": "payment link"
     -d "expire_date": "1-22-2022"
     'https://circlepay.ai/apis/Payment_Link/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created the payment link",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 0,
	 "url": "ahmed",
	 "form_id": 0,
	 "coupon_id": [],
	 "description": "desc",
	 "value": 0,
	 "currency": "EGP",
	 "expire_date": "2022-10-12",
	 "payment_method": [],
	 "payment": [],
	 "status": true,
	 "paying_customer": [],
	 "fees_list": []
	}
}
```

This endpoint helps you to create payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
value ||<span style="color: red;">required</span> || The value of payment. |
currency ||<span style="color: red;">required</span> || Currency type used in payment. |
enable_Survey ||<span style="color: red;">required</span> || Switch that helps you to enable or disable survey. |
expire_date ||<span style="color: red;">required</span> || Expire date of the payment link. |
description ||<span style="color: red;">required</span> || Description of transaction. |
shippingPolicyFlag ||<span style="color: red;">required</span> || The shipping policy flag. |
status || <span style="color: red;">required</span> || The status of the payment link, to know if the payment link is still valid. |
refundPolicyFlag || <span style="color: red;">required</span> || The refund policy flag. |
shippingPolicyDetails || <span style="color: red;">required</span> || The shipping policy Details for example, original sales receipt must accompany returns. |
refundPolicyDetails || <span style="color: red;">required</span> || The refund policy details for example, refunds and exchanges, Right to cancel your order. |
comments || <span style="color: red;">required</span> || Comments help merchant and customer to know more about order details and order process. |
name || <span style="color: red;">required</span> || The name of the customer. |
getCustAddress || <span style="color: red;">required</span> || The customer's address. |
merchantId || <span style="color: red;">required</span> || Unique identifier for the merchant object. |


### Returns

Returns the payment link object.

<aside class="notice">
The error codes used when you fail to create payment link are <a href="#4101">4101</a> , <a href="#1110">1110</a> , <a href="#4112">4112</a> 
</aside>

####################################################################################

## Retrieves a payment link

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd" 
     'https://circlepay.ai/apis/Payment_Link/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment link object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 0,
	 "url": "ahmed",
	 "form_id": 0,
	 "coupon_id": [],
	 "description": "desc",
	 "value": 0,
	 "currency": "EGP",
	 "expire_date": "2022-10-12",
	 "payment_method": [],
	 "payment": [],
	 "status": true,
	 "paying_customer": [],
	 "fees_list": []
	}
}
```

Retrieves a specific payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: lightblue;">optional</span> || The url of the payment link. |

### Returns

Returns the payment link object.

####################################################################################

## Update a payment link

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/Payment_Link/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the payment link",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 0,
	 "url": "ahmed",
	 "form_id": 0,
	 "coupon_id": [],
	 "description": "desc",
	 "value": 0,
	 "currency": "EGP",
	 "expire_date": "2022-10-12",
	 "payment_method": [],
	 "payment": [],
	 "status": true,
	 "paying_customer": [],
	 "fees_list": []
	}
}
```
This endpoint helps you to udpate payment link.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_id ||<span style="color: red;">required</span> || Unique identifier for the payment link object. |
payment_link_url ||<span style="color: red;">required</span> || The url of the payment link. |
value ||<span style="color: lightblue;">optional</span> ||The value of payment.|
description ||<span style="color: lightblue;">optional</span> || Description of transaction. |
expire_date ||<span style="color: lightblue;">optional</span> || Expire date of the payment link. |
payment_method_id ||<span style="color: lightblue;">optional</span> || List of unique identifier(s) for the payment method object(s). |
status ||<span style="color: lightblue;">optional</span> || The status of the payment link, to know if the payment link is still valid. |
fees_list ||<span style="color: lightblue;">optional</span> || The fixed price charged for a payment. |

### Returns

Returns the payment link object.

<aside class="notice">
The error codes used when you fail to update payment link are <a href="#4111">4111</a> , <a href="#1110">1110</a> , <a href="#4112">4112</a> 
</aside>

#################################################################################

## Deactive payment link

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/Payment_Link/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment links list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{}
}
```

Deactivate an active payment link. 

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || Payment link url.|

### Returns

Deactivate an active payment link. This will show an error page "Payment Link isn't available.

<aside class="notice">
The error code used when you fail to deactive payment link is <a href="#4111">4111</a>
</aside>


####################################################################################

## List all payment links

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "customer_mobile": 239494
     'https://circlepay.ai/apis/Payment_Link/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment links list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 0,
	 "url": "https://buy.circlepay.ai/sldkfhsd",
	 "form_id": 0,
	 "coupon_id": [],
	 "description": "desc",
	 "value": 0,
	 "currency": "EGP",
	 "expire_date": "2022-10-12",
	 "payment_method": [],
	 "payment": [],
	 "status": true,
	 "paying_customer": [],
	 "fees_list": []
	}
}
```

Retrieves all payment links.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
customer_mobile ||<span style="color: lightblue;">optional</span> || Customer's mobile number. |
Filter ||<span style="color: red;">required</span> || The filter object that has fields you want to retrieve. |

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
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/PayPaymentLink/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payment links list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{}
}
```

Execute a payment for a specific payment link or an invoice.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || The payment link url. |
Customer Object ||<span style="color: lightblue;">optional</span> || The customer object. |
Form_Response Object ||<span style="color: lightblue;">optional</span> || The form response object. |
payment_method_name ||<span style="color: lightblue;">optional</span> || The payment method name. |
payment_gateway_name ||<span style="color: lightblue;">optional</span> || The payment gateway name. |
coupon_code ||<span style="color: lightblue;">optional</span> || The coupon code. |

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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "date_time": "2022-10-12",
	 "merchant_id": 1,
	 "customer_id": 1,
	 "status": true,
	 "payment_link_id": 1,
	 "coupon_id": 1,
	 "amount_paid": 1,
	 "currency": "EGP",
	 "payment_method": null,
	 "source": "external"
	}
}
```

Retrieves the details of an existing payment.

### Parameters

No parameters.

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
     -d "coupon_code": 423746
     'https://circlepay.ai/apis/Payment/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Payments list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	[
	 {
		"id": 1,
		"date_time": "2022-10-12",
		"merchant_id": 1,
		"customer_id": 1,
		"status": "true",
		"payment_link_id": 1,
		"coupon_id": 1,
		"amount_paid": 1,
		"currency": "EGP",
		"payment_method": null,
		"source": "external"
	 },
	 {
		"id": 1,
		"date_time": "2022-10-12",
		"merchant_id": 1,
		"customer_id": 1,
		"status": true,
		"payment_link_id": 1,
		"coupon_id": 1,
		"amount_paid": 1,
		"currency": "EGP",
		"payment_method": null,
		"source": "external"
	 }
	]
}
```

Retrieves all payments.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_code ||<span style="color: red;">required</span>|| The coupon code. |
customer_mobile ||<span style="color: lightblue;">optional</span>|| Customer's mobile number. |
payment_link_url ||<span style="color: lighblue;">optional</span>|| The payment link url. |
invoice_num ||<span style="color: lighblue;">optional</span>|| The invoice number. |

### Returns

Returns a payment list which has the details of the payment like: status, amount paid and payment method.

<aside class="notice">
Also there is a filter object which contains values of wanted payment objects.
</aside>


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
	 -d value=33
     'https://circlepay.ai/apis/Refund/requestRefund'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully requested a refund",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "request_date": "2022-10-12",
	 "refund_date": "2022-10-12",
	 "value": 33,
	 "payment_id": 1,
	 "fees_list": [],
	 "payment_method": [],
	 "status": "pending",
	 "customer": null
	}
}
```
This endpoint helps you to request refund.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
transaction_id ||<span style="color: red;">required</span> || Unique identifier for the transaction object.|
value ||<span style="color: red;">required</span> || Value of the refund.|
currency ||<span style="color: red;">required</span> || The currency type used. |


### Returns

Returns the refund object. Status in refund object will be in pending state.

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
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/Refund/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Refunds list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	[
	 {
		"id": 1,
		"request_date": "2022-10-12",
		"refund_date": "2022-10-12",
		"value": 1,
		"transaction_id": 1,
		"fees_list": [],
		"payment_method": [],
		"status": [],
		"customer": null
	 },
	 {
		"id": 2,
		"request_date": "2022-10-12",
		"refund_date": "2022-10-12",
		"value": 2,
		"transaction_id": 2,
		"fees_list": [],
		"payment_method": [],
		"status": [],
		"customer": null
	 }
    ]
}
```
List refund objects.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
transaction_id ||<span style="color: lightblue;">optional</span>|| Unique identifier of transaction object. |
customer_mobile ||<span style="color: lightblue;">optional</span>|| Customer's mobile number. |
payment_link_url ||<span style="color: lighblue;">optional</span>|| The payment link url. |
invoice_num ||<span style="color: lighblue;">optional</span>|| The invoice number. |

### Returns

Returns refund list. If no more refunds are available, the resulting array will be empty.

<aside class="notice">
Also there is a filter object which contains values of wanted payment objects.
</aside>

<aside class="notice">
The error codes used when you fail to list refund list are <a href="#9111">9111</a> , <a href="#3110">3110</a> , <a href="#4111">4111</a> , <a href="#5111">5111</a> , <a href="#1110">1110</a>
</aside>

#######################################################################################

## Get refund status

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
 "message" : "Refund's status returned successfully ",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "status":"pending"
	}
}
```
Retrieves the status of refund object.

### Parameters

No parameters.

### Returns

Returns the status of refund object, for example: "approved", "pending" or "rejected".

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
     -d value=1
     -d name="AHMEDCOUPON"
	 -d expire_date=22-2-2022
     'https://circlepay.ai/apis/Coupon/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created a coupon",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "payment_link_id": 1,
	 "code": 1,
	 "value": 1,
	 "name": "ahmed",
	 "number_of_uses": 1,
	 "discount_t": "%"
	}
}
```
This endpoint helps you to create coupon.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || The payment link url. |
code ||<span style="color: red;">required</span> || The code of coupon. |
value ||<span style="color: red;">required</span> || The value of the payment after discounting. |
name ||<span style="color: red;">required</span> || The name of the coupon. |
expire_date ||<span style="color: red;">required</span> || Coupon's expire date.|
number_of_uses ||<span style="color: red;">required</span> || Number of uses to this coupon. |
discount_value ||<span style="color: red;">required</span> || Coupon's discount value. |
discount_type ||<span style="color: red;">required</span> || number or percentage. |

### Returns

Returns the coupon object. 

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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "value": 1,
	 "name": "ahmed",
	 "expire_date": "2022-12-22",
	 "number_of_uses": 1,
	 "payment_link_id": 1,
	 "payments": null,
	 "status": 1,
	 "times_per_customer": 1,
	 "customer": []
	}
}
```
Retrieves a specific coupon.

### Parameters

No parameters.

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
     -d value=1
     -d name="AHMEDCOUPON"
     'https://circlepay.ai/apis/Coupon/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the coupon",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "value": 1,
	 "name": "ahmed",
	 "expire_date": "2022-12-22",
	 "number_of_uses": 1,
	 "payment_link_id": 1,
	 "payments": null,
	 "status": "active",
	 "times_per_customer": 1,
	 "customer": []
	}
}
```
Updates the metadata of a coupon.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_code ||<span style="color: red;">required</span> ||The code of coupon.|
value ||<span style="color: red;">required</span> || The value of the payment after discounting. |
name ||<span style="color: red;">required</span> ||The name of the coupon.|
expire_date ||<span style="color: red;">required</span> ||Coupon's expire date.|
number_of_uses ||<span style="color: red;">required</span> || Number of uses for this coupon. |
status ||<span style="color: red;">required</span> ||The status of the coupon for example, expired.|
times_per_customer ||<span style="color: red;">required</span> || Times that customer can use the same coupon. |

### Returns

The newly updated coupon object if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

<aside class="notice">
The error codes used when you fail to update a coupon are <a href="#4312">4312</a> , <a href="#4112">4112</a> , <a href="#4311">4311</a> , <a href="#1110">1110</a>
</aside>

##############################################################################

## Activate coupon

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d coupon_id=1
     'https://circlepay.ai/apis/Coupon/activate'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the coupon",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "value": 1,
	 "name": "ahmed",
	 "expire_date": "2022-12-22",
	 "number_of_uses": 1,
	 "payment_link_id": 1,
	 "payments": null,
	 "status": "active",
	 "times_per_customer": 1,
	 "customer": []
	}
}
```
Updates status of the coupon to active.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_id ||<span style="color: red;">required</span> ||Unique identifier of coupon object.|

### Returns

The newly activated coupon object if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

<aside class="notice">
The error code used when you fail to active the coupon is <a href="#4311">4311</a>
</aside>

##############################################################################

## deactive coupon

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d coupon_id=1
     'https://circlepay.ai/apis/Coupon/deactive'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the coupon",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "value": 1,
	 "name": "ahmed",
	 "expire_date": "2022-12-22",
	 "number_of_uses": 1,
	 "payment_link_id": 1,
	 "payments": null,
	 "status": "deactive",
	 "times_per_customer": 1,
	 "customer": []
	}
}
```
Updates status of the coupon to deactive.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_id ||<span style="color: red;">required</span> ||Unique identifier of coupon object.|

### Returns

The newly deactivated coupon object if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

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
     'https://circlepay.ai/apis/Coupon/list/{paymentLinkUrl}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Coupons list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	[
	 {
		"id": 1,
		"value": 1,
		"name": "ahmed",
		"expire_date": "2022-12-22",
		"number_of_uses": 1,
		"payment_link_id": 1,
		"payments": null,
		"status": "active",
		"times_per_customer": 1,
		"customer": []
	 },
	 {
		"id": 1,
		"value": 1,
		"name": "ahmed",
		"expire_date": "2022-12-22",
		"number_of_uses": 1,
		"payment_link_id": 1,
		"payments": null,
		"status": "expired",
		"times_per_customer": 1,
		"customer": []
	 }
	]
}
```
Returns a list of your coupons per payment link.

### Parameters

No parameters.

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
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     -d title="title"
     'https://circlepay.ai/apis/form/create'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  data:
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
This endpoint helps you to create form.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || Payment link url. |
title ||<span style="color: red;">required</span> ||The title of the form.|
question_list ||<span style="color: red;">required</span> ||The list that has questions objects. |
status ||<span style="color: red;">required</span> || The status of the form for example, "pending".|

### Returns

Returns form object which has the questions array

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
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/form/get'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  data:
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
payment_link_url ||<span style="color: red;">required</span> || Payment link url. |

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
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     -d title="title"
     'https://circlepay.ai/apis/form/update'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  data:
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
payment_link_url ||<span style="color: lightblue;">optional</span> || Payment link url. |
title ||<span style="color: lightblue;">optional</span> ||The title of the form.|
question_list ||<span style="color: lightblue;">optional</span> ||The list that has questions objects. |
status ||<span style="color: lightblue;">optional</span> || The status of the form for example, "pending".|

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
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/form/activate'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  data:
  {
    "survey": {
      "title": "new_survey",
      "status": true,
      "questions": [.....]
	}   
  }
```
Activate a form to collect responses in the checkout.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || Payment link url. |

### Returns

Returns The newly updated form object if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
The error code used when you fail to activate form is <a href="#4111">4111</a>
</aside>

#################################################################################

## Deactivate form

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/form/deactivate'
```

> The above command returns JSON structured like this:

```json
{
  "message": "Survey fetched successfully",
  "status":"true",
  data:
  {
    "survey": {
      "title": "new_survey",
      "status": false,
      "questions": [.....]
	}   
  }
```
Deactivate the form.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || Payment link url. |

### Returns

Returns The newly deactivated form object if the call succeeded. Otherwise, this call returns an error.

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
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'https://circlepay.ai/apis/form/listResponses'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "form responses list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	[
	 {
	  "id": 1,
	  "customer": null,
	  "form": null
	 },
	 {
	  "id": 1,
	  "customer": null,
	  "form": null
	 }
	]
}
```
List all form responses.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_url ||<span style="color: red;">required</span> || The url of the payment link. |
customer_mobile ||<span style="color: lightblue;">optional</span> || Customer's mobile number. |

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
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d settlement_id=5
     'https://circlepay.ai/apis/settlements/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Settlement object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "date_time": "2022-10-22",
	 "value": "1",
	 "currency": "EGP",
	 "invoice_url": "url",
	 "merchant": 1,
	 "status": "pending"
	}
}
```
Retrieve the details of settlement.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
settlement_id ||<span style="color: red;">required</span> ||Unique identifier for the settlement object.|

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
	 -d filter[date_time]=22-2-2022
     'https://circlepay.ai/apis/settlements/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Settlements list returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
  [
	{
	 "id": 1,
	 "date_time": "2022-10-22",
	 "value": "1",
	 "currency": "EGP",
	 "invoice_url": "url",
	 "merchant": 1,
	 "status": "pending"
	},
	{
	 "id": 1,
	 "date_time": "2022-10-22",
	 "value": "1",
	 "currency": "EGP",
	 "invoice_url": "url",
	 "merchant": 1,
	 "status": "pending"
	}
  ]
}
```
Retrieve all settlements.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
Filter ||<span style="color: lightblue;">optional</span> || This is the filter object.|
Filter.date_time ||<span style="color: lightblue;">optional</span> ||The date time when the settlement happened. |
Filter.status ||<span style="color: lightblue;">optional</span> ||The status of the settlement for example, "pending".|

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
     -d merchant=1
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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "pending",
	 "due_date": "2022-10-12"
	}
}
```
This endpoint creates an invoice for a given customer. The invoice created will be in "pending" status.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
item ||<span style="color: red;">required</span> ||The item used in the invoice.|
item.name ||<span style="color: red;">required</span> || The item name.|
item.description ||<span style="color: red;">required</span> || The description of item. |
item.price ||<span style="color: red;">required</span> ||Item's price. |
customer ||<span style="color: red;">required</span> ||The details of the customer. |
invoice ||<span style="color: red;">required</span> ||The details of the invoice. |

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
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "pending",
	 "due_date": "2022-10-12"
	}
}
```
Retrieves the invoice with the given id.

### Parameters

No parameters.

### Returns

Returns an invoice object if a valid invoice ID was provided. Returns an error otherwise.

<aside class="notice">
The error code used when you fail to retrieve an invoice is <a href="#5111">5111</a>
</aside>

####################################################################################

## list invoices

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "customer_mobile"=923847
     'https://circlepay.ai/apis/invoice/list'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created an invoice",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
   [
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "pending",
	 "due_date": "2022-10-12"
	},
	{
	 "number": 2,
	 "merchant": 2,
	 "customer": 2,
	 "status": "pending",
	 "due_date": "2022-10-12"
	}
   ]
}
```
This endpoint list invoices for a given customer.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
customer_mobile ||<span style="color: lightblue;">optional</span> || Customer's mobile number.|
Filter Object ||<span style="color: red;">required</span> || The Filter object that invoice will retrieved based on.|

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
     -d "invoice_number"=923847
     'https://circlepay.ai/apis/invoice/delete'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully deleted an invoice",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "pending",
	 "due_date": "2022-10-12"
	}
}
```
Delete an invoice ONLY IF the invoice has no transactions.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
invoice_number ||<span style="color: red;">required</span> || Invoice's number.|

### Returns

Returns the deleted invoice object.

<aside class="notice">
The error code used when you fail to delete an invoice is <a href="#5111">5111</a>
</aside>

####################################################################################

## Pay invoice

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
	 -d invoice_number=023847
     'https://circlepay.ai/apis/invoice/payInvoice'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully pay the invoice",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "Pending",
	 "due_date": "2022-10-12"
	}
}
```

Pay an invoice.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
invoice_number ||<span style="color: red;">required</span> || Invoice's number.|
Customer Object ||<span style="color: lightblue;">optional</span> || Customer object (needed to update the current customer).|
payment_method_name ||<span style="color: lightblue;">optional</span> || The payment method name.|
payment_gateway_name ||<span style="color: lightblue;">optional</span> || The payment gateway name.|

<aside class="notice">
Payment method and payent gateway must be together, can't send only one.
</aside>

5111, 5114, 7113, 7111

<aside class="notice">
The error codes used when you fail to pay an invoice are <a href="#5111">5111</a> , <a href="#5114">5114</a> , <a href="#7113">7113</a> , <a href="#7111">7111</a> 
</aside>

### Returns

Returns the paid invoice object if a valid invoice number was provided. Returns an error otherwise.

####################################################################################

## Settle an invoice

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'https://circlepay.ai/apis/invoice/setInvoiceToPaid/{invoice_number}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully settled the invoice",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "Paid",
	 "due_date": "2022-10-12"
	}
}
```
Settle the invoice with the given id.

### Parameters

No parameters.

### Returns

Returns the settled invoice object if a valid invoice ID was provided. Returns an error otherwise.

####################################################################################