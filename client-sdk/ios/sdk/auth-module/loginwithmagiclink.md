---
description: >-
  Authenticate a user passwordlessly using a "magic link" sent to the specified
  user's email address.
---

# loginWithMagicLink

### **Public Methods**

| Methods |
| :--- |
| **loginWithMagicLink**\( \_ configuration: LoginWithMagicLinkConfiguration, response: \(\_ resp: Response&lt;String&gt;\) -&gt; Void \) |
| **loginWithMagicLink**\(\_ configuration: LoginWithMagicLinkConfiguration\) -&gt; Promise &lt;String&gt; |

### Returns

`Promise<string | null>`: The promise resolves upon authentication request success and rejects with a specific error code if the request fails. The resolved value is a Decentralized ID token with a default 15-minute lifespan.

### Example

{% tabs %}
{% tab title="Closure" %}
```swift
import MagicSDK

class LoginViewController: UIViewController {

    @IBOutlet weak var emailInput: UITextField!
    let magic = Magic.shared
    
    @IBAction func login() {
        guard let magic = magic else { return }
        guard let email = self.emailInput.text else { return }
        
        let configuration = LoginWithMagicLinkConfiguration(email: email)
        
        magic.auth.loginWithMagicLink(configuration, response: { response in 
            guard let token = response.result 
                else { return print("Error:", response.error.debugDescription) }
            print("Result", token)
        })
    }
}
```
{% endtab %}

{% tab title="Promise" %}
```swift
import MagicSDK

class LoginViewController: UIViewController {

    @IBOutlet weak var emailInput: UITextField!
    let magic = Magic.shared
    
    @IBAction func login() {
        guard let magic = magic else { return }
        
        let configuration = LoginWithMagicLinkConfiguration(email: self.emailInput.text!)
        
        magic.auth.loginWithMagicLink(configuration).done({ result in 
            print(result) // DIDToken
        }).catch({
            print(error) // handle Error
        })
    }
}
```
{% endtab %}
{% endtabs %}

### Associated Class

`LoginWithMagicLinkConfiguration(showUI: Bool = true, email: String)`

* `email`  The user email to log in with.
* `showUI` If `true`, show an out-of-the-box pending UI while the request is in flight.

