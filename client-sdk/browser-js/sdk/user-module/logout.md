---
description: Logs out the currently authenticated Magic user
---

# logout

### Arguments

None.

### Returns

`Promise<void>`

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

try {
  await m.user.logout();
  console.log(await m.user.isLoggedIn()); // => `false`
} catch {
  // Handle errors if required!
}
```

