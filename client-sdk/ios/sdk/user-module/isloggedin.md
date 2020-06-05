---
description: Checks if a user is currently logged in to the Magic IOS SDK.
---

# isLoggedIn

### **Public Methods**

| Methods |
| :--- |
| **getMetadata**\( response: \(\_ resp: Response&lt;Bool&gt;\) ~~_-_~~&gt; Void\) |
| **getMetadata**\(\) -&gt; Promise &lt;Bool&gt; |

### Returns

`Promise<Bool>`

### Example

```swift
import MagicSDK

class MagicViewController: UIViewController {

    let magic = Magic.shared
    
    func isLoggedIn() {
        guard let magic = magic else { return }
        
        magic.user.isLoggedIn(response: { response in
            guard let result = response.result 
                else { return print("Error:", response.error.debugDescription) }
            print("Result", result)
        })
    }
}
```



