# 👤 Get User Info

```swift
import MagicSDK
import Web3
import PromiseKit

class Web3ViewController: UIViewController {

    var web3 = Web3(provider: Magic.shared.rpcProvider)
    
    // ⭐️ After user is successfully authenticated
    @IBOutlet weak var accountLabel: UILabel!
    
    func getAccount() {
    
        firstly {
            // Get user's Ethereum public address
            web3.eth.accounts()
        }.done { accounts -> Void in
            if let account = accounts.first {
                // Set to UILa
                self.accountLabel.text = account.hex(eip55: false)
            } else {
                print("No Account Found")
            }
        }.catch { error in
            print("Error loading accounts and balance: \(error)")
        }
    }
}
```

