---
description: Logs out the currently authenticated Magic user
---

# logout

### **Public Methods**

| Methods |
| :--- |
| **logout**\(\): CompletableFuture&lt;LogoutResponse&gt; |

### Returns

`LogoutResponse: Response<Boolean>()` 

### Example

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
    
    // ⭐️Assuming user is logged in 
    fun logout(v: View) {
        val completable = magic.user.logout()
        completable.whenComplete { response: LogoutResponse?, error: Throwable? ->
            if (response != null && response.result) {
                Log.d("Magic", "You're logged out!")
            }
            if (error != null) {
                // handle Error
            }
        }
    }
}
```

