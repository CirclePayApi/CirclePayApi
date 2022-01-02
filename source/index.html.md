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

To process online transactions, you will need both a payment gateway and a payment processor. 

<span style="color: red">Payment Gateway</span>: is the beginning and end of the transaction, where the customer will enter their credit card information and receive an approval or denial of the transaction. 

<span style="color: red">Payment Processor</span>: moves the information between the customer’s bank and the merchant acquirer, or acquiring bank. 

<aside class="notice">
Every transaction processed online needs <span style="color: red">both</span> payment gateway and payment processor.
</aside>

<img src="https://devathon.com/wp-content/uploads/2020/02/Patement-gateway-process-Devathon.png" >

## List Payment Gateways

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/LIST_PAYMENTGATEWAY'
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

This endpoint retrieves all payment gateway to the merchant.

### HTTP Request

`GET http://example.com/LIST_PAYMENTGATEWAY`

### No Parameters

## Get a Specific Payment Gateway

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d '{"1",2}'
     'http://www.example.com/GET_PAYMENTGATEWAY'
```

> The above command returns JSON structured like this:

```json
{
	"id": 1,
	"name": "ahmed",
	"payment_methods": []
}
```

This endpoint retrieves a specific payment gateway.

### HTTP Request

`POST http://example.com/GET_PAYMENTGATEWAY`

### Request Body Model

 <code>{<br>
   &nbsp;gateway_id (string, optional),<br>
   &nbsp;user_id (integer, optional)<br>
 }</code>

 <h3>Request Body Example</h3>

 <code>{<br>
   &nbsp;gateway_id: "1",<br>
   &nbsp;user_id: 2<br>
 }</code>

# Payment Methods

<span style="color: red">Payment Method</span>: is a way that customers pay for a product or service. CirclePay gives customers the freedom to choose between payment methods like: cash, credit cards, prepaid cards, debit cards, or mobile payments.

<aside class="notice">
CirclePay supports these payment methods:

<ul>
  <li>paymob</li>
  <li>fawry</li>
  <li>myFatoorah</li>
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
</aside>

## List Payment Methods

```shell
curl -X GET --header 'Accept: application/json'
     --header 'Content-Type: application/json'
     --header 'access-token: Bearer'
     'http://www.example.com/LIST_PAYMENTMETHOD/1'
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

This endpoint retrieves all payment methods of the merchant.

### HTTP Request

`GET http://example.com/LIST_PAYMENTMETHOD/<merchantId>`

### URL Parameters

Parameter | Description
---------| -----------
merchantId | The ID of the merchant to retrieve

## Get a Specific Payment Method

```shell
curl -X POST --header 'Content-Type: application/json'
     --header 'Accept: application/json'
     --header 'access-token: Bearer'
     -d '{"1",2}'
     'http://www.example.com/GET_PAYMENTMETHOD'
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

This endpoint retrieves a specific payment method.

### HTTP Request

`POST http://example.com/GET_PAYMENTGATEWAY`

### Request Body Model

 <code>{<br>
   &nbsp;gateway_id (string, optional),<br>
   &nbsp;user_id (integer, optional)<br>
 }</code>

 <h3>Request Body Example</h3>

 <code>{<br>
   &nbsp;gateway_id: "1",<br>
   &nbsp;user_id: 2<br>
 }</code>





