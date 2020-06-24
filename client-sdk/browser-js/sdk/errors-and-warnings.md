# Errors & Warnings

There are three types of error class to be aware of when working with the client-side JavaScript SDK:

* `SDKError`: Raised by the SDK to indicate missing parameters, communicate deprecation notices, or other internal issues. A notable example would be a `MISSING_API_KEY` error, which informs the required API key parameter was missing from `new Magic(...)`.
* `RPCError`: Errors associated with specific method calls to the Magic `<iframe>` context. These methods are formatted as [JSON RPC 2.0](https://www.jsonrpc.org/specification) payloads, so they return error codes as _integers_. This type of error is raised by methods like [`AuthModule.loginWithMagicLink`](auth-module/login-with-magic-link.md#error-codes).
* `ExtensionError`: Errors associated with method calls to Magic SDK Extensions. Extensions are an upcoming/experimental feature of Magic SDK. More information will be available once Extensions are officially released.

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

`SDKError` instances expose the `code` field which may be used to deterministically identify the error. Additionally, an enumeration of error codes is exposed for convenience and readability:

```typescript
import { SDKErrorCode } from 'magic-sdk';

SDKErrorCode.MissingApiKey
SDKErrorCode.ModalNotReady
SDKErrorCode.MalformedResponse
// and so forth...
// Please reference the `Enum Key` column of the error table below.
```

### Error Codes

| Enum Key | Description |
| :--- | :--- |
| `MissingApiKey` | Indicates the required Magic API key is missing or invalid. |
| `ModalNotReady` | Indicates the Magic iframe context is not ready to receive events. This error should be rare and usually indicates an environmental issue or improper `async/await` usage. |
| `MalformedResponse` | Indicates the response received from the Magic iframe context is malformed. We all make mistakes \(even us\), but this should still be a rare exception. If you encounter this, please be aware of phishing! |
| `InvalidArgument` | Raised if an SDK method receives an invalid argument. Generally, TypeScript saves us all from simple bugs, but there are validation edge cases it cannot solve—this error type will keep you informed! |
| `ExtensionNotInitialized` | Indicates an extension method was invoked before the Magic SDK instance was initialized. Make sure to access extension methods only from the Magic SDK instance to avoid this error. |

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

`RPCError` instances expose the `code` field which may be used to deterministically identify the error. Additionally, an enumeration of error codes is exposed for convenience and readability:

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

## `ExtensionError`

The `ExtensionError` class is exposed for `instanceof` operations:

```typescript
import { ExtensionError } from 'magic-sdk';

try {
  // Something async...
catch (err) {
  if (err instanceof ExtensionError) {
    // Handle...
  }
}
```

`ExtensionError` instances expose the `code` field which may be used to deterministically identify the error. Magic SDK does not export a global enumeration of Extension error codes. Instead, Extension authors are responsible for exposing and documenting error codes relevant to the Extension's use-case.

