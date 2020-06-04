# PromiEvents

Magic SDK provides a flexible interface for handling methods which encompass multiple "stages" of an action. `Promises` returned by Magic SDK resolve when a flow has reached finality, but certain methods also contain life-cycle events that dispatch throughout. We refer to this interface as a **`PromiEvent`**. There is prior art to inspire this approach in Ethereum's [Web3](https://web3js.readthedocs.io/en/v1.2.1/callbacks-promises-events.html) standard.

**`PromiEvent`** is a portmanteau of `Promise` and [`EventEmitter`](https://github.com/primus/eventemitter3). Browser and React Native SDK methods return this object type, which is a native JavaScript `Promise` overloaded with `EventEmitter` methods. This value can be `awaited` in modern `async/await` code, or you may register event listeners to handle method-specific life-cycle hooks. Each `PromiEvent` contains the following default event types:

* **`"done"`**: Called when the `Promise` resolves. This is equivalent to `Promise.then`.
* **`"error"`**: Called if the `Promise` rejects. This is equivalent to `Promise.catch`.
* **`"settled"`**: Called when the `Promise` either resolves or rejects. This is equivalent to `Promise.finally`.

Look for additional event types documented near the method they relate to. Events are strongly-typed by TypeScript to offer developer hints and conveniant IDE auto-complete.

### Example

It's possible to chain `Promise` methods like `.then` and `.catch` with `EventEmitter` methods like `.on` and `.once` seamlessly. There are no limitations to either chaining interface, they all return an `awaitable` `PromiEvent`, as expected. The [species](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/species) of the object type is always a native JavaScript `Promise`.

```typescript
const req = magic.auth.loginWithMagicLink({ email: 'hello@magic.link' });

req
  .on("email-sent", () => { /* ... */ })
  .then(DIDToken => { /* ... */ })
  .once("email-not-deliverable", () => { /* ... */ })
  .catch(error => { /* ... */ })
  .on("error", error => { /* ... */ });
```

