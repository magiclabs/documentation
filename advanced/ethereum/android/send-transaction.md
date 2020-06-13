# 💸 Send Transaction

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
    fun sendTransaction(v: View) {
        try {
            val value: BigInteger =  Convert.toWei("0.5", Convert.Unit.ETHER).toBigInteger()
            val transaction = createEtherTransaction(account, BigInteger("1"), BigInteger("21000"), BigInteger("21000"), account, value)
            val receipt = web3j.ethSendTransaction(transaction).send()
            Log.d("Transaction complete: " + receipt.transactionHash)
        } catch (e: Exception) {
            Log.e("Error", e.localizedMessage)
        }
    }
}
```

