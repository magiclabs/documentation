---
description: Getting started with the Magic React Native JavaScript SDK
---

# 🚀 Get Started

## 📦 Installation

{% hint style="info" %}
React Native is available as of **`magic-sdk@1.1.1`**
{% endhint %}

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save magic-sdk
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add magic-sdk
```
{% endtab %}
{% endtabs %}

## ⚡️ Creating an SDK Instance

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk/react-native';

const m = new Magic('API_KEY'); // ✨
```
{% endtab %}

{% tab title="CommonJS" %}
```typescript
const { Magic } = require('magic-sdk/react-native');

const m = new Magic('API_KEY'); // ✨
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Examples for the React Native JavaScript SDK use the ES Module/TypeScript pattern by default.
{% endhint %}

## 📥 Importing Magic for React Native

The React Native SDK **has access to all the same methods and properties from Browser JS**, with one notable difference—the **`import`**! React Native-compatible code is namespaced like so:

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk/react-native';
                              /* ^^^^^^^^^^^^ */
                            /* Notice this part! */
```
{% endtab %}

{% tab title="CommonJS" %}
```typescript
const { Magic } = require('magic-sdk/react-native');
                                  /* ^^^^^^^^^^^^ */
                                /* Notice this part! */
```
{% endtab %}
{% endtabs %}

## 🖼 Rendering Magic

React Native exposes one additional member on your Magic instance: `Relayer`.

`Relayer` is a React component that manages all communication with the Magic service. This is analogous to the `<iframe>` in Browser JS.

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
import { Magic } from 'magic-sdk/react-native';

// ✅ Good!
import { Magic } from 'magic-sdk/react-native';
import Web3 from 'web3';
```

👉 **Learn more about integrating** [**Ethereum**](../../advanced/ethereum/)\*\*\*\*

