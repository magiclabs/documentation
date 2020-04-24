---
description: >-
  Logs a user out of all client-side Magic SDK sessions given the user's public
  address.
---

# logoutByToken

### Arguments

`logoutByToken(didToken)`

* `didToken` \(String\): A valid [Decentralized ID Token](../../../../tutorials/decentralized-id.md) generated client-side by a Magic user.

### Returns

`Promise<void>`

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');
const mAdmin = new Magic('SECRET_API_KEY');

...

// Get a token however you wish! Perhaps this is attached
// to `req.authorization`
const DIDToken = // ...

// logs the user out of all valid browser sessions.
await mAdmin.users.logoutByToken(DIDToken);
```

