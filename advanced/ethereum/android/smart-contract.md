# 📜 Smart Contract

## Solidity Contract

In this example, we'll be demonstrating how to use Magic with Web3j to interact with Solidity smart contracts. The simple Hello World contract allows anyone to read and write a message to it.

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

### Create a Kotlin/Java Contract Class from ABI

web3j supports the auto-generation of smart contract function wrappers in Java from Solidity ABI files.

To get started, you must have two files

* ABI JSON file `<Contract>.json`
* ByteCode file `<Contract>.bin`

#### Install web3j cli-tool

```
$ curl -L https://get.web3j.io | sh
```

You may need to install a JDK to support this library

![](../../../.gitbook/assets/image%20%283%29.png)

After it has been installed to your computer, you may run the following command to check

```text
$ web3j version
```

### Create the contract class

```bash
$ web3j solidity generate -a=./path/to/<Contract>.json -b=./path/to/<Contract>.bin -o=/output/path/ -p={packageName}
```

You’ll find a `Contract.java` file created in your output directory above. Put this file in your project, and no more changes are needed.

For more detail about this section. Please check the following link  
[https://web3j.readthedocs.io/en/latest/smart\_contracts.html\#solidity-smart-contract-wrappers](https://web3j.readthedocs.io/en/latest/smart_contracts.html#solidity-smart-contract-wrappers)

## Contract Functions

When deploying contract or building contract using web3j library, Magic offers `MagicTxnManager` class as a default `TransactionManager` that helps you to avoid dealing with private keys or credentials that Contract class requires. 

### Deploy Contract

```kotlin
import link.magic.demo.contract.Contract // This is the contract class you created above

class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    
    // ⭐️ After user is successfully authenticated
    private var account: String? = null
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
        web3j = Web3j.build(magic.rpcProvider)
    }
    
    fun deployContract(view: View) {
        try {
            val price = BigInteger.valueOf(22000000000L)
            val limit = BigInteger.valueOf(4300000)
            val gasProvider = StaticGasProvider(price, limit)
            val contract = Contract.deploy(
                    web3j,
                    account?.let { MagicTxnManager(web3j, it) },
                    gasProvider,
                    "HELLO_WORLD_FROM_ANDROID"
            ).send()
            Log.d("Magic", "Deploy to" + contract.contractAddress)
        } catch (e: Exception) {
            Log.e("E", "error", e)
        }
    }
} 
```

### Read From Contract

```kotlin
fun contractRead(view: View) { 
    try {
        val price = BigInteger.valueOf(22000000000L)
        val limit = BigInteger.valueOf(4300000)
        val gasProvider = StaticGasProvider(price, limit)
        
        // Contract in Rinkeby testnet
        val contract = ExampleContract.load("0x6a2d321a3679b1b3c8a19b84e41abd11763a8ab5", web3j, account?.let { MagicTxnManager(web3j, it) }, gasProvider)
        if (contract.isValid) {
            val ethCall = contract.message().send()
            Log.d("Magic", ethCall.toString())
        } else {
            throw Error("contract not valid")
        }
    } catch (e: Exception) {
        Log.e("E", "error", e)
    }
}
```

### Write to Contract

```kotlin
fun contractWrite(view: View) {
    try {
        val price = BigInteger.valueOf(22000000000L)
        val limit = BigInteger.valueOf(4300000)
        val gasProvider = StaticGasProvider(price, limit)
        
        // Contract in Rinkeby testnet
        val contract = ExampleContract.load("0x6a2d321a3679b1b3c8a19b84e41abd11763a8ab5", web3j, account?.let { MagicTxnManager(web3j, it) }, gasProvider)
        if (contract.isValid) {
            val ethCall = contract.update("NEW_MESSAGE_FROM_ANDROID").send()
            Log.d("Magic", ethCall.toString())
        } else {
            throw Error("contract not valid")
        }
    } catch (e: Exception) {
        Log.e("E", "error", e)
    }
}  
```

