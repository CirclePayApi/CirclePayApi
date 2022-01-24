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
     -d "first_name": "Ahmed"
     -d "last_name": "Khaled"
     -d "email": "ahmedkahled@gmail.com"
     -d "mobile_number": "923847"
	 -d "Business_Name": "CirclePay"
     -d "Business_Address": "El-maadi"
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

## Upload documents

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "document_list[id]"="124234" \
     -d "document_list[name]"="national id" \
     -d "document_list[size]"=7969 \
     'http://www.example.com/merchants/upload_documents?user_id=2'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully uploaded documents",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{  
	 "title":"success",
	 "message":"Documents Uploaded successfully",
	 "status":"200"
	}
}
```

To upload a file, The request should contain the document you would like to upload, as well as the parameters for creating a document.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
user_id ||<span style="color: red;">required</span> || Unique identifier for the user object. |
document_list ||<span style="color: red;">required</span> || It contains the details of the uploaded document. |
document_list.id ||<span style="color: red;">required</span> || The id of the document. |
document_list.name ||<span style="color: red;">required</span> || The name of the document for example, national id.|
document_list.size ||<span style="color: red;">required</span> || The size of the document in MB.|
document_list.upload_state ||<span style="color: red;">required</span> || The upload state of the document. |
document_list.last_update ||<span style="color: red;">required</span> || Last update of the document. |

### Returns

Returns success message if document uploaded.

###########################################################################

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
	{  
	 "title":"success",
	 "message":"Gateway enabled successfully",
	 "status":"200"
	}
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
	{  
	 "success":"The following payment gateways and payment methods got disabled",
	 "payment_gateway": {
		"name": "paymob",
		"id": 1
	 },
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

This endpoint disable specific gateway and it's related payment methods.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
gateway_id ||<span style="color: red;">required</span> || Unique identifier for the payment gateway object. |

### Returns

Returns success message if gateway disabled.

####################################################################################

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

## Retrieve a customer

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'http://www.example.com/customers/get/{customerId}'
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

### Parameters

No parameters.

### Returns

Returns the Customer object for a valid identifier.

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
     'http://www.example.com/customers/list'
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

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
user_id ||<span style="color: red;">required</span> || Unique identifier for the user object. |
circle_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the circle object. |

<aside class="notice">
Select the fields you want to retrieve.
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
     'http://www.example.com/payment_link/create'
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
description ||<span style="color: red;">required</span> || Description of transaction. |
expire_date ||<span style="color: red;">required</span> || Expire date of the payment link. |
payment_method_id ||<span style="color: lightblue;">optional</span> || List of unique identifier(s) for the payment method object(s). |
status || <span style="color: lightblue;">optional</span> || The status of the payment link, to know if the payment link is still valid. |
circle_id || <span style="color: lightblue;">optional</span> || Unique identifier for the circle object. |
fees_list || <span style="color: lightblue;">optional</span> || The fixed price charged for a payment. |

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
     -d "payment_link_id": 4
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd" 
     'http://www.example.com/payment_link/get'
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
payment_link_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the payment link object. |
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
     -d "payment_link_id": 3
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd"
     'http://www.example.com/payment_link/update'
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

## List all payment links

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d "circle_id": 4
     'http://www.example.com/payment_link/list'
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
circle_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the circle object. |

<aside class="notice">
Select the fields you want to retrieve.
</aside>

### Returns

Returns payment link list which is array contains payment link objects. If no payment links are available, the resulting array will be empty.

<aside class="notice">
The error codes used when you fail to list all payment links are <a href="#3110">3110</a> , <a href="#1110">1110</a>
</aside>


####################################################################################

# Payment

## Get a payment 

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'http://www.example.com/payment/get/{paymentId}'
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
     -d "payment_id": 4
     'http://www.example.com/payment/list'
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
payment_id ||<span style="color: red;">required</span>|| The list of Unique identifier(s) for the payment object(s). |

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
     -d value=54
     -d currency="EGP"
     'http://www.example.com/refund/request_refund'
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
	 "value": 1,
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
refund_id ||<span style="color: red;">required</span> || Unique identifier for the refund object.|
value ||<span style="color: red;">required</span> || Value of the refund.|
currency ||<span style="color: red;">required</span> || The currency type used. |
payment_id ||<span style="color: red;">required</span> ||Unique identifier for the payment object.|
fees_list ||<span style="color: red;">required</span> ||The list of fees which are fixed price charged for a payment.|
payment_method ||<span style="color: red;">required</span> || The payment method that used in payment. |
payment_gateway ||<span style="color: red;">required</span> || Payment gateway used in payment |
customer_id ||<span style="color: red;">required</span> || Unique identifier for the user oject. |
invoice_id ||<span style="color: red;">required</span> || Unique identifier for the invoice object. |

### Returns

Returns the refund object. Status in refund object will be in pending state.

<aside class="notice">
Default value of refund is equal to payment value.
</aside>

<aside class="notice">
The error code used when you fail to request refund is <a href="#9112">9112</a>
</aside>

######################################################################################

## Reject a refund

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d refund_id=4
     'http://www.example.com/refund/reject_refund'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully rejected a refund",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "request_date": "2022-10-12",
	 "refund_date": "2022-10-12",
	 "value": 1,
	 "payment_id": 1,
	 "fees_list": [],
	 "payment_method": [],
	 "status": "rejected",
	 "customer": null
	}
}
```
Returns refund object with rejected status.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
refund_id ||<span style="color: red;">required</span> || Unique identifier for the refund object. |

