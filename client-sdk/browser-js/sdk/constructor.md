---
description: Configure and construct your Magic SDK instance.
---

# Constructor

### Arguments

`new Magic(apiKey, options?)`

* `apiKey` \(String\): Your **publishable** API Key retrieved from the [Magic Dashboard](https://dashboard.magic.link).
* `options.network?` \(String\|Object\)
  * \(String\): a representation of the connected Ethereum network \(one of: `mainnet`, `rinkeby`, `kovan`, or `ropsten`\).
  * \(Object\): a custom Ethereum Node configuration with the following shape:
    * `rpcUrl` \(String\): A URL pointing to your custom Ethereum Node.
    * `chainId?` \(Number\): Some Node infrastructures require you to pass an explicit chain ID. If you are aware that your Node requires this configuration, pass it here as an integer.
  * [🤯 Learn more about using Magic SDK with Ethereum!](../../../advanced/ethereum/)
* `options.endpoint?`\(String\): A URL pointing to the Magic `<iframe>` application.

### Example

```typescript
import { Magic } from 'magic-sdk';

let m;

// Construct with an API key:
m = new Magic('API_KEY');

// Construct with an API key plus options:
m = new Magic('API_KEY', { network: 'rinkeby', endpoint: '...' });
```

