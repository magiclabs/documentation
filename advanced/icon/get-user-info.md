# 👤 Get User Info

## Get Account

Using getAccount function to get ICON public address for current user.

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { IconExtension } from '@magic-ext/icon';
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new IconExtension({
      rpcUrl: 'ICON_RPC_NODE_URL'
    })
  ]
});

// Get user's ICON public address
const publicAddress = await magic.icon.getAccount();
console.log('ICON Public Address: ', publicAddress);
```
{% endtab %}
{% endtabs %}

