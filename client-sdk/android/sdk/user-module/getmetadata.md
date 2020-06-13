---
description: Retrieves information for the authenticated user.
---

# getMetadata

### **Public Methods**

| Methods |
| :--- |
| **getMetadata**\(\): CompletableFuture&lt;GetMetadataResponse&gt; |

### Returns

`GetMetadataResponse: Response<UserMetadataResponse>()`

The `Completable` containing the issuer, email and cryptographic [public address ](https://support.blockchain.com/hc/en-us/articles/360000951966-Public-and-private-keys)of the authenticated user.

```kotlin
class UserMetadataResponse {
    var issuer: String? = null
    var publicAddress: String? = null
    var email: String? = null
}
```

* `issuer` : The Decentralized ID of the user.  In server-side use-cases, we recommend this value to be used as the user ID in your own tables.
* `email` : Email address of the authenticated user.
* `publicAddress`: The authenticated user's public address \(a.k.a.: public key\). Currently, this value is associated with the Ethereum blockchain. 

### Example

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
    
    // ⭐️Assuming user is logged in 
    fun getMetadata(v: View) {
        val completable = magic.user.getMetadata()
        completable.whenComplete { response: GetMetadataResponse?, error: Throwable? ->
            if (response != null) {
                Log.d("Magic", "Email: " + response.result.email)
                Log.d("Magic", "Issuer: " + response.result.issuer)
            } else {
                // handle Error
            }
        }
    }
}
```



