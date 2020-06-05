---
description: Configure and construct your Magic SDK instance.
---

# Constructor

### Magic

| Public constructors |  |
| :--- | :--- |
| **Magic**\(apiKey: String\) | Construct a Magic instance with **publishable** API Key retrieved from the [Magic Dashboard](https://dashboard.magic.link) |
| **Magic**\(apiKey: String, network: EthNetwork\) | Construct a Magic instance with publishable Key and Ethereum network  |
| **Magic**\(apiKey: String, customNode: CustomNodeConfiguration\) | Construct a Magic instance with publishable Key and Custom Node configuration  |

### Example

In `AppDelegate`

```swift
import MagicSDK
import UIKit

@UIApplicationMain
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

    // assign the newly created Magic instance to shared property
    // Test key defaults to "rinkeby", live key defaults to "mainnet"
    Magic.shared = Magic("YOUR_PUBLISHABLE_API_KEY");
    
    return true
}
```

