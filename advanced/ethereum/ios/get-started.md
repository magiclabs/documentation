# 🚀 Get Started

## 📦 Installation

To interact with the Ethereum blockchain, Magic iOS SDK embeds __[`Web3.swift`](https://github.com/Boilertalk/Web3.swift) as sub dependency. No more extra dependency is needed.

## ⚡️ Initializing Provider

{% hint style="info" %}
Following example is using Swift 5 with XCode 11. IOS demo will be open-sourced soon.
{% endhint %}

```swift
// AppDelegate.swift

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

```swift
// ViewController.swift

import UIKit
import MagicSDK
import Web3

class Web3ViewController: UIViewController {

    let web3 = Web3(provider: Magic.shared.rpcProvider)
}

```

## ☁️ Use Different Networks

### Choose Different Testnet

```swift
// AppDelegate.swift
import MagicSDK

func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

    // assign to Magic singleton 
    Magic.shared = Magic("YOUR_PUBLISHABLE_API_KEY", EthNetwork.rinkeby);
    
    return true
}
```

### Configure Custom Nodes

```swift
// AppDelegate.swift
import MagicSDK

// assign to Magic singleton 
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

    let config = CustomNodeConfiguration(rpcUrl: "https://alchemy.io", chainId: 1)
    Magic.shared = Magic(apiKey: "API_KEY", customNode: config);
    
    return true
}
```

{% hint style="danger" %}
Don't set the custom nodes to local IP address \(E.x. "http://127.0.0.1"\). Local IP will point to the network environment inside mobile device / simulator 
{% endhint %}

#### Associated Class

`CustomNodeConfiguration(rpcUrl: String, chainId: Int?)`

* `rpcUrl` :Your own node URL
* `chainId` : Your own node's chainId 

`EthNetwork`

```swift
public enum EthNetwork: String {
    case mainnet
    case kovan
    case rinkeby
    case ropsten
}
```

