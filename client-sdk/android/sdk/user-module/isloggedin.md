---
description: Checks if a user is currently logged in to the Magic IOS SDK.
---

# isLoggedIn

### **Public Methods**

| Methods |
| :--- |
| **isLoggedIn**\(\): CompletableFuture&lt;IsLoggedInResponse&gt; |

### Returns

`IsLoggedInResponse: Response<Boolean>()`

### Example

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
    
    // ⭐️Assuming user is logged in 
    fun isLoggedIn(v: View) {
        val completable = magic.user.isLoggedIn()
        completable.whenComplete { response: IsLoggedInResponse?, error: Throwable? ->
            if (response != null && response.result) {
                Log.d("Magic", "You're Logged In")
            }
            if (error != null) {
                // handle Error
            }
        }
    }
}
```



