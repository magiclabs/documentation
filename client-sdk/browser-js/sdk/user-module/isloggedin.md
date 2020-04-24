---
description: Checks if a user is currently logged in to the Magic Client-side SDK.
---

# isLoggedIn

### Arguments

None.

### Returns

`Promise<Boolean>`

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

try {
  const isLoggedIn = await m.user.isLoggedIn();
  console.log(isLoggedIn) // => `true` or `false`
} catch {
  // Handle errors if required!
}
```



