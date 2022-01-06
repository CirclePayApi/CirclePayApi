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

# Customers

## Retrieve a customer

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/customers/get/1'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves a specific customer.

### Parameters

No parameters.

### Returns

Returns the Customer object for a valid identifier.

####################################################################################

## List all customers

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d user_id=2
     'http://www.example.com/customers/list'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves a list of your customers.

### Parameters

          |          |
--------- | ---------|
user_id  |            |
circle_id <sub style="color: lightblue;">optional</sub> |            |

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
     --header 'access-token: Bearer'
     -d "value": 0
     -d "currency": "EGP"
     -d "description": "payment link"
     -d "expire_date": "1-22-2022"
     'http://www.example.com/payment_link/create'
```

> The above command returns JSON structured like this:

```json
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
```

This endpoint helps you to create payment link.

### Parameters

          |          |
--------- | ---------|
value <sub style="color: red;">required</sub> |            |
currency <sub style="color: red;">required</sub> |             |
description <sub style="color: red;">required</sub>  |                |
expire_date <sub style="color: red;">required</sub> |          |
payment_method_id <sub style="color: lightblue;">optional</sub> |              |
status <sub style="color: lightblue;">optional</sub> |              |
circle_id <sub style="color: lightblue;">optional</sub> |         |
fees_list <sub style="color: lightblue;">optional</sub> |            |

### Returns

Returns the payment link object.

####################################################################################

## Retrieves a payment link

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d "payment_link_id": 4
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd" 
     'http://www.example.com/payment_link/get'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves a specific payment link.

### Parameters

          |          |
--------- | ---------|
payment_link_id <sub style="color: lightblue;">optional</sub> |         |
payment_link_url <sub style="color: lightblue;">optional</sub> |         |

### Returns

Returns the payment link object.

####################################################################################

## Update a payment link

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d "payment_link_id": 3
     -d "payment_link_url": "https://buy.circlepay.ai/sldkfhsd"
     'http://www.example.com/payment_link/update'
```

> The above command returns JSON structured like this:

```json
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
```
This endpoint helps you to udpate payment link.

### Parameters

          |          |
--------- | ---------|
payment_link_id <sub style="color: red;">required</sub> |            |
payment_link_url <sub style="color: red;">required</sub> |             |
value <sub style="color: lightblue;">optional</sub> |              |
description <sub style="color: lightblue;">optional</sub> |              |
expire_date <sub style="color: lightblue;">optional</sub> |         |
payment_method_id <sub style="color: lightblue;">optional</sub> |            |
status <sub style="color: lightblue;">optional</sub> |         |
fees_list <sub style="color: lightblue;">optional</sub> |            |

### Returns

Returns the payment link object.

#################################################################################

## List all payment links

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d "circle_id": 4
     'http://www.example.com/payment_link/list'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves all payment links.

### Parameters

          |          |
--------- | ---------|
circle_id |         |

<aside class="notice">
Select the fields you want to retrieve.
</aside>

### Returns

Returns payment link list which is array contains payment link objects. If no payment links are available, the resulting array will be empty.


####################################################################################

# Payment

## Get a payment 

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/payment/get/1'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves the details of an existing payment.

### Parameters

No parameters.

### Returns

Returns a payment object if a valid identifier was provided, and returns an error otherwise.

######################################################################################

## List all payments

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d "payment_id": 4
     'http://www.example.com/payment/list'
```

> The above command returns JSON structured like this:

```json
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
```

Retrieves all payments.

### Parameters

          |          |
--------- | ---------|
payment_id |         |

### Returns

Returns a payment list which has the details of the payment like: status, amount paid and payment method.

######################################################################################

# Refund

Allows you to refund a charge that has previously been created but not yet refunded.

## Request a refund

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d value=54
     -d currency="EGP"
     'http://www.example.com/refund/request_refund'
```

> The above command returns JSON structured like this:

```json
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
```
This endpoint helps you to request refund.

### Parameters

          |          |
--------- | ---------|
refund_id <sub style="color: red;">required</sub> |            |
value <sub style="color: red;">required</sub> |             |
currency <sub style="color: red;">required</sub> |              |
payment_id <sub style="color: red;">required</sub> |              |
fees_list <sub style="color: red;">required</sub> |         |
payment_method <sub style="color: red;">required</sub> |            |
payment_gateway <sub style="color: red;">required</sub> |         |
customer_id <sub style="color: red;">required</sub> |            |
invoice_id <sub style="color: red;">required</sub> |            |

