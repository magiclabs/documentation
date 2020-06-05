# 🗄 SDK

Magic offers functions that returns promisified result by using PromiseKit. For more detail about promiseKit in iOS, please check [PromiseKit](https://github.com/mxcl/PromiseKit)

```swift
magic.auth.loginWithMagicLink(configuration, response: { response in 
    guard let result = response.result else { return print("Error:", response.error.debugDescription) }
    print("Result", result)
})
```

is equivalent to the follow function call

```swift
magic.auth.loginWithMagicLink(configuration).done({ result in 
    print("Result", result) // DIDToken
}).catch({
    print("Error:", error) // handle Error
})
```

Once the authentication request is complete, the closure will be executed with either success or failure state in the result. If you choose to return as a promise, the promise will resolve with success state or reject when failure state is reached.

