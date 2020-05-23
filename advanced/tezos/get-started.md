# 🚀 Get Started

## 📦 Installation

To interact with the Tezos blockchain, you can use **@magic-ext/tezos** with Magic.

For more information, you can check [@magic-ext/tezos](https://www.npmjs.com/package/@magic-ext/tezos) npm package and [conseiljs](https://cryptonomic.github.io/ConseilJS/#/) official documentation.

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save @magic-ext/tezos
```
{% endtab %}

{% tab title="Yarn" %}
```
yarn add @magic-ext/tezos
```
{% endtab %}
{% endtabs %}

## ⚡️ Initializing Extension

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { TezosExtension } from '@magic-ext/tezos';
 
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

