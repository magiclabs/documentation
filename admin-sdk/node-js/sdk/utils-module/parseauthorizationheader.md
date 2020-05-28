# parseAuthorizationHeader

### Arguments

`parseAuthorizationHeader(header)`

* `header` \(String\): A request authorization header passed in front the client-side application that looks like `Bearer WyIweG...n0iXQ==`.

### Returns

`string`: The DID token embedded in the authorization header.

{% hint style="info" %}
This is only available to Admin SDK version **1.1.0** and above.
{% endhint %}

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');
const mAdmin = new Magic();

...

/* Gets the DID token from a login request */
app.get('/login', async (req: any, res: any) => {
  /*
    Assumes DIDToken was passed in the Authorization header
    in the standard `Bearer {token}` format.
   */
  const didToken = mAdmin.utils.parseAuthorizationHeader(req.headers.authorization);
  /* You can now do stuff with the DID token */
});
```

