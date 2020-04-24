---
description: >-
  Authenticate a user passwordlessly using a "magic link" sent to the specified
  user's email address.
---

# loginWithMagicLink

### Arguments

`loginWithMagicLink({ email, showUI? = true })`

* `email` \(String\): The user email to log in with.
* `showUI?`\(Boolean\): If `true`, show an out-of-the-box pending UI while the request is in flight.

### Returns

`Promise<string | null>`: The promise resolves upon authentication request success and rejects with a specific error code if the request fails. The resolved value is a Decentralized ID token with a default 15-minute lifespan.

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

// log in a user by their email
try {
  await m.auth.loginWithMagicLink({ email: 'hello@example.com' });
} catch {
  // Handle errors if required!
}

// log in a user by their email, without showing an out-of-the box UI.
try {
  await m.auth.loginWithMagicLink({ email: 'hello@example.com', showUI: false });
} catch {
  // Handle errors if required!
}

```

### Error Handling

[**Relevant Error Codes**](../errors-and-warnings.md#magic-link-error-codes)\*\*\*\*

To achieve a fully white-labeled experience, you will need to implement some custom error handling according to your UI needs. Here's a short example to illustrate how errors can be caught and identified by their code:

```typescript
import { Magic, RPCError, RPCErrorCode } from 'magic-sdk';

const m = new Magic('API_KEY');

try {
  await m.auth.loginWithMagicLink({ email: 'hello@example.com', showUI: false });
} catch(err) {
  if (err instanceof RPCError) {
    switch(err.code) {
      case RPCErrorCode.MagicLinkFailedVerification:
      case RPCErrorCode.MagicLinkExpired:
      case RPCErrorCode.MagicLinkRateLimited:
      case RPCErrorCode.UserAlreadyLoggedIn:
        // Handle errors accordingly :)
        break;
    }
  }
}

```