### Returns

Returns the rejected refund object if a valid ID was provided. Returns an error otherwise.

######################################################################################

## Approve a refund

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d refund_id=4
     'http://www.example.com/refund/approve_refund'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully approved a refund",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "request_date": "2022-10-12",
	 "refund_date": "2022-10-12",
	 "value": 1,
	 "payment_id": 1,
	 "fees_list": [],
	 "payment_method": [],
	 "status": "approved",
	 "customer": null
	}
}
```
Returns refund object with approved status.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
refund_id ||<span style="color: red;">required</span> || Unique identifier for the refund object. |

### Returns

Returns the aprroved refund object if a valid ID was provided. Returns an error otherwise. 

<aside class="notice">
Requires a % value of the full value.
</aside>

######################################################################################

## List all refunds

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_id=4
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'http://www.example.com/refund/list'
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
		"payment_id": 1,
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
		"payment_id": 2,
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
circle_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the circle object. |
customer_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the user object. |
payment_link_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the payment link object. |
payment_link_url ||<span style="color: lightblue;">optional</span> || The url of the payment link. |

### Returns

Returns refund list. If no more refunds are available, the resulting array will be empty.

<aside class="notice">
At least one input is required.
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
     'http://www.example.com/refund/get_status/{refundId}'
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
     -d name="ahmed"
     'http://www.example.com/coupon/create'
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
payment_link_id ||<span style="color: red;">required</span> || Unique identifier for the payment link object. |
value ||<span style="color: red;">required</span> || The value of the payment after discounting. |
name ||<span style="color: red;">required</span> || The name of the coupon. |
expire_date ||<span style="color: red;">required</span> || Coupon's expire date.|
number_of_users ||<span style="color: red;">required</span> || Number of users who can use the coupon. |
status ||<span style="color: red;">required</span> || The status of the coupon for example, expired. |
times_per_customer ||<span style="color: red;">required</span> || Times that customer can use the same coupon. |

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
     'http://www.example.com/coupon/get/{couponId}'
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
     -d name="ahmed"
     -d status="1"
     'http://www.example.com/coupon/update'
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
	 "status": 1,
	 "times_per_customer": 1,
	 "customer": []
	}
}
```
Updates the metadata of a coupon.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
coupon_id ||<span style="color: red;">required</span> ||Unique identifier for the coupon object.|
value ||<span style="color: red;">required</span> || The value of the payment after discounting. |
name ||<span style="color: red;">required</span> ||The name of the coupon.|
expire_date ||<span style="color: red;">required</span> ||Coupon's expire date.|
number_of_users ||<span style="color: red;">required</span> || Number of users who can use the coupon. |
status ||<span style="color: red;">required</span> ||The status of the coupon for example, expired.|
times_per_customer ||<span style="color: red;">required</span> || Times that customer can use the same coupon. |

