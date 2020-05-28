# 💸 Send Transaction

## Send Transaction

### Getting Test XTZ

Before you can send transaction on the Tezos blockchain, you'll need to acquire some test XTZ \(Tezos' native cryptocurrency\). You can follow the steps here using the [**Tezos Faucet**](https://faucet.tzalpha.net/).

1. Go to  [Tezos Faucet](https://faucet.tzalpha.net/), click the **"Get Testnet ꜩ"** button
2. Copy the generated account JSON
3. Paste your account JSON to [Tezos Faucet Importer](https://smartpy.io/dev/faucet.html), follow the instruction to initialize the account.
4. Copy your pkh \(public key hash\) from account Json,  private key from step 3 and public key from the result of step 7 from the Tezos Faucet Importer.
5. Go to [conseiljs transfer value](https://cryptonomic.github.io/ConseilJS/#/?id=transfer-value), follow the document to create your account's key store by the value from previous step.
6. Transfer XTZ to your Magic Tezos account address \(Tezos public address from Get User Info section\).
7. You're good to go!

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

