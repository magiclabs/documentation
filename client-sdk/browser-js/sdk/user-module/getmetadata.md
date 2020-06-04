---
description: Retrieves information for the authenticated user.
---

# getMetadata

### Arguments

None.

### Returns

[`PromiEvent<{ issuer, email, publicAddress }>`](../promievents.md): an object containing the issuer, email and cryptographic [public address ](https://support.blockchain.com/hc/en-us/articles/360000951966-Public-and-private-keys)of the authenticated user.

* `issuer` \(String\): The Decentralized ID of the user.  In server-side use-cases, we recommend this value to be used as the user ID in your own tables.
* `email` \(String\): Email address of the authenticated user.
* `publicAddress`\(String\): The authenticated user's public address \(a.k.a.: public key\). Currently, this value is associated with the Ethereum blockchain. 

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

// Assumes a user is already logged in
try {
  const { email, publicAddress } = await m.user.getMetadata();
} catch {
  // Handle errors if required!
}
```

