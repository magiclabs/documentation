# Errors & Warnings

## `SDKError`

The `SDKError` class is exposed for `instanceof` operations.

```typescript
import { SDKError } from '@magic-sdk/admin';

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
import { ErrorCode } from '@magic-sdk/admin';

ErrorCode.MissingApiKey
ErrorCode.MissingAuthHeader
ErrorCode.IncorrectSignerAddress
// and so forth...
// Please reference the `Enum Key` column of the error table below.
```

### Error Codes

| Enum Key | Description |
| :--- | :--- |
| `TokenExpired` | The supplied DID Token is invalid due to an expired timestamp. |
| `IncorrectSignerAddress` | The supplied DID Token is invalid due to a mismatch between the signature origin and the claimed user public address. |
| `FailedRecoveryProof` | The supplied DID Token could not be recovered using Elliptic Curve recovery. |
| `ApiKeyMissing` | The API key required for a particular action is missing or malformed. |
| `MalformedTokenError` | The supplied DID Token could not be successfully parsed. |
| `ServiceError` | An error occurred while communicating with the Magic API. Be sure to check the `data` property of the error object for additional context. |

### `data` & Nested Errors

For additional context about an error, the `SDKError.data` property contains an array of potentially illuminating metadata. At the moment, this property is reserved for service errors when communication to Magic APIs fail. 

