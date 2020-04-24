---
description: Retrieves information about user by the supplied "issuer".
---

# getMetadataByIssuer

### Arguments

`getMetadataByIssuer(issuer)`

* `issuer` \(String\): The user's [Decentralized ID](../../../../tutorials/decentralized-id.md), which can be parsed using [`TokenModule.getIssuer`](../token-module/getissuer.md).

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

// Grabs the issuer from a DID Token
const issuer = mAdmin.token.getIssuer(DIDToken);

// Gets user metadata based on the given issuer
const metadata = await mAdmin.users.getMetadataByIssuer(issuer);
```

