# 📜 Smart Contract

## Solidity Contract

In this example, we'll be demonstrating how to use Magic with ethers.js or web3.js to interact with Solidity smart contracts. The simple Hello World contract allows anyone to read and write a message to it.

```javascript
pragma solidity ^0.5.10;

contract HelloWorld {

  string public message;
    
  constructor(string memory initMessage) public {
    message = initMessage;
  }

  function update(string memory newMessage) public {
    message = newMessage;
  }
}
```

## Ethers.js

### Deploy Contract

```javascript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

const signer = provider.getSigner();

const contractABI = '[{"constant":false,"inputs":[{"name":"newMessage","type":"string"}],"name":"update","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"message","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"initMessage","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]';
const contractByteCode = "0x608060405234801561001057600080fd5b5060405161047f38038061047f8339818101604052602081101561003357600080fd5b81019080805164010000000081111561004b57600080fd5b8281019050602081018481111561006157600080fd5b815185600182028301116401000000008211171561007e57600080fd5b5050929190505050806000908051906020019061009c9291906100a3565b5050610148565b828054600181600116156101000203166002900490600052602060002090601f016020900481019282601f106100e457805160ff1916838001178555610112565b82800160010185558215610112579182015b828111156101115782518255916020019190600101906100f6565b5b50905061011f9190610123565b5090565b61014591905b80821115610141576000816000905550600101610129565b5090565b90565b610328806101576000396000f3fe608060405234801561001057600080fd5b5060043610610053576000357c0100000000000000000000000000000000000000000000000000000000900480633d7403a314610058578063e21f37ce14610113575b600080fd5b6101116004803603602081101561006e57600080fd5b810190808035906020019064010000000081111561008b57600080fd5b82018360208201111561009d57600080fd5b803590602001918460018302840111640100000000831117156100bf57600080fd5b91908080601f016020809104026020016040519081016040528093929190818152602001838380828437600081840152601f19601f820116905080830192505050505050509192919290505050610196565b005b61011b6101b0565b6040518080602001828103825283818151815260200191508051906020019080838360005b8381101561015b578082015181840152602081019050610140565b50505050905090810190601f1680156101885780820380516001836020036101000a031916815260200191505b509250505060405180910390f35b80600090805190602001906101ac92919061024e565b5050565b60008054600181600116156101000203166002900480601f0160208091040260200160405190810160405280929190818152602001828054600181600116156101000203166002900480156102465780601f1061021b57610100808354040283529160200191610246565b820191906000526020600020905b81548152906001019060200180831161022957829003601f168201915b505050505081565b828054600181600116156101000203166002900490600052602060002090601f016020900481019282601f1061028f57805160ff19168380011785556102bd565b828001600101855582156102bd579182015b828111156102bc5782518255916020019190600101906102a1565b5b5090506102ca91906102ce565b5090565b6102f091905b808211156102ec5760008160009055506001016102d4565b5090565b9056fea265627a7a7230582003ae1ef5a63bf058bfd2b31398bdee39d3cbfbb7fbf84235f4bc2ec352ee810f64736f6c634300050a0032";
const contractFactory = new ethers.ContractFactory(
  contractABI,
  contractByteCode,
  signer
);

// Deploy contract with "Hello World!" in the constructor
const contract = await contractFactory.deploy("Hello World!");

// Wait for deployment to finish
const receipt = await contract.deployed();
```

### Read From Contract

```javascript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

const signer = provider.getSigner();

const contractABI = '[{"constant":false,"inputs":[{"name":"newMessage","type":"string"}],"name":"update","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"message","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"initMessage","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]';
const contractAddress = "0x8b211dfebf490a648f6de859dfbed61fa22f35e0";
const contract = new ethers.Contract(
  contractAddress,
  contractABI,
  signer
);

// Read message from smart contract
const message = await contract.message();
```

### Write to Contract

```javascript
import { Magic } from 'magic-sdk';
import { ethers } from 'ethers';

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const provider = new ethers.providers.Web3Provider(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

const signer = provider.getSigner();

const contractABI = '[{"constant":false,"inputs":[{"name":"newMessage","type":"string"}],"name":"update","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"message","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"initMessage","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]';
const contractAddress = "0x8b211dfebf490a648f6de859dfbed61fa22f35e0";
const contract = new ethers.Contract(
  contractAddress,
  contractABI,
  signer
);

// Send transaction to smart contract to update message
const tx = await contract.update("NEW_MESSAGE");

// Wait for transaction to finish
const receipt = await tx.wait();
```

