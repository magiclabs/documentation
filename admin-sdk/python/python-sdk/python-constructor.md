# Constructor

### Magic

The constructor allows you to specify your own API secret key and HTTP request strategy when your application is interacting with the Magic API.

```python
Magic(api_secret_key=None, retries=3, timeout=10, backoff_factor=0.02)
```

#### Arguments:

* `api_secret_key`\(str\): Your API **secret** Key retrieved from the [Magic Dashboard](https://dashboard.magic.link).
* `retries`\(num\): Total number of retries to allow.
* `timeout`\(num\): A period of time the request is going to wait for a response.
* `backoff_factor`\(num\): A backoff factor to apply between retry attempts.

#### Returns:

* A `Magic` object  that provides access to all the supported [resources](python-resources/).

#### Examples:

```python
from magic_admin import Magic

magic = Magic(
    api_secret_key='<YOUR_API_SECRET_KEY>'
    retries=5,
    timeout=5,
    backoff_factor=0.01,
)
```

