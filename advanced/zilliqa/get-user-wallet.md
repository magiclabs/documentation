# 👤 Get User Wallet

## Get Wallet

Using getAccount function to get ICON public address for current user.

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { ZilliqaExtension } from '@magic-ext/zilliqa';
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new ZilliqaExtension({
      rpcUrl: 'Zilliqa_RPC_NODE_URL'
    })
  ]
});

// Get user's Zilliqa wallet info
const wallet = await magic.zilliqa.getWallet();
console.log('Zilliqa wallet: ', wallet);
```
{% endtab %}
{% endtabs %}

