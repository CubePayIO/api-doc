# Authentication

Generate **sign** string follow these step :

1. Ascending sort your form data parameters by parameter's key name, and join to a string format in [Pattern of Query String](https://en.wikipedia.org/wiki/Query_string).  Example:

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250
```

2. Put **client\_secret={your client secret}** to the end of string.

```text
akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_secret=exampleclientkey
```

3. Hash String by **Sha-256**

```text
SHA256(akey=100&client_id=exampleclientid&ekey1=100&ekey2=200&wkey3=250&client_secret=exampleclientkey)
=
ca3f40ae95c5dc7cd89259746d2c2476f600e9c914ac2d35f6510aadb39a1364
```

4. String to uppercase

```text
sign=CA3F40AE95C5DC7CD89259746D2C2476F600E9C914AC2D35F6510AADB39A1364
```

5. Attach **sign** to form data parameters

{% hint style="info" %}
NOTICE!!   ****Don't show your **client\_secret** to request parameter.
{% endhint %}





