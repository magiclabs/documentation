# 🚀 Get Started

## 📦 Installation

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save @magic-sdk/admin
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add @magic-sdk/admin
```
{% endtab %}
{% endtabs %}

## ⚡️ Creating an SDK Instance

{% tabs %}
{% tab title="CommonJS" %}
```typescript
const { Magic } = require('@magic-sdk/admin');

const mAdmin = new Magic('SECRET_API_KEY'); // ✨
```
{% endtab %}

{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from '@magic-sdk/admin';

const mAdmin = new Magic('SECRET_API_KEY'); // ✨
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Examples for the server-side JavaScript SDK use the CommonJS pattern by default.
{% endhint %}



