---
description: Getting started with the Magic client-side JavaScript SDK
---

# 🚀 Get Started

## 📦 Installation

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

{% tab title="CDN" %}
```markup
<script src="https://cdn.jsdelivr.net/npm/magic-sdk/dist/magic.js"></script>
```
{% endtab %}
{% endtabs %}

## ⚡️ Creating an SDK Instance

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY'); // ✨
```
{% endtab %}

{% tab title="CommonJS" %}
```typescript
const { Magic } = require('magic-sdk');

const m = new Magic('API_KEY'); // ✨
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Examples for the client-side JavaScript SDK use the ES Module/TypeScript pattern by default.
{% endhint %}

