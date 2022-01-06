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

# Gateway

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
     --header 'access-token: Bearer'
     'http://www.example.com/gateway/list_paymentgateway'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves all payment gateways to the merchant.

### Parameters

No parameters.

### Returns

Returns payment gateway list.

########################################################################

## Retrieve a Payment Gateway

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d gateway_id="2"
     -d user_id=1
     'http://www.example.com/gateway/get_paymentgateway'
```

> The above command returns JSON structured like this:

```json
{
	"id": 1,
	"name": "ahmed",
	"payment_methods": []
}
```

Retrieves a specific payment gateway.

### Parameters

          |          |
--------- | ---------|
gateway_id <sub style="color: lightblue;">optional</sub> | The id of payment gateway. |
user_id <sub style="color: lightblue;">optional</sub> |  The id of the merchant.|

### Returns
Return a payment gateway object.

##############################################################################

# Payment Methods

<span style="color: red">A payment method</span> is a way that customers pay for a product or service. CirclePay gives customers the freedom to choose between payment methods like: cash, credit cards, prepaid cards, debit cards, or mobile payments.


CirclePay supports these payment methods:

<ul>
  <li>meeza</li>
  <li>valu</li>
  <li>VodavoneCash</li>
  <li>etisalatCash</li>
  <li>orangeCash</li>
  <li>PREMIUM CARD</li>
  <li>Visa</li>
  <li>MasterCard</li>
  <li>SADAD</li>
  <li>mada</li>
  <li>ApplePay</li>
  <li>Knet</li>
  <li>American express</li>
</ul>


<aside class="notice">Paymob, Fawry, MyFatoorah are payment gateways. 

Each of these payment gateways are supporting a number of payment methods. So, a payment method won't be available unless you enable the corresponding payment gateway.
</aside>

## List a Payment Methods

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/payment_methods/list_paymentmethod/1'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves all payment methods of the merchant.

### Parameters

No parameters.

### Returns

Returns a payment channel list.

#################################################################################

## Retrieve a Payment Method

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d gateway_id="2"
     -d user_id=1
     'http://www.example.com/payment_methods/get_paymentmethod'
```

> The above command returns JSON structured like this:

```json
{
	"id": 1,
	"name": "ahmed",
	"type": "card",
	"gateway": "paymob",
	"rate": 1
}
```

Retrieves a specific payment method.

### Parameters

          |          |
--------- | ---------|
gateway_id <sub style="color: lightblue;">optional</sub> | The id of payment gateway. |
user_id <sub style="color: lightblue;">optional</sub> |  The id of the merchant.|

### Returns

Returns a payment channel object.

###########################################################################################

# Merchants

<span style="color: red">Merchant</span> is the person or company engaged in the business of selling products or services. For example, wholesaler or retail store owner.

## Create a Merchant

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d "first_name": "Ahmed"
     -d "last_name": "Khaled"
     -d "email": "ahmedkahled@gmail.com"
     -d "phone_number": "923847"
     'http://www.example.com/merchants/create'
```

> The above command returns JSON structured like this:

```json
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
```

This endpoint helps you to create new merchant.

### Parameters

          |          |
--------- | ---------|
first_name <sub style="color: red;">required</sub> |            |
last_name <sub style="color: red;">required</sub> |             |
email <sub style="color: red;">required</sub>  |                |
phone_number <sub style="color: red;">required</sub> |          |
picture <sub style="color: lightblue;">optional</sub> |              |
id_card <sub style="color: lightblue;">optional</sub> |              |
billing_info <sub style="color: lightblue;">optional</sub> |         |
documents <sub style="color: lightblue;">optional</sub> |            |
business_individual <sub style="color: lightblue;">optional</sub> |  |
type_of_business <sub style="color: lightblue;">optional</sub> |     |

### Returns

Returns the user object if the update succeeded. Returns an error if create parameters are invalid.

########################################################################################

## Retrieve a Merchant

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d user_id=2
     'http://www.example.com/merchants/get'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves a specific merchant.

### Parameters

          |          |
--------- | ---------|
user_id <sub style="color: lightblue;">optional</sub> |            |

### Returns

Returns the user object for a valid identifier.

#################################################################################

## Update a Merchant

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/merchants/update'
```

> The above command returns JSON structured like this:

```json
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
```

Updates the specified merchant by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

### Parameters

          |          |
--------- | ---------|
user_id <sub style="color: red;">required</sub> |            |
first_name <sub style="color: red;">required</sub> |             |
last_name <sub style="color: red;">required</sub>  |                |
email <sub style="color: red;">required</sub> |          |
phone_number <sub style="color: red;">required</sub> |              |
picture <sub style="color: lightblue;">optional</sub> |              |
id_card <sub style="color: lightblue;">optional</sub> |         |
billing_info <sub style="color: lightblue;">optional</sub> |            |
documents <sub style="color: lightblue;">optional</sub> |  |
business_individual <sub style="color: lightblue;">optional</sub> |     |
type_of_business <sub style="color: lightblue;">optional</sub> |     |
payment_methods <sub style="color: lightblue;">optional</sub> |     |
circles <sub style="color: lightblue;">optional</sub> |     |

