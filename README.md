# Introduction

CubePay's API makes it easy to receive or send cryptocurrency by BTC, ETH , LTC and customized ERC-20 token. More info at [https://cubepay.io](https://cubepay.io)

## Getting Start

Get `client_id` and `client_secret` on [https://cubepay.io](https://cubepay.io) &gt;&gt; Account Setting

## The URL to the API service

* Live. [https://api.cubepay.ioSandbox](https://api.cubepay.ioSandbox)
* Sandbox. [https://api.sandbox.cubepay.io](https://api.sandbox.cubepay.io)

## Request

All API request with parameter using **POST** method and most have parameters `client_id` and `sign`. more about Authentication.

## Response

All API response process status with standard [HTTP Status Code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) in header, and with JSON format like below:

status : status code, 200 means process success and the others code means error.

data : a structure with relation information if success, else there will content error message.

```text
{
data: "missing client_id",
status: 401
}
```

## Status Code and message

| status code | message |
| :--- | :--- |
| 200 | success |
| 400 | process error |
| 401 | authentication fail |
| 404 | not found |
| 500 | fatal error |

## Authentication

Generate `sign` follow these step :

1. Ascending sort your parameters by parameter's name, and join to a string format in [Pattern of Query String](https://en.wikipedia.org/wiki/Query_string).

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=300&wkey3=250
```

2. Put `client_secret={your client secret}` to the end of string.

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_secret=exampleclientsecret
```

3. Hash String by **Sha-256**

```text
SHA256(akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_key=exampleclientkey)
=
ca3f40ae95c5dc7cd89259746d2c2476f600e9c914ac2d35f6510aadb39a1364
```

4. String to uppercase and you'll get the signature finally.

```text
sign=CA3F40AE95C5DC7CD89259746D2C2476F600E9C914AC2D35F6510AADB39A1364
```

5. Append `sign` to **POST** parameter and sending,  not need in sequence, it'll look like

```text
ekey1=100
akey=100
wkey3=250
client_id=exampleclientid
ekey2=300
sign=CA3F40AE95C5DC7CD89259746D2C2476F600E9C914AC2D35F6510AADB39A1364
```



