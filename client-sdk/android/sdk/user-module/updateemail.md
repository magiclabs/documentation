---
description: initiates the update email flow that allows a user to change to a new email
---

# updateEmail

### **Public Methods**

| Methods |
| :--- |
| **updateEmail**\(configuration: UpdateEmailConfiguration\) -&gt; CompletableFuture&lt;UpdateEmailResponse&gt; |

### Returns

`UpdateEmailResponse: Response<Boolean>()`

The `Completable` resolves with a true boolean value if update email is successful and rejects with a specific error code if the request fails. 

### Example

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
    
    // ⭐️Assuming user is logged in 
    fun updateEmail(v: View) {

        val configuration = UpdateEmailConfiguration("new_user_email@example.com")
        val completable = magic.user.updateEmail(configuration)
        completable.whenComplete { response: UpdateEmailResponse?, error: Throwable? ->
            if (response != null) {
                Log.d("Magic", response.result.toString()) // "True"
            } else {
                // handle error
            }
        }
    }
}
```

### **Associated Class**

`UpdateEmailConfiguration(showUI: Boolean? = true, email: String)`

* `email`  The user email to update with.
* `showUI` If `true`, show an out-of-the-box pending UI while the request is in flight.

