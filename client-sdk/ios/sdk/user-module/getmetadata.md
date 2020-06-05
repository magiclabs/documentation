---
description: Retrieves information for the authenticated user.
---

# getMetadata

### **Public Methods**

| Methods |
| :--- |
| **getMetadata**\( response: \(\_ resp: Response&lt;String&gt;\) ~~_-_~~&gt; Void \) |
| **getMetadata**\(\) -&gt; Promise &lt;String&gt; |

### Returns

`UserMetadata`: containing the issuer, email and cryptographic [public address ](https://support.blockchain.com/hc/en-us/articles/360000951966-Public-and-private-keys)of the authenticated user.

```swift
public struct UserMetadata: MagicResponse {
    public let issuer: String?
    public let publicAddress: String?
    public let email: String?
}
```

* `issuer` : The Decentralized ID of the user.  In server-side use-cases, we recommend this value to be used as the user ID in your own tables.
* `email` : Email address of the authenticated user.
* `publicAddress`: The authenticated user's public address \(a.k.a.: public key\). Currently, this value is associated with the Ethereum blockchain. 

### Example

```swift
import MagicSDK

class MagicViewController: UIViewController {

    let magic = Magic.shared
    
    func getMetadata() {
        guard let magic = magic else { return }
        
        // Assuming user is logged in 
        magic.user.getMetadata(response: { response in
            guard let metadata = response.result
                else { return print("Error:", response.error.debugDescription) }
            print("Result", metadata)
        })
    }
}
```

