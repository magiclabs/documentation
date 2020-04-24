# User Module

The User Module and it's members are accessible on the Magic SDK instance by the `user` property.

```typescript
import { Magic } from 'magic-sdk';

const m = new Magic('API_KEY');

m.user;
m.user.getIdToken;
m.user.generateIdToken;
m.user.getMetadata;
m.user.isLoggedIn;
m.user.logout;
```

## Members

{% page-ref page="getidtoken.md" %}

{% page-ref page="generateidtoken.md" %}

{% page-ref page="getmetadata.md" %}

{% page-ref page="isloggedin.md" %}

{% page-ref page="logout.md" %}