## Web3.js

{% hint style="warning" %}
Example is using **`web3@1.2.0`** or later version.
{% endhint %}

### Deploy Contract

```javascript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const contractABI = '[{"constant":false,"inputs":[{"name":"newMessage","type":"string"}],"name":"update","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"message","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"initMessage","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]';
const contractByteCode = "0x608060405234801561001057600080fd5b5060405161047f38038061047f8339818101604052602081101561003357600080fd5b81019080805164010000000081111561004b57600080fd5b8281019050602081018481111561006157600080fd5b815185600182028301116401000000008211171561007e57600080fd5b5050929190505050806000908051906020019061009c9291906100a3565b5050610148565b828054600181600116156101000203166002900490600052602060002090601f016020900481019282601f106100e457805160ff1916838001178555610112565b82800160010185558215610112579182015b828111156101115782518255916020019190600101906100f6565b5b50905061011f9190610123565b5090565b61014591905b80821115610141576000816000905550600101610129565b5090565b90565b610328806101576000396000f3fe608060405234801561001057600080fd5b5060043610610053576000357c0100000000000000000000000000000000000000000000000000000000900480633d7403a314610058578063e21f37ce14610113575b600080fd5b6101116004803603602081101561006e57600080fd5b810190808035906020019064010000000081111561008b57600080fd5b82018360208201111561009d57600080fd5b803590602001918460018302840111640100000000831117156100bf57600080fd5b91908080601f016020809104026020016040519081016040528093929190818152602001838380828437600081840152601f19601f820116905080830192505050505050509192919290505050610196565b005b61011b6101b0565b6040518080602001828103825283818151815260200191508051906020019080838360005b8381101561015b578082015181840152602081019050610140565b50505050905090810190601f1680156101885780820380516001836020036101000a031916815260200191505b509250505060405180910390f35b80600090805190602001906101ac92919061024e565b5050565b60008054600181600116156101000203166002900480601f0160208091040260200160405190810160405280929190818152602001828054600181600116156101000203166002900480156102465780601f1061021b57610100808354040283529160200191610246565b820191906000526020600020905b81548152906001019060200180831161022957829003601f168201915b505050505081565b828054600181600116156101000203166002900490600052602060002090601f016020900481019282601f1061028f57805160ff19168380011785556102bd565b828001600101855582156102bd579182015b828111156102bc5782518255916020019190600101906102a1565b5b5090506102ca91906102ce565b5090565b6102f091905b808211156102ec5760008160009055506001016102d4565b5090565b9056fea265627a7a7230582003ae1ef5a63bf058bfd2b31398bdee39d3cbfbb7fbf84235f4bc2ec352ee810f64736f6c634300050a0032";
const contract = new web3.eth.Contract(JSON.parse(contractABI));

// Deploy contract with "Hello World!" in the constructor and wait to finish
const contractInstance = await contract
  .deploy({
    data: contractByteCode,
    arguments: ["Hello World!"]
  })
  .send({
    from: fromAddress
  });
```

### Read From Contract

```javascript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const contractABI = '[{"constant":false,"inputs":[{"name":"newMessage","type":"string"}],"name":"update","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"message","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"initMessage","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]';
const contractAddress = "0x8b211dfebf490a648f6de859dfbed61fa22f35e0";
const contract = new web3.eth.Contract(JSON.parse(contractABI), contractAddress);

// Read message from smart contract
const message = await contract.methods.message().call();
```

### Write to Contract

```javascript
import { Magic } from "magic-sdk";
import Web3 from "web3";

const magic = new Magic("YOUR_PUBLISHABLE_API_KEY");
const web3 = new Web3(magic.rpcProvider);

// ⭐️ After user is successfully authenticated

// Get user's Ethereum public address
const fromAddress = (await web3.eth.getAccounts())[0];

const contractABI = '[{"constant":false,"inputs":[{"name":"newMessage","type":"string"}],"name":"update","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"message","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"initMessage","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]';
const contractAddress = "0x8b211dfebf490a648f6de859dfbed61fa22f35e0";
const contract = new web3.eth.Contract(JSON.parse(contractABI), contractAddress);

// Send transaction to smart contract to update message and wait to finish
const receipt = await contract.methods
  .update("NEW_MESSAGE")
  .send({ from: fromAddress });
```

