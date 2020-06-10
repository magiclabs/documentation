---
description: >-
  Generates a Decentralized Id Token which acts as a proof of authentication to
  resource servers.
---

# getIdToken

### Arguments

`getIdToken({ lifespan? = 900 })`

* `lifespan?` \(String\): will set the lifespan of the generated token. Defaults to 900s \(15 mins\)

### Returns

[`PromiEvent<string>`](../promievents.md): Base64-encoded string representation of a JSON tuple representing `[proof, claim]`

{% page-ref page="../../../../decentralized-id.md" %}

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

// Assumes a user is already logged in
try {
  const idToken = await m.user.getIdToken();
} catch {
  // Handle errors if required!
}
```