### Returns

The newly updated coupon object if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

<aside class="notice">
The error codes used when you fail to update a coupon are <a href="#4312">4312</a> , <a href="#4112">4112</a> , <a href="#4311">4311</a> , <a href="#1110">1110</a>
</aside>

##############################################################################

## List all coupons

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'http://www.example.com/coupon/list/{paymentLinkId}'
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
		"status": 1,
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
		"status": 1,
		"times_per_customer": 1,
		"customer": []
	 }
	]
}
```
Returns a list of your coupons.

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
     -d payment_link_id=1
     -d title="title"
     'http://www.example.com/form/create'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully created a form",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
   {
	"payment_link_id": 1,
	"title": "title",
	"questions": [
		{
			"question": "question?",
			"questionType": "type",
			"editable": true,
			"mandatory": true,
			"answer": "answer",
			"options": [
				{
					"name": "question?",
					"type": "type",
					"editable": true
				},
				{
					"name": "question?",
					"type": "type",
					"editable": true
				}
			]
		},
		{
			"question": "question?",
			"questionType": "type",
			"editable": true,
			"mandatory": true,
			"answer": "answer",
			"options": [
				{
					"name": "question?",
					"type": "type",
					"editable": true
				},
				{
					"name": "question?",
					"type": "type",
					"editable": true
				}
			]
		}
	],
	"status": "pending"
  }
}
```
This endpoint helps you to create form.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_id ||<span style="color: red;">required</span> || Unique identifier for the payment link object. |
title ||<span style="color: red;">required</span> ||The title of the form.|
question_list ||<span style="color: red;">required</span> ||The list that has questions objects. |
status ||<span style="color: red;">required</span> || The status of the form for example, "pending".|

### Returns

Returns form object which has the questions array. Status is "active" by default.

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
     -d form_id=3
     'http://www.example.com/form/get'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Form object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
   {
	"payment_link_id": 1,
	"title": "title",
	"questions": [
		{
			"question": "question?",
			"questionType": "type",
			"editable": true,
			"mandatory": true,
			"answer": "answer",
			"options": [
				{
					"name": "question?",
					"type": "type",
					"editable": true
				},
				{
					"name": "question?",
					"type": "type",
					"editable": true
				}
			]
		},
		{
			"question": "question?",
			"questionType": "type",
			"editable": true,
			"mandatory": true,
			"answer": "answer",
			"options": [
				{
					"name": "question?",
					"type": "type",
					"editable": true
				},
				{
					"name": "question?",
					"type": "type",
					"editable": true
				}
			]
		}
	],
	"status": "active"
   }
}
```
Retrieves a form object.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
form_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the form object. |
payment_link_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the payment link object. |

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
     -d form_id=1
     -d title="title"
     'http://www.example.com/form/update'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully updated the form",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
   {
	"payment_link_id": 1,
	"title": "title",
	"questions": [
		{
			"question": "question?",
			"questionType": "type",
			"editable": true,
			"mandatory": true,
			"answer": "answer",
			"options": [
				{
					"name": "question?",
					"type": "type",
					"editable": true
				},
				{
					"name": "question?",
					"type": "type",
					"editable": true
				}
			]
		},
		{
			"question": "question?",
			"questionType": "type",
			"editable": true,
			"mandatory": true,
			"answer": "answer",
			"options": [
				{
					"name": "question?",
					"type": "type",
					"editable": true
				},
				{
					"name": "question?",
					"type": "type",
					"editable": true
				}
			]
		}
	],
	"status": "active"
  }
}
```
Updates details in a form object.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
form_id ||<span style="color: lightblue;">optional</span> ||Unique identifier for the form object. |
payment_link_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the payment link object. |
payment_link_url ||<span style="color: lightblue;">optional</span> || The url of the payment link.|
title ||<span style="color: lightblue;">optional</span> || The title of the form.|
questions_list ||<span style="color: lightblue;">optional</span> || The list that has questions objects.|
status ||<span style="color: lightblue;">optional</span> || The status of the form for example, "pending". |

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

