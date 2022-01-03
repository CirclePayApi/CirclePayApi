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

<span style="color: red">A payment method</span> is a way that customers pay for a product or service. CirclePay gives customers the freedom to choose between payment methods like: cash, credit cards, prepaid cards, debit cards, or mobile payments.


<h3>CirclePay supports these payment methods:</h3>

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





