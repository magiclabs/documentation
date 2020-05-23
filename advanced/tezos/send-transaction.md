# 💸 Send Transaction

## Send transaction

Using sendTransactionOperation function to send tezos. You can get testnet tezos account with test XTZ from [Tezos Faucet](https://faucet.tzalpha.net/). Please check [conseiljs](https://cryptonomic.github.io/ConseilJS/#/) official documentation to **Initialize the tezos account**

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { TezosExtension } from '@magic-sdk/extension-tezos';
 
const magic = new Magic('YOUR_API_KEY', {
    extensions: [
        new TezosExtension({
            rpcUrl: 'tezos rpc url'
        })
    ]
});


const result = await magic.tezos.sendTransactionOperation(
        'tz1RVcUP9nUurgEJMDou8eW3bVDs6qmP5Lnc', // to address
        500000, // amount
        1500,   // fee
        ''      // derivation path
    );
console.log(`Injected operation group id ${result.operationGroupID}`);
```
{% endtab %}
{% endtabs %}