### Returns

Returns the refund object. Status in refund object will be in pending state.

######################################################################################

## Reject a refund

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d refund_id=4
     'http://www.example.com/refund/reject_refund'
```

> The above command returns JSON structured like this:

```json
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
```
Returns refund object with rejected status.

### Parameters

          |          |
--------- | ---------|
refund_id <sub style="color: red;">required</sub> |            |

### Returns

Returns the rejected refund object if a valid ID was provided. Returns an error otherwise. 

######################################################################################

## Approve a refund

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     -d refund_id=4
     'http://www.example.com/refund/approve_refund'
```

> The above command returns JSON structured like this:

```json
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
```
Returns refund object with approved status.

### Parameters

          |          |
--------- | ---------|
refund_id <sub style="color: red;">required</sub> |            |

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
     --header 'access-token: Bearer'
     -d payment_link_id=4
     -d payment_link_url="https://buy.circlepay.ai/sldkfhsd"
     'http://www.example.com/refund/list'
```

> The above command returns JSON structured like this:

```json
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
```
List refund objects.

### Parameters

          |          |
--------- | ---------|
circle_id <sub style="color: lightblue;">optional</sub> |            |
customer_id <sub style="color: lightblue;">optional</sub> |            |
payment_link_id <sub style="color: lightblue;">optional</sub> |            |
payment_link_url <sub style="color: lightblue;">optional</sub> |            |

### Returns

Returns refund list. If no more refunds are available, the resulting array will be empty.

<aside class="notice">
At least one input is required.
</aside>

#######################################################################################

## Get refund status

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/refund/get_status/2'
```

> The above command returns JSON structured like this:

```json
{
  "status":"pending"
}
```
Retrieves the status of refund object.

### Parameters

No parameters.

### Returns

Returns the status of refund object, for example: "approved", "pending" or "rejected".

##############################################################################

# Coupon

## Create a coupon

```shell
curl -X POST --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/coupon/create'
```

> The above command returns JSON structured like this:

```json
{
	"payment_link_id": 1,
	"code": 1,
	"value": 1,
	"name": "ahmed",
	"number_of_uses": 1,
	"discount_t": ""
}
```
This endpoint helps you to create coupon.

### Parameters

          |          |
--------- | ---------|
payment_link_id <sub style="color: red;">required</sub> |            |
value <sub style="color: red;">required</sub> |            |
name <sub style="color: red;">required</sub> |            |
expire_date <sub style="color: red;">required</sub> |            |
number_of_users <sub style="color: red;">required</sub> |            |
status <sub style="color: red;">required</sub> |            |
times_per_customer <sub style="color: red;">required</sub> |            |

### Returns

Returns the coupon object. Status of coupon is "active" by default.

##############################################################################

## Retrieve a coupon

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/coupon/get/1'
```

> The above command returns JSON structured like this:

```json
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
```
Retrieves a specific coupon.

### Parameters

No parameters.

### Returns

Returns a coupon if a valid coupon Id was provided. Returns an error otherwise.

##############################################################################

## Update a coupon

```shell
curl -X PUT --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/coupon/update'
```

> The above command returns JSON structured like this:

```json
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
```
Updates the metadata of a coupon.

### Parameters

          |          |
--------- | ---------|
coupon_id <sub style="color: red;">required</sub> |            |
value <sub style="color: red;">required</sub> |            |
name <sub style="color: red;">required</sub> |            |
expire_date <sub style="color: red;">required</sub> |            |
number_of_users <sub style="color: red;">required</sub> |            |
status <sub style="color: red;">required</sub> |            |
times_per_customer <sub style="color: red;">required</sub> |            |

### Returns

The newly updated coupon object if the call succeeded. Otherwise, this call returns an error, such as if the coupon has been deleted.

##############################################################################

## List all coupons

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/coupon/list/2'
```

> The above command returns JSON structured like this:

```json
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
```
Returns a list of your coupons.

### Parameters

No parameters.

### Returns

Returns list of coupons objects. Each entry in the list is a separate coupon object. If no more coupons are available, the resulting array will be empty. This request should never return an error.

##############################################################################











