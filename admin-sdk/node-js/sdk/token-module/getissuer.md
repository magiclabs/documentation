# getIssuer

### Arguments

`getIssuer(didToken)`

* `didToken` \(String\): A [Decentralized ID Token](../../../../decentralized-id.md) generated by a Magic user on the client-side.

### Returns

`string`: The Decentralized ID of the Magic User who generated the DID Token.

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');
const mAdmin = new Magic('SECRET_API_KEY');

...

/* Gets the DID token from a login request */
app.get('/login', async (req: any, res: any) => {
  /*
    Assumes DIDToken was passed in the Authorization header
    in the standard `Bearer {token}` format.
   */
  const DIDToken = req.headers.authorization.substring(7);
  const issuer = mAdmin.token.getIssuer(DIDToken);
  /* You can use this as the ID column in your own tables */
});
```

