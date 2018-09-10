# CubePay API Document

CubePay's API makes it easy to receive or send cryptocurrency by BTC, ETH , LTC and customized ERC-20 token. 
More info at https://cubepay.io

## Getting Start

Get **client\_id** and **client\_key** on [https://cubepay.io](https://cubepay.io) &gt;&gt; Account Setting


## The URL to the API service

* Live. [https://api.cubepay.ioSandbox](https://api.cubepay.ioSandbox)
* Sandbox. [https://api.sandbox.cubepay.io](https://api.sandbox.cubepay.io)


## Request

All API request with parameter using **POST** method**.**

All API most have parameters **client\_id** and **sign**. more about Authentication.

{% method %}

## Response

All API response process status with standard [HTTP Status Code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) in header,  and with JSON format like below: 

{% common -%}

status : status code, 200 means process success and the others code means error.

data : a structure with relation information if success, else there will content error message.

```text
{
data: "missing client_id",
status: 401
}
```

{% endmethod %}

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

{% method %}

1.Ascending sort your parameters by parameter's name, and join to a string format in [Pattern of Query String](https://en.wikipedia.org/wiki/Query_string).

{% common %}

Example

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250
```

{% endmethod %}

{% method %}

2.Put **client\_key={your client key}** to the end of string.

{% common %}

Example

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_key=exampleclientkey
```
{% endmethod %}

{% method %}

3.Hash String by **Sha-256**

{% common %}

```text
SHA256(akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_key=exampleclientkey)
=
ca3f40ae95c5dc7cd89259746d2c2476f600e9c914ac2d35f6510aadb39a1364
```
{% endmethod %}

4.String to uppercase

{% method %}

{% common %}
Example

```text
sign=CA3F40AE95C5DC7CD89259746D2C2476F600E9C914AC2D35F6510AADB39A1364
```
{% endmethod %}

5.Attach **sign** to parameter

