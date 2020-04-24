# get\_metadata\_by\_public\_address

Retrieves information about the user by the supplied `public_address`. This method is useful if you store the `public_address` with your user data.

```text
User.get_metadata_by_public_address(public_address)
```

### Arguments:

* public\_address \(str\): The user's Ethereum public address, which can be parsed using [Token.get\_public\_address](../python-token/get_public_address.md).

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
# A util provided by `magic_admin` to parse the auth header value.
from magic_admin.utils.http import parse_authorization_header_value
from magic_admin.error import DIDTokenError
from magic_admin.error import RequestError


@user.route('/v1/user/update', method=['POST'])
def update_user_info(self, user_id):
    """An exmaple of user update view that uses DID Token from the
    client-side to ensure authenticity of a request before updating
    the user meta.
    """
    did_token = parse_authorization_header_value(
        requests.headers.get('Authorization'),
    )
    if did_token is None:
        raise BadRequest(
            'Authorization header is missing or header value is invalid',
        )
    
    magic = Magic(api_secret_key='<YOUR_API_SECRET_KEY>')
    
    # Validate the did_token
    try:
        magic.Token.validate(did_token)
        pub_addr = magic.Token.get_public_address(did_token)
    except DIDTokenError as e:
        raise BadRequest('DID Token is invalid: {}'.format(e))
    
    try:
        magic_response = magic.User.get_metadata_by_public_address(pub_addr)
    except RequestError as e:
        # You can also remap this error to your own application error.
        return HttpError(str(e))
    
    # Use your application logic to update the user info.
    user_info = logic.User.update_by(
        user_id,
        email=magic_response.data['email'],
    )
    
    return HttpResponse(user_info)
```

{% hint style="warning" %}
It is important to always validate the DID Token before using.
{% endhint %}

