# Token Module

The Token Module and its members are accessible on the Magic Admin SDK instance by the `token` property.

```typescript
const { Magic } = require('@magic-sdk/admin');

const mAdmin = new Magic('SECRET_API_KEY');

mAdmin.token;
mAdmin.token.getIssuer;
mAdmin.token.getPublicAddress;
mAdmin.token.decode;
mAdmin.token.validate;
```

## Members

{% page-ref page="getissuer.md" %}

{% page-ref page="getpublicaddress.md" %}

{% page-ref page="decode.md" %}

{% page-ref page="validate.md" %}



