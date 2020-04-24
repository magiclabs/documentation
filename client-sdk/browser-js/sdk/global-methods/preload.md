---
description: >-
  Starts downloading the static assets required to render the Magic iframe
  context.
---

# preload

### Arguments

None.

### Returns

`Promise<void>`: A Promise that resolves to indicate the `<iframe>` is ready for requests. 

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

m.preload().then(() => console.log('Magic <iframe> loaded.');
```

