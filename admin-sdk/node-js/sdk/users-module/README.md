# Users Module

The Users Module and it's members are accessible on the Magic Admin SDK instance by the `users` property.

```typescript
const { Magic } = require('@magic-sdk/admin');

const mAdmin = new Magic('SECRET_API_KEY');

mAdmin.users;
mAdmin.users.logoutByIssuer;
mAdmin.users.logoutByPublicAddress;
mAdmin.users.logoutByToken;
mAdmin.users.getMetadataByIssuer;
mAdmin.users.getMetadataByPublicAddress;
mAdmin.users.getMetadataByToken;
```

## Members

{% page-ref page="logoutbyissuer.md" %}

{% page-ref page="logoutbypublicaddress.md" %}

{% page-ref page="logoutbytoken.md" %}

{% page-ref page="getmetadatabyissuer.md" %}

{% page-ref page="getmetadatabypublicaddress.md" %}

{% page-ref page="getmetadatabytoken.md" %}

