# 🚀 Get Started

## 📦 Installation

Magic interacts with the [ICON](https://icon.foundation/)  blockchain via Magic's extension NPM package [`@magic-ext/icon`](https://www.npmjs.com/package/@magic-ext/icon). The ICON extension also lets you interact with the blockchain using methods from [ICON's Javascript SDK](https://www.icondev.io/docs/javascript-sdk).

{% hint style="info" %}
You can skip straight to our kitchen sink example directly:

👉 [**ICON Example**](https://go.magic.link/example-icon)\*\*\*\*
{% endhint %}

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save @magic-ext/icon
```
{% endtab %}

{% tab title="Yarn" %}
```
yarn add @magic-ext/icon
```
{% endtab %}
{% endtabs %}

## ⚡️ Initializing Extension

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { IconExtension } from '@magic-ext/icon';
 
const magic = new Magic('YOUR_API_KEY', {
  extensions: [
    new IconExtension({
      rpcUrl: 'ICON_RPC_NODE_URL'
    })
  ]
});
```
{% endtab %}
{% endtabs %}