### Returns

Returns the user object if the update succeeded. Returns an error if update parameters are invalid


#################################################################################

## List all merchants

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/merchants/list'
```

> The above command returns JSON structured like this:

```json
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
     --header 'access-token: Bearer'
     -d user_id=1
     'http://www.example.com/merchants/list_documents'
```

> The above command returns JSON structured like this:

```json
{
	"id": "124234",
	"name": "national id",
  "size": 7969,
  "upload_state": "success",
  "last_update": 23-3-2022
},
{
	"id": "12434234",
	"name": "passport",
  "size": 7969,
  "upload_state": "success",
  "last_update": 21-1-2022
}
```

Retrieves all merchants' documents.

### Parameters

          |          |
--------- | ---------|
user_id <sub style="color: lightblue;">optional</sub> |            |

### Returns

Returns a document list.

####################################################################################

## Upload documents

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d "document_list[id]"="124234" \
     -d "document_list[name]"="national id" \
     -d "document_list[size]"=7969 \
     'http://www.example.com/merchants/upload_documents?user_id=2'
```

> The above command returns JSON structured like this:

```json
{  
  "title":"success",
  "message":"Documents Uploaded successfully",
  "status":"200"
}
```

To upload a file, The request should contain the document you would like to upload, as well as the parameters for creating a document.

### Parameters

          |          |
--------- | ---------|
user_id  |            |
document_list  |            |
document_list.id  |            |
document_list.name  |            |
document_list.size  |            |
document_list.upload_state  |            |
document_list.last_update  |            |

### Returns

Returns success message if document uploaded.

###########################################################################

## Enable gateway

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d user_id=2
     -d gateway_id="4"
     'http://www.example.com/merchants/enable_gateway'
```

> The above command returns JSON structured like this:

```json
{  
  "title":"success",
  "message":"Gateway enabled successfully",
  "status":"200"
}
```

This endpoint enable specific gateway.

### Parameters

          |          |
--------- | ---------|
user_id  |            |
gateway_id  |            |

### Returns

Returns success message if gateway enabled.

####################################################################################

## Disable gateway

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/merchants/disable_gateway'
```

> The above command returns JSON structured like this:

```json
{  
  "success":"The following payment gateways and payment methods got disabled",
  "payment_gateway": {
    "name": "paymob",
    "id": 1
  }
  "payment_channels":[ 
  {
    "name": "payment channel-1",
    "id": 2
  },
  {
    "name": "payment channel-2",
    "id": 3
  }
  ]
}
```

This endpoint disable specific gateway and it's related payment methods.

### Parameters

No parameters.

### Returns

Returns success message if gateway disabled.

####################################################################################

## Enable payment method

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d user_id=2
     -d gateway_id="4"
     'http://www.example.com/merchants/enable_payment_method'
```

> The above command returns JSON structured like this:

```json
{  
  "title":"success",
  "message":"The following payment method has been enabled",
  "status":"200"
}
```

This endpoint enable specific payment method.

### Parameters

          |          |
--------- | ---------|
user_id  |            |
gateway_id  |            |

### Returns

Returns success message if payment method enabled.

#######################################################################################

## Disable payment method

```shell
curl -X PUT --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/merchants/disable_payment_method'
```

> The above command returns JSON structured like this:

```json
{  
  "title":"success",
  "message":"The following payment method has been disabled",
  "status":"200"
}
```

This endpoint disable specific payment method.

### Parameters

          |          |
--------- | ---------|
user_id  |            |
gateway_id  |            |

### Returns

Returns success message if payment method disabled.

#######################################################################################

## List payment methods

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/merchants/list_payment_methods'
```

> The above command returns JSON structured like this:

```json
{
 "payment_channels":[ 
  {
    "name": "payment channel-1",
    "id": 2
  },
  {
    "name": "payment channel-2",
    "id": 3
  }
]
}
```

This endpoint list payment methods of the merchant.

### Parameters

          |          |
--------- | ---------|
user_id  |            |

### Returns

Returns a payment channel list.

########################################################################################

## Set Alert

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d user_id=2
     -d note=""
     'http://www.example.com/merchants/set_alert'
```

> The above command returns JSON structured like this:

```json
{  
  "message":"The user has been flagged. CirclePay admins shall investigate this customer"
}
```

This endpoint flag the user.

### Parameters

          |          |
--------- | ---------|
user_id  |            |
note  |            |

### Returns

Returns a message to inform you if the user flagged or not.

####################################################################################