## List form responses

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_id=3
     'http://www.example.com/form/list_responses'
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
payment_link_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the payment link object. |
payment_link_url ||<span style="color: lightblue;">optional</span> || The url of the payment link. |
form_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the form object. |


### Returns

Returns response object list if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
at least one attribute to be provided. 
</aside>

<aside class="notice">
The error codes used when you fail to update a coupon are <a href="#4111">4111</a> , <a href="#3110">3110</a> 
</aside>

####################################################################################

## Retrieve a specific response

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     -d payment_link_id=3
     -d customer_id=1
     'http://www.example.com/form/get_response'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "form response object returned successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "id": 1,
	 "customer": null,
	 "form": null
	}
}
```
Retrieves a specific form responses.

Parameter|Type|Required|Default|Description|
---------|--------|---------|--------|-----|
payment_link_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the payment link object. |
payment_link_url ||<span style="color: lightblue;">optional</span> || The url of the payment link. |
form_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the form object.|
customer_id ||<span style="color: lightblue;">optional</span> || Unique identifier for the user object. |

### Returns

Returns one response object if the call succeeded. Otherwise, this call returns an error.

<aside class="notice">
at least one attribute to be provided. 
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
     -d merchant_id=3
     -d settlement_id=5
     'http://www.example.com/settlements/get'
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
merchant_id ||<span style="color: red;">required</span> ||Unique identifier for the user object. |
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
     -d merchant_id=3
     -d status="pending"
     'http://www.example.com/settlements/list'
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
merchant_id ||<span style="color: red;">required</span> ||Unique identifier for the user object.|
date_time ||<span style="color: lightblue;">optional</span> ||The date time when the settlement happened. |
status ||<span style="color: lightblue;">optional</span> ||The status of the settlement for example, "pending".|

### Returns

Returns a settlement object list. The list has a separate settlement objects. If no more settlements are available, the resulting array will be empty. 

####################################################################################

## Get settlement Status

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'http://www.example.com/settlements/get_status/{settlementId}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "Settlement's status retrieved successfully",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "status": "pending"
	}
}
```
Retrieve the status of settlement.

### Parameters

No parameters.

### Returns

Returns the status of the settlement object.

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
     -d "item[name]"="book"
     -d "item[description]"="rich dad poor dad"
     -d "item[price]"=55
     'http://www.example.com/invoice/create'
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
merchant ||<span style="color: red;">required</span> || The details of the merchant.|
item ||<span style="color: red;">required</span> ||The item used in the invoice.|
item.name ||<span style="color: red;">required</span> || The item name.|
item.description ||<span style="color: red;">required</span> || The description of item. |
item.price ||<span style="color: red;">required</span> ||Item's price. |
customer ||<span style="color: red;">required</span> ||The details of the customer. |

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
     'http://www.example.com/invoice/get/{invoiceId}'
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

## Deactive an invoice

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'http://www.example.com/invoice/deactive/{invoiceId}'
```

> The above command returns JSON structured like this:

```json
{
 "status" : True,
 "message" : "You successfully deactivated an invoice",
 "isError" : False,
 "errorCode" : 0,
 "errorDetails" : "No error till now",
 "data" :
	{
	 "number": 1,
	 "merchant": 1,
	 "customer": 1,
	 "status": "deactivated",
	 "due_date": "2022-10-12"
	}
}
```
Deactivate the invoice with the given id.

### Parameters

No parameters.

### Returns

Returns the deactivated invoice object if a valid invoice ID was provided. Returns an error otherwise.

####################################################################################

## Settle an invoice

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'account_key: de40f1f2-98a8-32bd-bc2c-96280c7b4b6b'
	 --header 'account_token: Bearer eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0J'
     'http://www.example.com/invoice/settle_invoice/1'
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