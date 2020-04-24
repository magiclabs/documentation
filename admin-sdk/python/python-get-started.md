# 🚀 Get Started

## 📦 Installation

{% tabs %}
{% tab title="PIP" %}
```text
pip install magic-admin
```
{% endtab %}

{% tab title="Conda" %}
```text
conda install magic-admin
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Current SDK is built with Python3.6. Testing for Python3.6+ will be added soon. If you are interested in using the SDK with the earlier versions of Python \(ex: 2.7+\), please create a ticket in this [repo](https://github.com/fortmatic/magic-admin-python) and let us know :\)
{% endhint %}

## ⚡️ Creating an SDK Instance

{% tabs %}
{% tab title="Instantiation" %}
```python
from magic_admin import Magic

# Pass your API secret key directly to the Magic.
magic = Magic(api_secret_key='<YOUR_API_SECRET_KEY>')

# Or add an environment variable, `MAGIC_API_SECRET_KEY`
magic = Magic()
```
{% endtab %}
{% endtabs %}



