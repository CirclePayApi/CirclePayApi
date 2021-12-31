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

A payment gateway is a technical backend service processing payments in online transactions. it acts as an interface between the <span style="color: red">payment processor</span>, the merchant and the acquiring bank, besides informing the customer about their purchase's status.

<aside class="notice"><span style="color: red">Payment processor</span>: is the entity that will facilitate the entire process, it responsible for the money collection and for depositing that money into the seller's account.
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
