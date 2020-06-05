# ✏️ Sign Message

Magic IOS SDK extends the functionality from Web3.swift to allow developers to sign Typed Data. Make sure to `import MagicSDK` while using these functions.

{% tabs %}
{% tab title="Eth Sign" %}
```swift
import MagicSDK
import Web3
import PromiseKit

class ViewController: UIViewController {

    let web3 = Web3(provider: Magic.shared.rpcProvider)
    var account: EthereumAddress?
    
    func ethSign() {
        guard let account = self.account else { return }
        
        let message = try! EthereumData("Hello World".data(using: .utf8)!)
        web3.eth.sign(from: account, message: message).done({ result in
            print(result.hex())
        })
    }
}    
```
{% endtab %}

{% tab title="Sign Typed Data Legacy \(V1\)" %}
```swift
import MagicSDK
import Web3
import PromiseKit

class Web3ViewController: UIViewController {

    let web3 = Web3(provider: Magic.shared.rpcProvider)
    var account: EthereumAddress?
    
    func SignTypedDataLegacy() {
        guard let account = self.account else { return }
        
        let payload = EIP712TypedDataLegacyFields(type: "string", name: "Hello from Magic Labs", value: "This message will be signed by you")

        web3.eth.signTypedDataLegacy(account: account, data: [payload]).done({ result in
            print(result.hex())
        })
    }
}    
```
{% endtab %}

{% tab title="Sign Typed Data \(EIP 712\)" %}
```swift
import MagicSDK
import Web3

class Web3ViewController: UIViewController {

    let web3 = Web3(provider: Magic.shared.rpcProvider)
    var account: EthereumAddress?
    
    func SignTypedData() {
        guard let account = self.account else { return }
            
        do {
            let json = """
                {"types":{"EIP712Domain":[{"name":"name","type":"string"},{"name":"version","type":"string"},{"name":"verifyingContract","type":"address"}],"Greeting":[{"name":"contents","type":"string"}]},"primaryType":"Greeting","domain":{"name":"Magic","version":"1","verifyingContract":"0xE0cef4417a772512E6C95cEf366403839b0D6D6D"},"message":{"contents":"Hello, from Magic!"}}
            """.data(using: .utf8)!
            let typedData = try JSONDecoder().decode(EIP712TypedData.self, from: json)
                
            web3.eth.signTypedData(account: account, data: typedData).done({ result in
                print(result.hex())
            })
        } catch {
            print(error.localizedDescription)
        }
    }
}    
```
{% endtab %}
{% endtabs %}



