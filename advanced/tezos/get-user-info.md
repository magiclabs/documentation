# 👤 Get User Info

## Get Account

Using getAccount function to get Tezos public address for current user.

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

// Get user's Tezos public address
const publicAddress = await magic.tezos.getAccount();
console.log('Tezos Public Address: ', publicAddress);
```
{% endtab %}
{% endtabs %}



