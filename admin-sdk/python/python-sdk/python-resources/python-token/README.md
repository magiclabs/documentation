---
description: This resource provides methods to interact with the DID Token.
---

# Token

The token resource and its methods are accessible on the Magic instance by the `Token` attribute. 

{% hint style="info" %}
The token resource does not make any API calls to the Magic server.
{% endhint %}

```python
from magic_admin import Magic

magic = Magic(api_secret_key='sk_live_...')

magic.Token
magic.Token.get_issuer
magic.Token.get_public_address
magic.Token.decode
magic.Token.validate
```

## Methods

{% page-ref page="get\_issuer.md" %}

{% page-ref page="get\_public\_address.md" %}

{% page-ref page="decode.md" %}

{% page-ref page="validate.md" %}

