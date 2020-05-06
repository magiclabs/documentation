# Migrating From Fortmatic

This short guide highlights some of the differences between the **soon-to-be-deprecated** [**Fortmatic Whitelabel API**](https://docs.fortmatic.com/whitelabel-sdk) **and Magic SDK.**

Developers should plan to migrate existing `Fortmatic.Phantom` implementations to Magic SDK **before October 30, 2020.**

## Prerequisite

* ​[Install client-side JavaScript SDK​](../get-started.md#installation)

## Imports

{% tabs %}
{% tab title="Fortmatic" %}
```typescript
import Fortmatic from 'fortmatic';
```
{% endtab %}

{% tab title="Magic" %}
```typescript
import { Magic } from 'magic-sdk';
```
{% endtab %}
{% endtabs %}

## Constructing the SDK Instance

{% tabs %}
{% tab title="Fortmatic" %}
```typescript
const fmPhantom = new Fortmatic.Phantom('API_KEY');

// With custom Ethereum node configuration:
const fmPhantom = new Fortmatic.Phantom('API_KEY', 'mainnet');
const fmPhantom = new Fortmatic.Phantom('API_KEY', { rpcUrl: 'https://...' });
```
{% endtab %}

{% tab title="Magic" %}
```typescript
const magic = new Magic('API_KEY');

// With custom Ethereum node configuration:
const magic = new Magic('API_KEY', { network: 'mainnet' });
const magic = new Magic('API_KEY', {
  network: { rpcUrl: 'https://...' }
});
```
{% endtab %}
{% endtabs %}

## Logging in

{% tabs %}
{% tab title="Fortmatic" %}
```typescript
fmPhantom.loginWithMagicLink({ email: 'hello@magic.link' });
```
{% endtab %}

{% tab title="Magic" %}
```typescript
magic.auth.loginWithMagicLink({ email: 'hello@magic.link' });
```
{% endtab %}
{% endtabs %}

## Constructing a Web3 Instance

{% tabs %}
{% tab title="Fortmatic" %}
```typescript
new Web3(fmPhantom.getProvider());
```
{% endtab %}

{% tab title="Magic" %}
```typescript
new Web3(magic.rpcProvider);
```
{% endtab %}
{% endtabs %}

