---
description: Retrieves information about user by the supplied DID Token.
---

# getMetadataByToken

### Arguments

`getMetadataByToken(didToken)`

* `didToken` \(String\): A valid [Decentralized ID Token](../../../../decentralized-id.md) generated client-side by a Magic user.

### Returns

`Promise<{ issuer, email, publicAddress }>`: an object containing the issuer, email and cryptographic [public address ](https://support.blockchain.com/hc/en-us/articles/360000951966-Public-and-private-keys)of the authenticated user.

* `issuer` \(String\): The Decentralized ID of the user.  We recommend this value to be used as the user ID in your own tables.
* `email` \(String\): Email address of the authenticated user.
* `publicAddress`\(String\): The authenticated user's public address \(a.k.a.: public key\). Currently, this value is associated with the Ethereum blockchain.

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');
const mAdmin = new Magic('SECRET_API_KEY');

...

// Get a token however you wish! Perhaps this is attached
// to `req.authorization`
const DIDToken = // ...

// Retrieves user information by DID token
const metadata = await mAdmin.users.getMetadataByToken(DIDToken);
```

