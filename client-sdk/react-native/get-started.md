---
description: Getting started with the Magic React Native JavaScript SDK
---

# 🚀 Get Started

## 📦 Installation

{% hint style="warning" %}
As of `magic-sdk@2.0.0`, React Native bindings are published as a separate NPM package.
{% endhint %}

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save @magic-sdk/react-native
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add @magic-sdk/react-native
```
{% endtab %}
{% endtabs %}

## ⚡️ Creating an SDK Instance

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from '@magic-sdk/react-native';

const m = new Magic('API_KEY'); // ✨
```
{% endtab %}

{% tab title="CommonJS" %}
```typescript
const { Magic } = require('@magic-sdk/react-native');

const m = new Magic('API_KEY'); // ✨
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Examples for the React Native JavaScript SDK use the ES Module/TypeScript pattern by default.
{% endhint %}

## 🖼 Rendering Magic

To facilitate events between the Magic `<iframe>` context and your React Native application, a React component is exposed on your Magic instance: `<Relayer>`.

**`<Relayer>` must be rendered into your application before Magic methods will resolve.**

```typescript
function App() {
  return (
    <div>
      {/* Remember to render the `Relayer` component into your app! */}
      <m.Relayer />
    </div>
  );
}
```

{% hint style="success" %}
APIs from [**Browser JS**](../browser-js/) are also available in the React Native bundle.
{% endhint %}

## ⛓ Usage With Ethereum/Web3

As with the Browser JS SDK, the React Native SDK can be used with Ethereum via **Web3** or **Ethers JS**. There's just one "_gotcha"_ to be aware of: **`magic-sdk/react-native`** must be imported **before `web3`** \(this restriction does not apply to `ethers`\). For example:

```typescript
// 🚫 Bad!
import Web3 from 'web3';
import { Magic } from '@magic-sdk/react-native';

// ✅ Good!
import { Magic } from '@magic-sdk/react-native';
import Web3 from 'web3';
```

👉 **Learn more about integrating** [**Ethereum**](../../advanced/ethereum/)\*\*\*\*

