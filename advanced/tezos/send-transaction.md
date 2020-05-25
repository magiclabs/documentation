# 💸 Send Transaction

## Send Transaction

### Getting Test XTZ

Before you can send transaction on the Tezos blockchain, you'll need to acquire some test XTZ \(Tezos' native cryptocurrency\). You can follow the steps here using the [**Tezos Faucet**](https://faucet.tzalpha.net/).

### Call Extension Method

Note that the Magic Tezos extension follows the method names and conventions by [**ConceilJS**](https://cryptonomic.github.io/ConseilJS/#/) \(link to documentation\). To send a standard Tezos blockchain transaction, you can call the `magic.tezos.sendTransactionOperation` method.

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

const result = await magic.tezos.sendTransactionOperation(
  'tz1RVcUP9nUurgEJMDou8eW3bVDs6qmP5Lnc', // to address
  500000, // amount
  1500,   // fee
  ''      // derivation path
);
console.log(`Injected operation group ID: ${result.operationGroupID}`);
```
{% endtab %}
{% endtabs %}

