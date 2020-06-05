---
description: Logs out the currently authenticated Magic user
---

# logout

### **Public Methods**

| Methods |
| :--- |
| **logout**\( response: \(\_ resp: Response&lt;Bool&gt;\) ~~_-_~~&gt; Void \) |
| **logout**\(\) -&gt; Promise &lt;Bool&gt; |

### Returns

`Promise<Bool>`

### Example

```swift
import MagicSDK

class MagicViewController: UIViewController {

    let magic = Magic.shared
    
    func logout() {
        guard let magic = magic else { return }
        
        // Assuming user is logged in 
        magic.user.logout(response: { response in
            guard let result = response.result 
                else { return print("Error:", response.error.debugDescription) }
            print("Result", result)
        })
    }
}
```

