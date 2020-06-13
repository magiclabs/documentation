---
description: >-
  The Magic class is the entry-point to the Magic SDK. It must be instantiated
  with a Magic publishable key.
---

# Constructor

## Magic

| Public constructors |  |
| :--- | :--- |
| **Magic**\(context: Context, apiKey: String\) | Construct a Magic instance with **publishable** API Key retrieved from the [Magic Dashboard](https://dashboard.magic.link) |
| **Magic**\(context:Context, apiKey: String, network: Magic.EthNetwork\) | Construct a Magic instance with publishable Key and Ethereum network  |
| **Magic**\(context:Context, apiKey: String, customNode: CustomNodeConfiguration\) | Construct a Magic instance with publishable Key and Custom Node configuration  |

## Example

```kotlin
import link.magic.android.Magic

open class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
}
```

