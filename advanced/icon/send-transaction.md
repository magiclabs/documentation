# 💸 Send Transaction

## Send Transaction

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

const { IconBuilder, IconAmount, IconConverter } = IconService;
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new IconExtension({
      rpcUrl: 'ICON_RPC_NODE_URL'
    })
  ]
});

const metadata = await magic.user.getMetadata();
const destinationAddress = 'hx19f4fc31c6e51d5facccb52e3ccbe6b7d61f409e';
const sendICXAmount = '10';

// Build a transaction
const txObj = new IconBuilder.IcxTransactionBuilder()
  .from(metadata.publicAddress)
  .to(destinationAddress)
  .value(IconAmount.of(sendICXAmount, IconAmount.Unit.ICX).toLoop())
  .stepLimit(IconConverter.toBigNumber(100000))
  .nid(IconConverter.toBigNumber(3))
  .nonce(IconConverter.toBigNumber(1))
  .version(IconConverter.toBigNumber(3))
  .timestamp(new Date().getTime() * 1000)
  .build();

// Send a transaction
const txhash = await magic.icon.sendTransaction(txObj);

console.log(`Transaction Hash: ${txhash}`);
```
{% endtab %}
{% endtabs %}

