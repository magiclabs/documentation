# 💸 Send Transaction

## Ethers.js

```javascript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

const signer = provider.getSigner();

const destination = "0xE0cef4417a772512E6C95cEf366403839b0D6D6D";
const amount = ethers.utils.parseEther(1); // Convert 1 ether to wei

// Submit transaction to the blockchain
const tx = await signer.sendTransaction({
  to: destination,
  value: amount
});

// Wait for transaction to be mined
const receipt = await tx.wait();
```

## Web3.js

{% hint style="warning" %}
Example is using **`web3@1.2.0`** or later version.
{% endhint %}

```javascript
import { Magic } from 'magic-sdk';
import Web3 from 'web3';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const destination = "0xE0cef4417a772512E6C95cEf366403839b0D6D6D";
const amount = web3.utils.toWei(1); // Convert 1 ether to wei

// Submit transaction to the blockchain and wait for it to be mined
const receipt = await web3.eth.sendTransaction({
  from: fromAddress,
  to: destination,
  value: amount
})
```

