# 🚀 Get Started

### 📦 Installation

To interact with the Ethereum blockchain, Magic Android SDK integrates [`Web3j`](https://github.com/web3j/web3j) __as sub dependency. 

Add the following dependencies in `build.gradle`

```java
dependencies {
    implementation 'link.magic:magic-android:0.3.0'
    implementation 'org.web3j:core:4.6.0-android' // Not required
    implementation 'org.web3j:geth:4.6.0-android' // Only for personal Sign
}
```

## ⚡️ Initializing Provider

{% hint style="info" %}
The following example is using **Kotlin 1.3**. Android demo will be open-sourced soon. 

You may use Android Studio to convert Java to Kotlin or vise versa. 
{% endhint %}

```swift
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    lateinit var web3j: Web3j
    lateinit var gethWeb3j: Geth
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY")
        web3j = Web3j.build(magic.rpcProvider)
        gethWeb3j = Geth.build(magic.rpcProvider)
    }
}
```

## ☁️ Use Different Networks

### Choose Different Testnet

```kotlin
magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY", Magic.Network.Mainnet)
```

### Configure Custom Nodes

```kotlin
magic = Magic(this, "YOUR_PUBLISHABLE_API_KEY", CustomNodeConfiguration("https://alchemy.io"))
```

{% hint style="danger" %}
Don't set the custom nodes to local IP address \(E.x. "http://127.0.0.1"\), because local IP will point to the network environment inside mobile device / simulator. Try accessible IP address in the same Wifi/Internet Environment \(E.x. "http://10.0.0.93:3000"\)
{% endhint %}

#### Associated Class

`CustomNodeConfiguration(rpcUrl: String, chainId: Int?)`

* `rpcUrl` :Your own node URL
* `chainId` : Your own node's chainId 

`Magic.EthNetwork`

```swift
 enum class EthNetwork {
        Mainnet, Kovan, Rinkeby, Ropsten
 }
```

