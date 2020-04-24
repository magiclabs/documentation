---
description: initiates the update email flow that allows a user to change to a new email
---

# updateEmail

## Arguments

`updateEmail({ email, showUI? = true })`

* `email` \(String\): The new email to update to.
* `showUI?`\(Boolean\): If `true`, show an out-of-the-box pending UI  includes instructions on which step of the confirmation process the user is on. Dismisses automatically when the process is complete.

### Returns

`Promise<boolean>`: The promise resolves with a true boolean value if update email is successful and rejects with a specific error code if the request fails. 

### Example

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

// Initiates the flow to update a user's current email to a new one.
try {
  ...
  /* Assuming user is logged in */
  await magic.user.updateEmail({ email: 'new_user_email@example.com' });
} catch {
  // Handle errors if required!
}

/**
 * Initiates the flow to update a user's current email to a new one,
 * without showing an out-of-the box UI.
 */ 
try {
  /* Assuming user is logged in */
  await magic.user.updateEmail({ email: 'new_user_email@example.com', showUI: false });
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
  await m.user.updateEmail({ email: 'hello@example.com', showUI: false });
} catch(err) {
  if (err instanceof RPCError) {
    switch(err.code) {
      case RPCErrorCode.UpdateEmailFailed:
        // Handle errors accordingly :)
        break;
    }
  }
}

```

