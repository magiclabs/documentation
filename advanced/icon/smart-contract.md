# 📜 Smart Contract

## Deploy Contract

### Getting Test ICON

Before you can send transaction on the ICON blockchain, you'll need to acquire some test ICON \(ICON's native cryptocurrency for test network\).

1. Go to our [**ICON Example**](https://go.magic.link/example-icon) application
2. Login with your email address
3. Copy your ICON public address
4. Go to the[ **ICON Faucet**](https://icon-faucet.ibriz.ai/)\*\*\*\*
5. Paste your copied ICON public address in the text input
6. You can receive up to **100 test ICON per day**
7. Now you can use your test ICON in our [**example app**](https://go.magic.link/example-icon)\*\*\*\*

### Call Extension Method

Note that the Magic ICON extension follows the method names and conventions by [**ICON's Javascript SDK**](https://www.icondev.io/docs/javascript-sdk). \(link to documentation\). To send a standard ICON blockchain transaction, you can call the `magic.icon.sendTransaction` method.

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { IconExtension } from '@magic-ext/icon';

import IconService from "icon-sdk-js";

const { DeployTransactionBuilder, IconConverter } = IconService;
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new IconExtension({
      rpcUrl: 'ICON_RPC_NODE_URL'
    })
  ]
});

const metadata = await magic.user.getMetadata();

// Build a transaction
const txObj = new DeployTransactionBuilder()
  .from(metadata.publicAddress)
  .to('cx0000000000000000000000000000000000000000')
  .stepLimit(IconConverter.toBigNumber(2100000000).toString())
  .nid(IconConverter.toBigNumber(3).toString())
  .nonce(IconConverter.toBigNumber(1).toString())
  .version(IconConverter.toBigNumber(3).toString())
  .timestamp((new Date()).getTime() * 1000)
  .contentType('application/zip')
  .content(`0x${compiledContractContent}`)
  .params({
    initialSupply: IconConverter.toHex('100000000000'),
    decimals: IconConverter.toHex(18),
    name: 'StandardToken',
    symbol: 'ST',
  })
  .build();

// Send transaction to deploy contract
const txhash = await magic.icon.sendTransaction(txObj);

console.log(`Transaction Hash: ${txhash}`);
```
{% endtab %}
{% endtabs %}

