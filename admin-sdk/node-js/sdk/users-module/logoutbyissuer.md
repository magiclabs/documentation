---
description: >-
  Logs a user out of all client-side Magic SDK sessions given the user's
  Decentralized ID.
---

# logoutByIssuer

### Arguments

`logoutByIssuer(issuer)`

* `issuer` \(String\): The user's [Decentralized ID](../../../../tutorials/decentralized-id.md), which can be parsed using [`TokenModule.getIssuer`](../token-module/getissuer.md).

### Returns

`Promise<void>`

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');
const mAdmin = new Magic('SECRET_API_KEY');

...

// Grabs user's Decentralized ID from the DID Token
const issuer = mAdmin.token.getIssuer(DIDToken);

// logs the user out of all valid browser sessions.
await mAdmin.users.logoutByIssuer(issuer);
```

