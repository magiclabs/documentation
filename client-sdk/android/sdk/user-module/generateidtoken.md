---
description: Generates a Decentralized Id Token with optional serialized data.
---

# generateIdToken

### **Public Methods**

| Methods |
| :--- |
| **generateIdToken**\(configuration: GenerateIdTokenConfiguration?\): CompletableFuture&lt;GenerateIdTokenResponse&gt; |

### Returns

`GenerateIdTokenResponse: Response<String>()`

Base64-encoded string representation of a JSON tuple representing `[proof, claim]`

### **Example**

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
    
    // ⭐️Assuming user is logged in 
    fun generateIdToken(v: View) {
        val configuration = GenerateIdTokenConfiguration(lifespan = 900, attachment = "none")
        val completable = magic.user.generateIdToken(configuration)
        
        completable.whenComplete { response: GenerateIdTokenResponse?, error: Throwable? ->
            if (response != null) {
                Log.d("Magic", response.result)
            } else {
                // handle Error            
            }
        }
    }
}
```

### Associated Class

`GenerateIdTokenConfiguration(attachment: String? = "none", lifespan: Long? = 900)`

* `lifespan` : will set the lifespan of the generated token. Defaults to 900s \(15 mins\)
* `attachment`  : will set a signature of serialized data in the generated token. Defaults to `"none"`



