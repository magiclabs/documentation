# Constructor

### Arguments

`new Magic(secretApiKey, options?)`

* `secretApiKey` \(String\): Your **secret** API Key retrieved from the [Magic Dashboard](https://dashboard.magic.link).
* `options.endpoint?`\(String\): A URL pointing to the Magic API. You should not need to provide this value except in case you are building highly custom integration tests.

### Example

```typescript
const { Magic } = require('@magic-sdk/admin');

let m;

// Construct with an API key:
m = new Magic('API_KEY');

// Construct with an API key plus options:
m = new Magic('API_KEY', { endpoint: '...' });
```

