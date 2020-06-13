---
description: >-
  Authenticate a user passwordlessly using a "magic link" sent to the specified
  user's email address.
---

# loginWithMagicLink

### **Public Methods**

| Methods |
| :--- |
| **loginWithMagicLink**\(configuration: LoginWithMagicLinkConfiguration\): CompletableFuture&lt;DIDToken&gt; |

### Returns

`DIDToken: Response<String>()` 

The function resolves upon authentication request success and rejects with a specific error code if the request fails. The resolved value is a Decentralized ID token with a default 15-minute lifespan.

### Example

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
    }
    
   fun login(v: View) {
        val email = findViewById<EditText>(R.id.emailInput)
        val configuration = LoginWithMagicLinkConfiguration(email.text.toString())
        val completable = magic.auth.loginWithMagicLink(configuration)

        // Logging in
        completable.whenComplete { response: DIDToken?, error: Throwable? ->
            if (error != null) {
                // Handle error
            }
            if (response != null && !response.hasError()) {
                Log.d("Magic", "You're logged in!" + response.result)
            } else {
                Log.d("Magic", "Not Logged in")
            }
        }
    }
}
```

### Associated Class

`LoginWithMagicLinkConfiguration(showUI: Boolean? = true, email: String)`

* `email`  The user email to log in with.
* `showUI` If `true`, show an out-of-the-box pending UI while the request is in flight.

