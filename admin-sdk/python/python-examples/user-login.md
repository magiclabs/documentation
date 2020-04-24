# User Login

This example shows how you can implement  user `login` on the server side using the [DID Token](../../../tutorials/decentralized-id.md). 

The example assumes:

* You have already configured your client-side app with the [Brower.JS](../../../client-sdk/browser-js/)
* You are already using a Python Web Framework \(Django, Flask, Cherrypy, etc.\)  Web framework's specific imports are omitted in favor of the simplicity of the example. Only the `magic_admin` related imports are shown below

```python
from magic_admin import Magic
# A util provided by `magic_admin` to parse the auth header value.
from magic_admin.utils.http import parse_authorization_header_value
from magic_admin.error import DIDTokenError
from magic_admin.error import RequestError


@user.route('/v1/user/login', method=['POST'])
def user_login(self, email):
    did_token = parse_authorization_header_value(
        requests.headers.get('Authorization'),
    )
    if did_token is None:
        raise BadRequest(
            'Authorization header is missing or header value is invalid',
        )
    
    magic = Magic(api_secret_key='<YOUR_API_SECRET_KEY>')
    
    # Validate the did_token.
    try:
        magic.Token.validate(did_token)
        issuer = magic.Token.get_issuer(did_token)
    except DIDTokenError as e:
        raise BadRequest('DID Token is invalid: {}'.format(e))
    except RequestError as e:
        # You can also remap this error to your own application error.
        return HttpError(str(e))
    
    # Call your appilication logic to load the user.
    user_info = logic.User.load_by(email=email)
    
    if user_info.issuer != issuer:
        return UnAuthorizedError('UnAuthorized user login')
    
    return HttpResponse(user_info)
```

{% hint style="warning" %}
It is important to always validate the DID Token before using.
{% endhint %}

