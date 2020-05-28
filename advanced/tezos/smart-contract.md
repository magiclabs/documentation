# 📜 Smart Contract

## Deploy Contract

Note that the Magic Tezos extension follows the method names and conventions by [**ConceilJS**](https://cryptonomic.github.io/ConseilJS/#/?id=smart-contract-interactions) \(link to documentation\). To deploy a Tezos smart contract, you can call the `magic.tezos.sendContractOriginationOperation` method.

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

const contract = `[
  {
    "prim":"parameter",
     "args":[ { "prim":"string" } ]
  },
  {
    "prim":"storage",
     "args":[ { "prim":"string" } ]
  },
  {
    "prim":"code",
    "args":[
      [  
        { "prim":"CAR" },
        { "prim":"NIL", "args":[ { "prim":"operation" } ] },
        { "prim":"PAIR" }
      ]
    ]
  }
]`;

const storage = '{"string": "Sample"}';

const params = {
  amount: 0,
  delegate: undefined,
  fee: 100000,
  derivationPath: "",
  storage_limit: 1000,
  gas_limit: 100000,
  code: contract,
  storage,
  codeFormat: "micheline"
};

const result = await magic.tezos.sendContractOriginationOperation(
  params.amount,
  params.delegate,
  params.fee,
  params.derivationPath,
  params.storage_limit,
  params.gas_limit,
  params.code,
  params.storage,
  params.codeFormat
);

const operationGroupID = result.operationGroupID.trim();

setContractoperationGroupID(
  operationGroupID.substring(1, operationGroupID.length - 1)
);

console.log(
  `Injected operation group ID: ${result.operationGroupID}`,
  result
);
```
{% endtab %}
{% endtabs %}



