# Introduction

CubePay's API makes it easy to receive or send cryptocurrency by BTC, ETH , LTC and customized ERC-20 token. More info at [https://cubepay.io](https://cubepay.io)

## Getting Start

Get **client\_id** and **client\_key** at [https://cubepay.io](https://cubepay.io) &gt;&gt; Dashboard &gt;&gt; Account Setting

## The URL to the API service

* Live. [https://api.cubepay.io](https://api.cubepay.ioSandbox)
* Sandbox. [https://api.sandbox.cubepay.io](https://api.sandbox.cubepay.io)

## Request

All request with Form Data Parameters using **POST** method and most have parameters **client\_id** and **sign** \(all request need to auth\). more about [Authentication](authentication.md).

## Response

API return process status with standard [HTTP Status Code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) in header, and with JSON format like below:

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



