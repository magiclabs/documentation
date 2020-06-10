---
description: >-
  Decentralized ID (DID) tokens are used as cryptographically-generated proofs
  that are used to manage user access to your application's resource server.
---

# 👤 Decentralized ID

## What is a Decentralized ID \(DID\) Token?

By adapting W3C's [Decentralized Identifiers](https://w3c-ccg.github.io/did-primer/) \(DID\) protocol, the **DID token** created by the Magic client-side SDK \(see [`getIdToken`](client-sdk/browser-js/sdk/user-module/getidtoken.md)\) leverages the [Ethereum](https://ethereum.org/) blockchain and [elliptic curve cryptography](https://en.wikipedia.org/wiki/Elliptic-curve_cryptography) to generate  verifiable proofs of identity and authorization. These proofs are encoded in a lightweight, digital signature that can be shared between client and server to manage permissions; protect routes and resources, or authenticate users.

The DID token is encoded as a Base64 JSON string tuple representing **`[proof, claim]`**:

* `proof`: A digital signature that proves the validity of the given `claim`.
* `claim`: Unsigned data the user asserts. This should equal the `proof` after Elliptic Curve recovery.

```javascript
const claim = JSON.stringify({ ... }); // Data representing the user's access
const proof = sign(claim); // Sign data with Ethereum's `personal_sign` method
const DIDToken = btoa(JSON.stringify([proof, claim]));
```

## Decentralized ID Token Specification

| Key | Description |
| :--- | :--- |
| `iat` | Issued at timestamp \(UTC in seconds\). |
| `ext` | Expiration timestamp \(UTC in seconds\). |
| `nbf` | Not valid before timestamp \(UTC in seconds\). |
| `iss` | Issuer \(the signer, the "user"\). This field is represented as a [Decentralized Identifier](https://w3c-ccg.github.io/did-primer/#the-format-of-a-did) populated with the user's Ethereum public key. |
| `sub` | The "subject" of the request. This field is currently populated with the user's _Magic entity ID_. Note: this is separate from the user's Ethereum public key. |
| `aud` | Identifies the project space. This field is represented as a [Decentralized Identifier](https://w3c-ccg.github.io/did-primer/#the-format-of-a-did) populated with a UUID. In the future, this field will represent the _application's Magic entity ID._ |
| `add` | An encrypted signature of arbitrary, serialized data. The usage of this field is up to the developer and use-case dependent. It's handy for validating information passed between client and server. _The  raw data must be known to the developer in order to recover the token!_ |
| `tid` | Unique token identifier. |

### Generating a Decentralized ID Token \(Pseudo-code\)

```typescript
// Construct the user's claim
const claim = JSON.stringify({
    iat: Math.floor(Date.now() / 1000),
    ext: Math.floor(Date.now() / 1000) + lifespan,
    iss: `did:ethr:${account.address}`,
    sub: subject,
    aud: `did:magic:${uuid()}`,
    nbf: Math.floor(Date.now() / 1000),
    tid: uuid(),
});

// Sign the claim with the user's private key
// (this way the claim is verifiable and impossible to forge).
const proof = sign(claim);

// Encode the DIDToken so it can be transported over HTTP.
const DIDToken = btoa(JSON.stringify([proof, claim]));
```

