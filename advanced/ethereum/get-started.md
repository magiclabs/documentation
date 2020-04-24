# 🚀 Get Started

## 📦 Installation

To interact with the Ethereum blockchain, you can use _either_ `ethers.js` or `web3.js` libraries with Magic.

{% hint style="info" %}
If you are already familiar with Ethereum application development, you can skip straight to our kitchen sink examples:

👉 [**Ethers.js Example**](https://go.magic.link/example-ethers)  
👉 [**Web3.js Example**](https://go.magic.link/example-web3)\*\*\*\*
{% endhint %}

### Ethers.js

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save ethers
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add ethers
```
{% endtab %}

{% tab title="CDN" %}
```markup
<script src="https://cdn.ethers.io/scripts/ethers-v4.min.js"></script>
```
{% endtab %}
{% endtabs %}

### Web3.js

{% tabs %}
{% tab title="NPM" %}
```bash
npm install --save web3
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add web3
```
{% endtab %}

{% tab title="CDN" %}
```markup
<script src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>
```
{% endtab %}
{% endtabs %}

## ⚡️ Initializing Provider

{% hint style="warning" %}
Ethereum provider is only supported in **`magic-sdk@1.0.1`** or later version.
{% endhint %}

### Ethers.js

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

// Test key defaults to "rinkeby", live key defaults to "mainnet"
const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);
```
{% endtab %}

{% tab title="CommonJS" %}
```typescript
const { Magic } = require('magic-sdk');
const ethers = require('ethers');

// Test key defaults to "rinkeby", live key defaults to "mainnet"
const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);
```
{% endtab %}
{% endtabs %}

### Web3.js

{% tabs %}
{% tab title="ES Modules/TypeScript" %}
```typescript
import { Magic } from 'magic-sdk';
import Web3 from 'web3';

// Test key defaults to "rinkeby", live key defaults to "mainnet"
const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider); // Or window.web3 = ...
```
{% endtab %}

{% tab title="CommonJS" %}
```typescript
const { Magic } = require('magic-sdk');
const Web3 = require('web3');

// Test key defaults to "rinkeby", live key defaults to "mainnet"
const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider); // Or window.web3 = ...
```
{% endtab %}
{% endtabs %}

## ☁️ Use Different Networks

### Choose Different Testnet

```javascript
const magic = new Magic("YOUR_PUBLISHABLE_API_KEY", {
  network: "ropsten" // Supports "rinkeby", "ropsten", "kovan"
});
```

### Configure Custom Nodes

```javascript
const customNodeOptions = {
  rpcUrl: 'http://127.0.0.1:7545', // Your own node URL
  chainId: 1011 // Your own node's chainId 
}

// Setting network to localhost blockchain
const magic = new Magic('YOUR_PUBLISHABLE_API_KEY', { network: customNodeOptions });
```

