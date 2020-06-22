# 💸 Send Transaction

## Send Transaction

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

To send a standard Zilliqa blockchain transaction, you can call the `magic.Zilliqa.sendTransaction` method.

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

const chainId = 333; // chainId of the developer testnet
const msgVersion = 1; // current msgVersion
const VERSION = bytes.pack(chainId, msgVersion);

const myGasPrice = units.toQa('1000', units.Units.Li);

const params = {
   version: VERSION,
   toAddr: "zil14vut0rh7q78ydc0g7yt7e5zkfyrmmps00lk6r7",
   amount: (new BN(units.toQa('0.5', units.Units.Zil))), 
   gasPrice: myGasPrice,
   gasLimit: Long.fromNumber(1),
};

const tx = await magic.zil.sendTransaction(
   params,
   false,
);
// Send a transaction
console.log('send transaction', tx)

```
{% endtab %}
{% endtabs %}

