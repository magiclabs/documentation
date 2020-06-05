# generateIdToken

### **Public Methods**

| Methods |
| :--- |
| **generateIdToken**\( \_ configuration: GenerateIdTokenConfiguration, response: \(\_ resp: Response&lt;String&gt;\) ~~_-_~~&gt; Void \) |
| **generateIdToken**\(\_ configuration: GenerateIdTokenConfiguration\) -&gt; Promise &lt;String&gt; |

### Returns

`Promise<String>`: Base64-encoded string representation of a JSON tuple representing `[proof, claim]` 

### Example

```swift
import MagicSDK

class MagicViewController: UIViewController {

    let magic = Magic.shared
    
    func generateIdToken() {
        guard let magic = magic else { return }
        
        // Assuming user is logged in 
        let configuration = GenerateIdTokenConfiguration(lifespan: 900, attachment: "none")
        
        magic.user.generateIdToken(configuration, response: { response in
            guard let token = response.result 
                else { return print("Error:", response.error.debugDescription) }
            print("Result", token)
        })
    }
}
```

### **Associated Class**

`GenerateIdTokenConfiguration(lifespan: Int = 900, attachment: String = 'none')`

* `lifespan` \(Number\) : will set the lifespan of the generated token. Defaults to 900s \(15 mins\)
* `attachment` \(String\) : will set a signature of serialized data in the generated token. Defaults to `"none"`

