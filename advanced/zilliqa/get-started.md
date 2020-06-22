# 🚀 Get Started

## 📦 Installation

Magic interacts with the [Zilliqa](https://www.zilliqa.com/)  blockchain via Magic's extension NPM package [`@magic-ext/zilliqa`](https://www.npmjs.com/package/@magic-ext/zilliqa). The Zilliqa extension also lets you interact with the blockchain using methods from [Zilliqa's Javascript SDK](https://github.com/Zilliqa/Zilliqa-JavaScript-Library).

{% hint style="info" %}
You can skip straight to our kitchen sink example directly:

👉[**Zilliqa Example**](https://codesandbox.io/s/github/MagicLabs/example-zilliqa)\*\*\*\*
{% endhint %}

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save @magic-ext/zilliqa
```
{% endtab %}

{% tab title="Yarn" %}
```
yarn add @magic-ext/zilliqa
```
{% endtab %}
{% endtabs %}

## ⚡️ Initializing Extension

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { ZilliqaExtension } from '@magic-ext/zilliqa';
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new ZilliqaExtension({
      rpcUrl: 'Zilliqa_RPC_NODE_URL'
    })
  ]
});
```
{% endtab %}
{% endtabs %}

