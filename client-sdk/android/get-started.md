# 🚀 Get Started

## 📦 Installation

Magic SDK is available in `mavenCentral` . Simply add the following line to the `build.gradle` in your Android project

```bash
dependencies {
    implementation 'link.magic:magic-android:0.3.0'
}
```

Sync the project with new dependencies settings.

## ⚡️ Creating an SDK Instance

```kotlin
open class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
}
```

{% hint style="info" %}
All the examples are written in Kotlin. 
{% endhint %}

