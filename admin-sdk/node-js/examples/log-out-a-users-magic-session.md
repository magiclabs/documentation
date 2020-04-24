# Log Out a User's Magic Session

Sometimes you will find yourself needing to log your users out from the server-side. This provides a small example of how to do so.

## Prerequisite

* [Install server-side JavaScript SDK](../get-started.md#installation)

## Step 1: Invalidate the user session

{% tabs %}
{% tab title="With public address" %}
```javascript
app.post('/logout', (req: any, res: any) => {
  const userPublicAddress = magicAdmin.token.getPublicAddress(
    req.headers.authorization
  );
  magicAdmin.users.logoutByPublicAddress(userPublicAddress);
});
```
{% endtab %}

{% tab title="With DID Token" %}
```javascript
app.post('/logout', (req: any, res: any) => {
  magicAdmin.token.invalidate(req.headers.authorization);
});
```
{% endtab %}
{% endtabs %}

