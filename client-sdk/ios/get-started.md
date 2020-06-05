# 🚀 Get Started

## 📦 Installation

It's easy to install Magic SDK if you manage your iOS dependencies using [CocoaPods](http://cocoapods.org/). If you don't have an existing [Podfile](https://guides.cocoapods.org/syntax/podfile.html), run the following command to create one:

```text
$ pod init
```

Simply add `pod 'MagicSDK'`  to your `Podfile`:

```bash
target 'TARGET_NAME' do
  use_frameworks!

  pod 'MagicSDK'
end
```

Run the following command:

```text
$ pod install
```

To update pods to latest, run the following command

```text
$ pod update
```

## ⚡️ Creating an SDK Instance

```swift
import UIKit
import MagicSDK

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        
        // assign the newly created Magic instance to shared property
        Magic.shared = Magic(apiKey: "API_KEY")
        
        // do any other necessary launch configuration
    }
    return true
}
```

{% hint style="info" %}
All the examples are written in Swift. Objective-C examples will be added soon. 
{% endhint %}

