---
description: This resource provides methods to interact with the User.
---

# User

The user resource and its methods are accessible on the Magic instance by the `User` attribute.

```python
from magic_admin import Magic

magic = Magic(api_secret_key='sk_live_...')

magic.User
magic.User.get_metadata_by_issuer
magic.User.get_metadata_by_public_address
magic.User.get_metadata_by_token
magic.User.logout_by_issuer
magic.User.logout_by_public_address
magic.User.logout_by_token
```

{% page-ref page="get\_metadata\_by\_issuer.md" %}

{% page-ref page="get\_metadata\_by\_public\_address.md" %}

{% page-ref page="get\_metadata\_by\_token.md" %}

{% page-ref page="logout\_by\_issuer.md" %}

{% page-ref page="logout\_by\_public\_address.md" %}

{% page-ref page="logout\_by\_token.md" %}

