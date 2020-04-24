# ✏️ Sign Message

## Ethers.js

{% tabs %}
{% tab title="Personal Sign" %}
```typescript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

const signer = provider.getSigner();

const originalMessage = "YOUR_MESSAGE";

const signedMessage = await signer.signMessage(originalMessage);
```
{% endtab %}

{% tab title="Sign Typed Data v1" %}
```typescript
import { Magic } from "magic-sdk";
import { ethers } from "ethers";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = await signer.getAddress();

const originalMessage = [
  {
    type: "string",
    name: "fullName",
    value: "John Doe"
  },
  {
    type: "uint32",
    name: "userId",
    value: "1234"
  }
];
const params = [originalMessage, fromAddress];
const method = "eth_signTypedData";

const signedMessage = await signer.provider.send(method, params);
```
{% endtab %}

{% tab title="Sign Typed Data v3" %}
```javascript
import { Magic } from "magic-sdk";
import { ethers } from "ethers";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = await signer.getAddress();

const originalMessage = {
  types: {
    EIP712Domain: [
      {
        name: "name",
        type: "string"
      },
      {
        name: "version",
        type: "string"
      },
      {
        name: "verifyingContract",
        type: "address"
      }
    ],
    Greeting: [
      {
        name: "contents",
        type: "string"
      }
    ]
  },
  primaryType: "Greeting",
  domain: {
    name: "Magic",
    version: "1",
    verifyingContract: "0xE0cef4417a772512E6C95cEf366403839b0D6D6D"
  },
  message: {
    contents: "Hello, from Magic!"
  }
};
const params = [fromAddress, originalMessage];
const method = "eth_signTypedData_v3";

const signedMessage = await signer.provider.send(method, params);
```
{% endtab %}
{% endtabs %}

## Web3.js

{% hint style="warning" %}
Example is using **`web3@1.2.0`** or later version.
{% endhint %}

{% tabs %}
{% tab title="Personal Sign" %}
```typescript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const originalMessage = "YOUR_MESSAGE";

const signedMessage = await web3.eth.personal.sign(
  originalMessage,
  fromAddress
);
```
{% endtab %}

{% tab title="Sign Typed Data v1" %}
```typescript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const originalMessage = [
  {
    type: "string",
    name: "fullName",
    value: "John Doe"
  },
  {
    type: "uint32",
    name: "userId",
    value: "1234"
  }
];
const params = [originalMessage, fromAddress];
const method = "eth_signTypedData";

const signedMessage = await web3.currentProvider.sendAsync({
  id: 1,
  method,
  params,
  fromAddress
});
```
{% endtab %}

{% tab title="Sign Typed Data v3" %}
```javascript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const originalMessage = {
  types: {
    EIP712Domain: [
      {
        name: "name",
        type: "string"
      },
      {
        name: "version",
        type: "string"
      },
      {
        name: "verifyingContract",
        type: "address"
      }
    ],
    Greeting: [
      {
        name: "contents",
        type: "string"
      }
    ]
  },
  primaryType: "Greeting",
  domain: {
    name: "Magic",
    version: "1",
    verifyingContract: "0xE0cef4417a772512E6C95cEf366403839b0D6D6D"
  },
  message: {
    contents: "Hello, from Magic!"
  }
};
const params = [fromAddress, originalMessage];
const method = "eth_signTypedData_v3";

const signedMessage = await web3.currentProvider.sendAsync({
  id: 1,
  method,
  params,
  fromAddress
});
```
{% endtab %}
{% endtabs %}

