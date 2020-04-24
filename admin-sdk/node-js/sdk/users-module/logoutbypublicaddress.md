---
description: >-
  Logs a user out of all client-side Magic SDK sessions given the user's public
  address.
---

# logoutByPublicAddress

### Arguments

`logoutByPublicAddress(publicAddress)`

* `publicAddress` \(String\): The user's [public address](https://support.blockchain.com/hc/en-us/articles/360000951966-Public-and-private-keys) to log out via the Magic API.

### Returns

`Promise<void>`

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');
const mAdmin = new Magic('SECRET_API_KEY');

...

// Grabs user's public address by DIDToken
const userPublicAddress = mAdmin.token.getPublicAddress(DIDToken);

// logs the user out of all valid browser sessions.
await mAdmin.users.logoutByPublicAddress(userPublicAddress);
```

