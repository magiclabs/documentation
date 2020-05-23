# 👤 Get User Info

## Get account

Using getAccount function to get tezos public address for current user.

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { TezosExtension } from '@magic-ext/tezos';
 
const magic = new Magic('YOUR_API_KEY', {
    extensions: [
        new TezosExtension({
            rpcUrl: 'tezos rpc url'
        })
    ]
});

// get user's tezose public address
const publicAddress = await magic.tezos.getAccount();
console.log('tezos public address', publicAddress);
```
{% endtab %}
{% endtabs %}



