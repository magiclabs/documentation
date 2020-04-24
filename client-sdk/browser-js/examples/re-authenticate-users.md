# Re-authenticate Users

A user's Magic SDK session persists up to 7 days, so re-authentication is usually friction-less.

## Prerequisite

* ​[Install client-side JavaScript SDK​](../get-started.md#installation)

## Step 1: Re-authenticate the user

```typescript
import { Magic } from 'magic-sdk';
const m = new Magic('API_KEY');

const email = 'example@magic.link';

if (await m.user.isLoggedIn())  {
    const didToken = await m.user.getIdToken();
    
    // Do something with the DID token.
    // For instance, this could be a `fetch` call
    // to a protected backend endpoint.
    document.getElementById('your-access-token').innerHTML = didToken;
} else {
    // Log in the user
    const user = await m.auth.loginWithMagicLink({ email });
}
```

