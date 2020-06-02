# 💸 Send Transaction

## Send Transaction

### Getting Test XTZ

Before you can send transaction on the Tezos blockchain, you'll need to acquire some test XTZ \(Tezos' native cryptocurrency for test network\).

1. Go to our [**Tezos Faucet**](https://go.magic.link/tezos-test-faucet)\*\*\*\*
2. Type in your email and click the **"Sign Up / Login"** button
3. Go to your email and click on the magic link to login
4. Once you are logged in, you will get **10 test XTZ**
5. Now you can use your test XTZ in our [**example app**](https://go.magic.link/example-tezos)\*\*\*\*

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

