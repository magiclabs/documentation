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
      rpcUrl: 'TEZOS_RPC_NODE_URL'
    })
  ]
});

// Get user's tezose public address
const publicAddress = await magic.tezos.getAccount();
console.log('Tezos Public Address: ', publicAddress);
```
{% endtab %}
{% endtabs %}



