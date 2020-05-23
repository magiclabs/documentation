# 🚀 Get Started

## 📦 Installation

To interact with the Tezos blockchain, you can use **@magic-sdk/extension-tezos** with Magic.

For more information, you can check [@magic-sdk/extension-tezos](https://www.npmjs.com/package/@magic-sdk/extension-tezos) npm package and [conseiljs](https://cryptonomic.github.io/ConseilJS/#/) official documentation.

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save @magic-sdk/extension-tezos
```
{% endtab %}

{% tab title="Yarn" %}
```
yarn add @magic-sdk/extension-tezos
```
{% endtab %}
{% endtabs %}

## ⚡️ Initializing Extension

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
```
{% endtab %}
{% endtabs %}

