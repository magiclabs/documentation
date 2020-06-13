# ✏️ Sign Message

Magic Android SDK extends the functionality from Web3j to allow developers to sign Typed Data. You may find it in `magic.web3jSigExt`

{% tabs %}
{% tab title="Personal Sign" %}
```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    lateinit var gethWeb3j: Geth
    
    // ⭐️ After user is successfully authenticated
    private var account: String? = null
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
        web3j = Web3j.build(magic.rpcProvider)
        gethWeb3j = Geth.build(magic.rpcProvider)
    }
    
    fun personSign(view: View) {
        val message = "Hello from Magic!!!"
        val personalSign: PersonalSign = gethWeb3j.personalSign(
                message, account, "password")
                .send()
        Log.d("Magic", "Signed Message: " + personalSign.signedMessage)

        // Recover Message
        val recovered = gethWeb3j.personalEcRecover(message, personalSign.signedMessage).send()
        Log.d("Magic", "Recovered Address: " + recovered.recoverAccountId)
    }
}
```
{% endtab %}

{% tab title="Sign TypedData Legacy \(V1\)" %}
```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    lateinit var gethWeb3j: Geth
    
    // ⭐️ After user is successfully authenticated
    private var account: String? = null
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
    }
    
    // Sign with EIP712 Data Field 
    fun signTypedDataLegacy(v: View) {
        val list = listOf(
                EIP712TypedDataLegacyFields("string", "Hello from Magic", "This message will be signed by you"),
                EIP712TypedDataLegacyFields("uint32", "Here is a number", "90210")
        )
        val signature = magic.web3jSigExt.signTypedDataLegacy(account, list).send()
        Log.d("Magic", signature.result)
    }
    
    // Sign with JSON String
    fun signTypedDataLegacyJson(v: View) {
        val jsonString = "[{\"type\":\"string\",\"name\":\"Hello from Magic\",\"value\":\"This message will be signed by you\"},{\"type\":\"uint32\",\"name\":\"Here is a number\",\"value\":\"90210\"}]"
        val signature = magic.web3jSigExt.signTypedDataLegacy(account, jsonString).send()
        Log.d("Magic", signature.result)
    }
}
```
{% endtab %}

{% tab title="Sign TypedData \(V3\)" %}
```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    lateinit var gethWeb3j: Geth
    
    // ⭐️ After user is successfully authenticated
    private var account: String? = null
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
    }
    
    fun signTypedData(v: View) {
        val jsonString = "{\"types\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"verifyingContract\",\"type\":\"address\"}],\"Order\":[{\"name\":\"makerAddress\",\"type\":\"address\"},{\"name\":\"takerAddress\",\"type\":\"address\"},{\"name\":\"feeRecipientAddress\",\"type\":\"address\"},{\"name\":\"senderAddress\",\"type\":\"address\"},{\"name\":\"makerAssetAmount\",\"type\":\"uint256\"},{\"name\":\"takerAssetAmount\",\"type\":\"uint256\"},{\"name\":\"makerFee\",\"type\":\"uint256\"},{\"name\":\"takerFee\",\"type\":\"uint256\"},{\"name\":\"expirationTimeSeconds\",\"type\":\"uint256\"},{\"name\":\"salt\",\"type\":\"uint256\"},{\"name\":\"makerAssetData\",\"type\":\"bytes\"},{\"name\":\"takerAssetData\",\"type\":\"bytes\"}]},\"domain\":{\"name\":\"0x Protocol\",\"version\":\"2\",\"verifyingContract\":\"0x35dd2932454449b14cee11a94d3674a936d5d7b2\"},\"message\":{\"exchangeAddress\":\"0x35dd2932454449b14cee11a94d3674a936d5d7b2\",\"senderAddress\":\"0x0000000000000000000000000000000000000000\",\"makerAddress\":\"0x338be8514c1397e8f3806054e088b2daf1071fcd\",\"takerAddress\":\"0x0000000000000000000000000000000000000000\",\"makerFee\":\"0\",\"takerFee\":\"0\",\"makerAssetAmount\":\"97500000000000\",\"takerAssetAmount\":\"15000000000000000\",\"makerAssetData\":\"0xf47261b0000000000000000000000000d0a1e359811322d97991e03f863a0c30c2cf029c\",\"takerAssetData\":\"0xf47261b00000000000000000000000006ff6c0ff1d68b964901f986d4c9fa3ac68346570\",\"salt\":\"1553722433685\",\"feeRecipientAddress\":\"0xa258b39954cef5cb142fd567a46cddb31a670124\",\"expirationTimeSeconds\":\"1553808833\"},\"primaryType\":\"Order\"}"
        val signature = magic.web3jSigExt.signTypedData(account, jsonString).send()
        Log.d("Magic", "Signature: " + signature.result)
    }
}
```
{% endtab %}

{% tab title="Sign TypedData V4" %}
```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    lateinit var gethWeb3j: Geth
    
    // ⭐️ After user is successfully authenticated
    private var account: String? = null
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
    }

    fun signTypedDataV4(v: View) {
        val jsonString = "{\"domain\":{\"chainId\":1,\"name\":\"Ether Mail\",\"verifyingContract\":\"0xCcCCccccCCCCcCCCCCCcCcCccCcCCCcCcccccccC\",\"version\":\"1\"},\"message\":{\"contents\":\"Hello, Bob!\",\"from\":{\"name\":\"Cow\",\"wallets\":[\"0xCD2a3d9F938E13CD947Ec05AbC7FE734Df8DD826\",\"0xDeaDbeefdEAdbeefdEadbEEFdeadbeEFdEaDbeeF\"]},\"to\":[{\"name\":\"Bob\",\"wallets\":[\"0xbBbBBBBbbBBBbbbBbbBbbbbBBbBbbbbBbBbbBBbB\",\"0xB0BdaBea57B0BDABeA57b0bdABEA57b0BDabEa57\",\"0xB0B0b0b0b0b0B000000000000000000000000000\"]}]},\"primaryType\":\"Mail\",\"types\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"},{\"name\":\"verifyingContract\",\"type\":\"address\"}],\"Group\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"members\",\"type\":\"Person[]\"}],\"Mail\":[{\"name\":\"from\",\"type\":\"Person\"},{\"name\":\"to\",\"type\":\"Person[]\"},{\"name\":\"contents\",\"type\":\"string\"}],\"Person\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"wallets\",\"type\":\"address[]\"}]}}"
        val signature = magic.web3jSigExt.signTypedDataV4(account, jsonString).send()
        Log.d("Magic", "Signature: " + signature.result)
    }
}
```
{% endtab %}
{% endtabs %}

