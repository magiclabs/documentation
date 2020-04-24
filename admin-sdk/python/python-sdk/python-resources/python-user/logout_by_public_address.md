# logout\_by\_public\_address

Logs a user out of all Magic SDK sessions given the user's public address. This method is useful if you store the `public_address` . 

```text
User.logout_by_public_address(public_address)
```

### Arguments:

* public\_address \(str\): The user's Ethereum public address.

### Raises:

* `RateLimitingError`: If you have sent too many requests within a given period of time.
* `BadRequestError`: If the supplied parameters are invalid.
* `AuthenticationError`: If your API secret key cannot be authenticated with Magic API server.
* `ForbiddenError`:  If your API secret key is not authorized to access the resources.
* `APIError`: For any other API error.
* `APIConnectionError`: If your server cannot communicate with the Magic server. Normally this is a network communication error.

{% hint style="info" %}
See [Error Handling](../../python-response-and-error-handling.md) for more examples.
{% endhint %}

### Returns:

* A [`MagicResponse`](../../python-response-and-error-handling.md#magicresponse).

### Example:

The example below is assuming you are already using a Python Web Framework \(Django, Flask, Cherrypy, etc.\)  Web framework's specific imports are omitted in favor of the simplicity of the example. Only the `magic_admin` related imports are shown below.

```python
from magic_admin import Magic
from magic_admin.error import DIDTokenError
from magic_admin.error import RequestError


@user.route('/v1/user/logout', method=['POST'])
def user_logout(self, user_id):
    magic = Magic(api_secret_key='<YOUR_API_SECRET_KEY>')

    # Load user by user_id.
    user = logic.User.load_by_id(user_id)
    
    try:
        magic.User.logout_by_public_address(user.public_address)
    except RequestError as e:
        # You can also remap this error to your own application error.
        return HttpError(str(e))
    
    return HttpResponse()
```

