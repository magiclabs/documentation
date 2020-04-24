# 📱 React Native

## 🚀 Welcome to the Magic React Native JS SDK

The Magic **React Native** JavaScript SDK is distributed **from the same NPM package as our**[ **Browser JavaScript SDK**](../browser-js/)**!** This is your entry-point to secure, passwordless authentication for your iOS or Android-based React Native app. This guide will cover some important topics for getting started with client-side APIs and to make the most of Magic's features.

**👉 Go to our** [**Getting Started**](get-started.md) **tutorial to begin your integration**

{% hint style="info" %}
Magic can support both server-based or serverless web applications. It is up to the developers to implement the [Admin SDK](../../admin-sdk/node-js/) to validate the DID Token.
{% endhint %}

### React Native and Browser JS share the same API

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
```javascript
const { Magic } = require('magic-sdk/react-native');
                                  /* ^^^^^^^^^^^^ */
                                /* Notice this part! */
```
{% endtab %}
{% endtabs %}

### Looking for a server-side API? Start with one of these:

{% page-ref page="../../admin-sdk/node-js/" %}

{% page-ref page="../../admin-sdk/python/" %}



