# currency/fait

> Get list of available fiat currencies.
>
> You can **only** use these fiat currencies for your product's original list price, not for receive/send.
>
> We'll convert value by exchange rate between currency of list price and currency of actual paid.

{% api-method method="post" host="API\_URL" path="/currency/fiat" %}
{% api-method-summary %}
Get available fiat currencies
{% endapi-method-summary %}

{% api-method-description %}
**Response**  
  
`id` : Identity of coin.  
  
`symbol` : Symbol of coin.  
  
`name` : Coin name.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="client\_id" type="string" required=true %}
Client ID of the merchant.
{% endapi-method-parameter %}

{% api-method-parameter name="sign" type="string" required=true %}
Sign string hash by client\_id and other parameters.
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "data": {
        "300": {
            "id": 300,
            "symbol": "AED",
            "name": "United Arab Emirates Dirham"
        },
        "301": {
            "id": 301,
            "symbol": "AFN",
            "name": "Afghan Afghani"
        },
        "302": {
            "id": 302,
            "symbol": "ALL",
            "name": "Albanian Lek"
        },
        "303": {
            "id": 303,
            "symbol": "AMD",
            "name": "Armenian Dram"
        }
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

