# payment/coin

> Initial order with specific coin and amount that customer use to pay.
>
> Order will expire after 6 hours.
>
> We provide refund function on [https://cubepay.io](https://cubepay.io) &gt;&gt; Dashboard &gt;&gt; Payments\(but you can't get back the send coin if you had defined\).
>
> If the coin is your customize ERC-20 token, make sure you have enough blance of ETH for payment fee\(See [_**currency/coin**_](coin.md) response\), we'll lock the fee temporarily and unlock until payment finish or expired.
>
> When you define the parameter _send\_coin\_id_, _receive\_address_, _send\_amount_ to send back coin to your customer, we'll lock the amount of send coin and fee temporarily and unlock until payment finish or expired. It will consider two situations:
>
> * Send coin is official coin\(not customize ERC-20 token\) : we'll lock  `send back amount of the official coin + min fee of official`
> * Send coin is customize ERC-20 token : we'll lock `send back amount of the customize ERC-20 token + min fee of ETH`

{% api-method method="post" host="API\_URL" path="/payment/coin" %}
{% api-method-summary %}
Init payment with specific coin
{% endapi-method-summary %}

{% api-method-description %}
**Response**  
  
See _**payment/query**_ response
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="coin\_id" type="string" required=true %}
Coin id you want receive.  
Get the id from API _**currency/coin**_.
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
Client ID of the merchant.
{% endapi-method-parameter %}

{% api-method-parameter name="sign" type="string" required=true %}
Sign string hash by client\_id and other parameters.
{% endapi-method-parameter %}

{% api-method-parameter name="source\_coin\_id" type="string" required=true %}
Coin id of your original list price.  
Get the id from API _**currency/coin**_ or _**currency/fiat**_
{% endapi-method-parameter %}

{% api-method-parameter name="source\_amount" type="string" required=true %}
original list price of your product.  
must be postive number and large then zero.
{% endapi-method-parameter %}

{% api-method-parameter name="item\_name" type="string" required=true %}
The customize name of your item.
{% endapi-method-parameter %}

{% api-method-parameter name="merchant\_transaction\_id" type="string" required=true %}
Transaction ID generated by your shop.  
Recommend be unique.
{% endapi-method-parameter %}

{% api-method-parameter name="other" type="string" required=false %}
Other information you can pass to the payment, such as your member id, your product id or anything you want....We'll return the field for your at IPN\_URL.
{% endapi-method-parameter %}

{% api-method-parameter name="return\_url" type="string" required=false %}
The url you want your customer back to. it will show a link button on the coin pay page.
{% endapi-method-parameter %}

{% api-method-parameter name="ipn\_url" type="string" required=false %}
The notify url . When the payment finish\(only success\), we'll sending a request within transaction information by **POST** method.The parameter we sending see _**payment/query**_.You should synchronize your order according our notify, and response a string `success` tell as you have receive, else we'll notify continue up to 10 times.
{% endapi-method-parameter %}

{% api-method-parameter name="send\_coin\_id" type="string" required=false %}
Coin id you want to send back to your customer, we'll send this coin to **receive\_address** you define.If you pass value on send\_coin\_id, you should pass value on receive\_address and send\_amount too.
{% endapi-method-parameter %}

{% api-method-parameter name="receive\_address" type="string" required=false %}
Coin address you want to send back to your customer.
{% endapi-method-parameter %}

{% api-method-parameter name="send\_amount" type="string" required=false %}
Coin amount you want to send back to your customer.Must be postive number and large then zero, and make sure you have enough amout\(amount you want to send back and fee\) of the send coin.
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
        "id": "C1536678153791231775",
        "status": 0,
        "status_message": "unpaid",
        "pay_url": "http://cubepay.io/payment/pay?id=C1536678153791231775",
        "pay_info": {
            "coin": {
                "id": 2,
                "symbol": "BTC",
                "name": "BitCoin",
                "image": "http://common.cubepay.io/uploads/coin/1533198036.png",
                "description": "BitCoin"
            },
            "address": "2N8iLSfdFv7GRXoNxtSgMmA1e9BQHyU1PzB",
            "qrcode": "http://common.cubepay.io/tool/qrcode/2N8iLSfdFv7GRXoNxtSgMmA1e9BQHyU1PzB.png",
            "amount": 0.00251098,
            "paid_amount": 0,
            "merchant_transaction_id": "M12345678",
            "item_name": "Test item name",
            "source_coin": {
                "id": 443,
                "symbol": "TWD",
                "name": "New Taiwan Dollar",
                "image": "http://common.cubepay.io/images/coin.png",
                "description": null
            },
            "source_amount": 500,
            "rate": 199124.20804479,
            "send_coin": [],
            "send_amount": 0,
            "receive_address": null
        },
        "refund": null
    },
    "status": 200
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}
