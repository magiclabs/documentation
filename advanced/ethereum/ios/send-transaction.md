# 💸 Send Transaction

```swift
import MagicSDK
import Web3

class Web3ViewController: UIViewController {

    var web3 = Web3(provider: Magic.shared.rpcProvider)
    var account: EthereumAddress?
    
    // ⭐️ After user is successfully authenticated
    func sendTransaction() {
    
        guard let account = self.account else { return }
        
        // Construct a transaction
        let transaction = EthereumTransaction(
            from: account, // from Get User Info section
            to: EthereumAddress(hexString: "0xE0cef4417a772512E6C95cEf366403839b0D6D6D"), 
            value: EthereumQuantity(quantity: 1.gwei)
        )
        
        // Submit transaction to the blockchain
        web3.eth.sendTransaction(transaction: transaction).done { (transactionHash) in
            print(transactionHash.hex())
        }.catch { error in
            print(error.localizedDescription)
        }
    }
}
```

