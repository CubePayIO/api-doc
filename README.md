---
description: >-
  CubePay's API makes it easy to receive or send cryptocurrency by BTC, ETH ,
  LTC and customized ERC-20 token. More info at https://cubepay.io
---

# API Document

## Start

Get **client\_id** and **client\_key** on [https://cubepay.io](https://cubepay.io) &gt;&gt; Account Setting

## The URL to the API service

* Live. [https://api.cubepay.ioSandbox](https://api.cubepay.ioSandbox)
* Sandbox. [https://api.sandbox.cubepay.io](https://api.sandbox.cubepay.io)

## Request

All API request with parameter using **POST** method**.**

All API most have parameters **client\_id** and **sign**. more about Authentication.

## Response

All API response process status with standard [HTTP Status Code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) in header,  and with JSON format like below: 

```text
{
data: "missing client_id",
status: 401
}
```

status : status code, 200 means process success and the others code means error.

data : include a structure with relation information if success, else there will content error message.

## Status Code and message

| status code | message |
| :--- | :--- |
| 200 | success |
| 400 | process error |
| 401 | authentication fail |
| 404 | not found |
| 500 | fatal error |

## Authentication

Generate a **sign** string follow these step :

1.Get **client\_id** and **client\_key** on [https://cubepay.io](https://cubepay.io) &gt;&gt; Account Setting.

2.Ascending sort your parameters by parameter's name.

3.Ascending sort your parameters by parameter's name, and join to a string format in [Pattern of Query String](https://en.wikipedia.org/wiki/Query_string).  for example:

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250
```

4.Put **client\_key={your client key}** to the end of string. The string should look lik:

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_key=exampleclientkey
```

5.Hash String by **Sha-256**

```text
SHA256(akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_key=exampleclientkey)
=
ca3f40ae95c5dc7cd89259746d2c2476f600e9c914ac2d35f6510aadb39a1364
```

6.String to uppercase

```text
sign=CA3F40AE95C5DC7CD89259746D2C2476F600E9C914AC2D35F6510AADB39A1364
```

7.Attach **sign** to parameter

