# 🚀 Get Started

## 📦 Installation

Magic interacts with the [Tezos](https://tezos.com/) blockchain via Magic's extension NPM package [`@magic-ext/tezos`](https://www.npmjs.com/package/@magic-ext/tezos). The Tezos extension also lets you interact with the blockchain using methods from Tezos's [ConseilJS](https://cryptonomic.github.io/ConseilJS/#/) SDK.

{% hint style="info" %}
You can skip straight to our kitchen sink example directly:

👉 [**Tezos ConseilJS Example**](https://go.magic.link/example-tezos)\*\*\*\*
{% endhint %}

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
      rpcUrl: 'TEZOS_RPC_NODE_URL'
    })
  ]
});
```
{% endtab %}
{% endtabs %}

