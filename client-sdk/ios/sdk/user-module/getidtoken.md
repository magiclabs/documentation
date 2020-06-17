---
description: >-
  Generates a Decentralized Id Token which acts as a proof of authentication to
  resource servers.
---

# getIdToken

### **Public Methods**

| Methods |
| :--- |
| **getIdToken**\( \_ configuration: GenerateIdTokenConfiguration? = nil, response: \(\_ resp: Response&lt;String&gt;\) ~~_-_~~&gt; Void \) |
| **getIdToken**\(\_ configuration: GenerateIdTokenConfiguration? = nil\) -&gt; Promise &lt;String&gt; |

### Returns

`Promise<String>`: Base64-encoded string representation of a JSON tuple representing `[proof, claim]`

### Example

```swift
import MagicSDK

class MagicViewController: UIViewController {

    let magic = Magic.shared
    
    func getIdToken() {
        guard let magic = magic else { return }
        
        // Assuming user is logged in 
        let configuration = GetIdTokenConfiguration(lifespan: 900)
        
        magic.user.getIdToken(configuration, response: { response in
            guard let token = response.result 
                else { return print(response.error.debugDescription) }
            print(token)
        })
    }
}
```

### Associated Class

`GetIdTokenConfiguration(lifespan: Int = 900)` 

* `lifespan?` \(Int\): will set the lifespan of the generated token. Defaults to 900s \(15 mins\)



