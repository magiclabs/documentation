# 🗄 SDK

### Returns

All Magic functions are asynchronous calls. They will return a [CompletableFuture](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CompletableFuture.html) object, which resolves the results in a Response class. 

To get the result without blocking the UI thread, call `CompletableFuture.whenComplete` to wait for the results asynchronously.

```kotlin
val result = magic.auth.loginWithMagicLink("hello@example.com")
    
result.whenComplete { response: DIDToken?, error: Throwable? ->
    if (error != null) {
       //Handle Error
    }
    if (response != null && !response.hasError()) {
        Log.d("Magic", "You're logged in." + response.result)
    } else {
        Log.d("login", "Not Logged in")
    }
}
```

For the full implementation of Response class, please check [here](https://github.com/web3j/web3j/blob/master/core/src/main/java/org/web3j/protocol/core/Response.java).



