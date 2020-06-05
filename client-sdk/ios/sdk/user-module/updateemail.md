---
description: initiates the update email flow that allows a user to change to a new email
---

# updateEmail

### **Public Methods**

| Methods |
| :--- |
| updateEmail\( \_ configuration: UpdateEmailConfiguration, response: \(\_ resp: Response&lt;Bool&gt;\) ~~_-_~~&gt; Void \) |
| updateEmail\(\_ configuration: UpdateEmailConfiguration\) -&gt; Promise &lt;Bool&gt; |

### Returns

`Promise<Bool>`: The promise resolves with a true boolean value if update email is successful and rejects with a specific error code if the request fails. 

### Example

```swift
import MagicSDK

class MagicViewController: UIViewController {

    let magic = Magic.shared

    // Initiates the flow to update a user's current email to a new one.
    func updateEmail() {
    
        guard let magic = magic else { return }
        
        // Assuming user is logged in 
        let configuration = UpdateEmailConfiguration(email: "new_user_email@example.com")
        magic.user.updateEmail(configuration, response: { response in
            guard let result = response.result 
                else { return print("Error:", response.error.debugDescription) }
            print("Result", result)
        })
    }
}
```

### **Associated Class**

`UpdateEmailConfiguration(showUI: Bool = true, email: String)`

* `email`  The user email to update with.
* `showUI` If `true`, show an out-of-the-box pending UI while the request is in flight.

