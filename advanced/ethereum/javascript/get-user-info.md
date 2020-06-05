# 👤 Get User Info

## Ethers.js

```javascript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

const signer = provider.getSigner();

// Get user's Ethereum public address
const address = await signer.getAddress();

// Get user's balance in ether
const balance = ethers.utils.formatEther(
  await provider.getBalance(userAddress) // Balance is in wei
);
```

## Web3.js

{% hint style="warning" %}
Example is using **`web3@1.2.0`** or later version.
{% endhint %}

```javascript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const address = (await web3.eth.getAccounts())[0];

// Get user's balance in ether
const balance = web3.utils.fromWei(
  await web3.eth.getBalance(address) // Balance is in wei
);
```

