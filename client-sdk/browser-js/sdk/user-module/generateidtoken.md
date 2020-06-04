---
description: Generates a Decentralized Id Token with optional serialized data.
---

# generateIdToken

### Arguments

`generateIdToken({ lifespan? = 900, attachment? = 'none' })`

* `lifespan?` \(Number\) : will set the lifespan of the generated token. Defaults to 900s \(15 mins\)
* `attachment?` \(String\) : will set a signature of serialized data in the generated token. Defaults to `"none"`

### Returns

[`PromiEvent<string>`](../promievents.md): Base64-encoded string representation of a JSON tuple representing `[proof, claim]`

{% page-ref page="../../../../tutorials/decentralized-id.md" %}

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

// Assumes a user is already logged in
try {
  const idToken = await m.user.generateIdToken({ attachment: 'SERVER_SECRET' });
} catch {
  // Handle errors if required!
}
```

