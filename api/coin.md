# currency/coin

> Get list of available cryptocurrencies.
>
> You can use these currencies at payment receive or send \(source\_coin\_id or pay\_coin\_id\).
>
> Turn on/off at [https://cubepay.io](https://cubepay.io) &gt;&gt; Dashboard &gt;&gt; Coins

{% api-method method="post" host="API\_URL" path="/currency/coin" %}
{% api-method-summary %}
Get available cryptocurrencies
{% endapi-method-summary %}

{% api-method-description %}
**Response**  
  
`id` : Identity of coin.  
  
`symbol` : Symbol of coin.  
  
`name` : Coin name.`image` : Coin image \(64 pixel \* 64 pixel\)  
  
`description` : Description of coin.  
  
`fee_coin_id` : The coin id charge for fee \(Every customized ERC-20 token charge fee by ETH\).  
  
`fee` : The percentage of income will charge by fee\_coin\_id.  
  
`min_fee` : The min amount of fee will be charge when the income coin less than the value.
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
        "1": {
            "id": 1,
            "symbol": "ETH",
            "name": "Ether",
            "image": "http://common.cubepay.io/uploads/coin/1533198049.png",
            "description": "Ether",
            "fee_coin_id": 1,
            "fee": 2,
            "min_fee": 0.003
        },
        "2": {
            "id": 2,
            "symbol": "BTC",
            "name": "BitCoin",
            "image": "http://common.cubepay.io/uploads/coin/1533198036.png",
            "description": "BitCoin",
            "fee_coin_id": 2,
            "fee": 3,
            "min_fee": 0.0002
        },
        "3": {
            "id": 3,
            "symbol": "USDT",
            "name": "USDT",
            "image": "http://common.cubepay.io/uploads/coin/1534500017.png",
            "description": "USDT",
            "fee_coin_id": 3,
            "fee": 3,
            "min_fee": 0.3
        },
        "4": {
            "id": 4,
            "symbol": "LTC",
            "name": "LiteCoin",
            "image": "http://common.cubepay.io/uploads/coin/1535690747.png",
            "description": "",
            "fee_coin_id": 4,
            "fee": 2,
            "min_fee": 0.002
        },
        "502": {
            "id": 502,
            "symbol": "TOKEN1",
            "name": "Token1 Test",
            "image": "http://common.cubepay.io/images/coin.png",
            "description": "",
            "fee_coin_id": 1,
            "fee": 2,
            "min_fee": 0.003
        }
    },
    "status": 200
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

