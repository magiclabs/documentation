# get\_metadata\_by\_issuer

Retrieves information about the user by the supplied `iss` from the [DID Token](../../../../../decentralized-id.md). This method is useful if you store the `iss` with your user data, **which is recommended**.

```text
User.get_metadata_by_issuer(issuer)
```

### Arguments:

* issuer \(str\): The user's Decentralized ID, which can be parsed using [Token.get\_issuer](../python-token/get_issuer.md)

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

* A [`MagicResponse`](../../python-response-and-error-handling.md#magicresponse): The `data` field contains all of the user meta information.
  * `issuer` \(str\): The user's Decentralized ID.
  * `email` \(str\): The user's email address.
  * `public_address` \(str\): The authenticated user's public address \(a.k.a.: public key\). Currently, this value is associated with the Ethereum blockchain.

### Example:

The example below is assuming you are already using a Python Web Framework \(Django, Flask, Cherrypy, etc.\)  Web framework's specific imports are omitted in favor of the simplicity of the example. Only the `magic_admin` related imports are shown below.

```python
from magic_admin import Magic
from magic_admin.error import DIDTokenError
from magic_admin.error import RequestError


@user.route('/v1/user/update', method=['POST'])
def update_user_info(self, user_id):
    """An exmaple of user update view that uses `iss` stored in the
    databoase to fresh user metadata.
    """
    magic = Magic(api_secret_key='<YOUR_API_SECRET_KEY>')
    
    # User your application logic to get the use data.
    user_info = logic.User.get_by_id(user_id)
    
    try:
        magic_response = magic.User.get_metadata_by_issuer(
            user_info.issuer,
        )
    except RequestError as e:
        # You can also remap this error to your own application error.
        return HttpError(str(e))
    
    if user_info.email != magic_response.data['email']:
        # Use your application logic to update the user info.
        logic.User.update_by(
            user_id,
            email=magic_response.data['email'],
        )
    
    return HttpResponse()
```

