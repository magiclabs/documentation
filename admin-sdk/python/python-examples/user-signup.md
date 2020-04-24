# User Signup

This example shows how you can implement  user `signup` on the server side using the [DID Token](../../../tutorials/decentralized-id.md). 

The example assumes:

* You have already configured your client-side app with the [Brower.JS](../../../client-sdk/browser-js/)
* You are already using a Python Web Framework \(Django, Flask, Cherrypy, etc.\)  Web framework's specific imports are omitted in favor of the simplicity of the example. Only the `magic_admin` related imports are shown below

```python
from magic_admin import Magic
# A util provided by `magic_admin` to parse the auth header value.
from magic_admin.utils.http import parse_authorization_header_value
from magic_admin.error import DIDTokenError
from magic_admin.error import RequestError


@user.route('/v1/user/signup', method=['POST'])
def user_signup(self, name, email):
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
        user_meta = magic.User.get_metadata_by_issuer(issuer)
    except DIDTokenError as e:
        raise BadRequest('DID Token is invalid: {}'.format(e))
    except RequestError as e:
        # You can also remap this error to your own application error.
        return HttpError(str(e))
    
    if user_meta.data['email'] != email:
        return UnAuthorizedError('UnAuthorized user signup')
    
    # Call your application logic to save the user.
    logic.User.add(name, email, issuer)
    
    return HttpResponse()
```

You will only need to handle the DID Token. No more password handling ✨

{% hint style="warning" %}
It is important to always validate the DID Token before using.
{% endhint %}

