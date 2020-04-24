# Errors & Warnings

There are two types of error class to be aware of when working with the client-side JavaScript SDK:

* `SDKError`: Raised by the SDK to indicate missing parameters, communicate deprecations, or other internal issues. A notable example would be a `MISSING_API_KEY` error, which indicates the required API key parameter was missing from `new Magic(...)`.
* `RPCError`: Errors associated with specific method calls to the Magic `<iframe>` context. These methods are formatted as [JSON RPC 2.0](https://www.jsonrpc.org/specification) payloads, so they return error codes as _integers_. This type of error is raised by methods like [`AuthModule.loginWithMagicLink`](auth-module/login-with-magic-link.md#error-codes).

## `SDKError`

The `SDKError` class is exposed for `instanceof` operations.

```typescript
import { SDKError } from 'magic-sdk';

try {
  // Something async...
catch (err) {
  if (err instanceof SDKError) {
    // Handle...
  }
}
```

Additionally, an enumeration of relevant error codes is also exposed for convenience and human readability:

```typescript
import { SDKErrorCode } from 'magic-sdk';

SDKErrorCode.MissingApiKey
SDKErrorCode.ModalNotReady
SDKErrorCode.MalformedResponse
// Please reference the `Enum Key` column of the error table below.
```

### Error Codes

| Code | Enum Key | Description |
| :--- | :--- | :--- |
| `MISSING_API_KEY` | `MissingApiKey` | Indicates the required Magic API key is missing or invalid. |
| `MODAL_NOT_READY` | `ModalNotReady` | Indicates the Magic iframe context is not ready to receive events. This error should be rare and usually indicates an environmental issue or improper `async/await` usage. |
| `MALFORMED_RESPONSE` | `MalformedResponse` | Indicates the response received from the Magic iframe context is malformed. We all make mistakes \(even us\), but this should still be a rare exception. If you encounter this, please be aware of phishing! |

## `RPCError`

The `RPCError` class is exposed for `instanceof` operations:

```typescript
import { RPCError } from 'magic-sdk';

try {
  // Something async...
catch (err) {
  if (err instanceof RPCError) {
    // Handle...
  }
}
```

Additionally, an enumeration of relevant error codes is also exposed for convenience and human readability:

```typescript
import { RPCErrorCode } from 'magic-sdk';

RPCErrorCode.MagicLinkExpired
RPCErrorCode.UserAlreadyLoggedIn
RPCErrorCode.ParseError
RPCErrorCode.MethodNotFound
RPCErrorCode.InternalError
// and so forth...
// Please reference the `Enum Key` column of the error table below.
```

### Magic Link Error Codes

| Code | Enum Key | Description |
| :--- | :--- | :--- |
| -10000 | `MagicLinkFailedVerification` | The magic link failed verification, possibly due to an internal service error or a generic network error. |
| -10001 | `MagicLinkExpired` | The user clicked their magic link after it had expired \(this can happen if the user takes more than 10 minutes to check their email\). |
| -10002 | `MagicLinkRateLimited` | If the `showUI` parameter is set to `false`, this error will communicate the email rate limit has been reached. Please debounce your method calls if this occurs. |
| -10003 | `UserAlreadyLoggedIn` | A user is already logged in. If a new user should replace the existing user, make sure to call [`logout`](user-module/logout.md) before proceeding. |
| -10004 | `UpdateEmailFailed` | An update email request was unsuccessful, either due to an invalid email being supplied or the user canceled the action. |

### Standard JSON RPC 2.0 Error Codes

| Code | Enum Key | Description |
| :--- | :--- | :--- |
| -32700 | `ParseError` | Invalid JSON was received by the server. An error occurred on the server while parsing the JSON text. |
| -32600 | `InvalidRequest` | The JSON sent is not a valid Request object. |
| -32601 | `MethodNotFound` | The method does not exist / is not available. |
| -32602 | `InvalidParams` | Invalid method parameter\(s\). |
| -32603 | `InternalError` | Internal JSON-RPC error. These can manifest as different generic issues \(i.e.: attempting to access a protected endpoint before the user is logged in\). |

