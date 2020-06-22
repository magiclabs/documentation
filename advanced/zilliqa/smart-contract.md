# 📜 Smart Contract

## Deploy Contract

### Getting Test ZIL

Before you can send transaction on the Zilliqa blockchain, you'll need to acquire some test ZIL \(Zilliqa's native cryptocurrency for test network\).

1. Go to our [**Zilliqa Example**](https://codesandbox.io/s/github/MagicLabs/example-zilliqa) application
2. Login with your email address
3. Copy your **Zilliqa** public address
4. Go to the [**ZIL Faucet**](https://dev-wallet.zilliqa.com/faucet)\*\*\*\*
5. Paste your copied Zilliqa public address in the text input
6. You can receive **300 test ZIL**
7. Now you can use your test ZIL in our [**example app**](https://codesandbox.io/s/github/MagicLabs/example-zilliqa)\*\*\*\*

### Call Extension Method

To deploy a smart contract, you can call the `magic.zilliqa.deployContract` method.

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { ZilliqaExtension } from '@magic-ext/zilliqa';
const { BN, Long, bytes, units } = require('@zilliqa-js/util');
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new ZilliqaExtension({
      rpcUrl: 'Zilliqa_RPC_NODE_URL'
    })
  ]
});

const wallet = await magic.zilliqa.getWallet();

const address = wallet.address;

const code = `scilla_version 0
 
    (* HelloWorld contract *)
 
    import ListUtils
 
    (***************************************************)
    (*               Associated library                *)
    (***************************************************)
    library HelloWorld
 
    let not_owner_code = Int32 1
    let set_hello_code = Int32 2
 
    (***************************************************)
    (*             The contract definition             *)
    (***************************************************)
 
    contract HelloWorld
    (owner: ByStr20)
 
    field welcome_msg : String = ""
 
    transition setHello (msg : String)
      is_owner = builtin eq owner _sender;
      match is_owner with
      | False =>
        e = {_eventname : "setHello()"; code : not_owner_code};
        event e
      | True =>
        welcome_msg := msg;
        e = {_eventname : "setHello()"; code : set_hello_code};
        event e
      end
    end
 
 
    transition getHello ()
        r <- welcome_msg;
        e = {_eventname: "getHello()"; msg: r};
        event e
    end`;
 
const init = [
  // this parameter is mandatory for all init arrays
  {
      vname: '_scilla_version',
      type: 'Uint32',
      value: '0',
  },
  {
      vname: 'owner',
      type: 'ByStr20',
      value: `${address}`,
  },
];

const chainId = 333; // chainId of the developer testnet
const msgVersion = 1; // current msgVersion
const VERSION = bytes.pack(chainId, msgVersion);

const myGasPrice = units.toQa('1000', units.Units.Li);

const params = {
  version: VERSION,
  gasPrice: myGasPrice,
  gasLimit: Long.fromNumber(10000),
}

const result = await magic.zil.deployContract(
  init, code, params, 33, 1000, false
)


console.log('deploy contract', result);

```
{% endtab %}
{% endtabs %}

