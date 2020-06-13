# 👤 Get User Info

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
        web3j = Web3j.build(magic.rpcProvider)
    }
    
    // ⭐️ After user is successfully authenticated
    fun getAccount(){
        try {
            val accounts = web3j.ethAccounts().sendAsync()

            accounts.whenComplete { accRepsonse: EthAccounts?, error: Throwable? ->
                if (error != null) {
                    Log.e("MagicError", error.localizedMessage)
                }
                if (accRepsonse != null && !accRepsonse.hasError()) {
                    account = accRepsonse.accounts[0]
                    Log.d("Magic", "Your address is $account")
                }
            }
        } catch (e: Exception) {
            Log.e("Error", e.localizedMessage)
        }
    }
}
```

