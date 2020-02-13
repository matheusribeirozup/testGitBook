---
description: Getting started with Beagle for Android
---

# Beagle Android

## Setting up the dependency

The **first step** is to set the Zup's repository \(using the **credentials** bellow\) to download Beagle's Library.  

```go
// Add it in your root build.gradle at the end of repositories:
allprojects {
    repositories {
        google()
        jcenter()
        maven {
            credentials {
                // user@password with read only access
                username "beagle"
                password "Xq7wAh3xDkGN"
            }
            url 'https://repo-iti.zup.com.br/repository/beagle-jars-all/'
        }
    }
}
```

The **second step** is to include Beagle as a dependency into your dependency manager, for example, as a Gradle dependency:

```go
// Add in your app level dependency
ext.beagle_version = "0.0.17-alpha"

dependencies {
    implementation "br.com.zup.beagle:android:$beagle_version"
    kapt "br.com.zup.beagle:android-processor:$beagle_version"
}
```

The **third step** is to create a `BeagleConfig` ****class and annotate this class with the `@BeagleComponent` and provide the attributes below:

```kotlin
@BeagleComponent
class AppBeagleConfig : BeagleConfig {
    override val environment: Environment get() = Environment.DEBUG // return the current build state of your app
    override val baseUrl: String get() = "https://myapp.server.com/" // return the base url based on your environment
}
```

{% hint style="warning" %}
It's very important to notice that Beagle expects classes that are annotated with `@BeagleComponent` to have empty constructors.
{% endhint %}

The **fourth step** is to initialise Beagle in your `Application` class. To do that you just need to build your app once and that will trigger Beagle into creating the `BeagleSetup` class \(you don't have to create it, it is automatically created by  Beagle\).

After that you must call the `BeagleSetup().init(this)` in your `Application` class at the `onCreate` method as listed below and you will be almost good to go. There is just one more step.

```kotlin
class MyApplication : Application() {

    // It is mandatory to Initialize Beagle at the "onCreate method" in the class that extends the application class
    override fun onCreate() {
        super.onCreate()

        BeagleSetup().init(this)
    }
}
```

The **fifth and last step** is to authorize Beagle to use the local resources in your Android App. To do this, you must create a `AppDesignSystem` class that extends the `DesignSystem` class as bellow:

```kotlin
// This class is used by the RenderEngine in order to define the styles configured at the application.
// It must extend DesignSystem.
// These are the styles the AppDesignSystem implements: buttonStyle, toolbarStyle, textAppearance, theme and image

@BeagleComponent
class AppDesignSystem : DesignSystem {
    override fun toolbarStyle(name: String): Int {
        return R.style.toolbar
    }

    override fun buttonStyle(name: String): Int {
        return when (name) {
            "DesignSystem.Button.Confirm" -> R.style.DesignSystem_Button_Confirm
            else -> R.style.DesignSystem_Button_Default
        }
    }

    override fun image(name: String): Int {
        return when(name) {
            "full_star" -> R.drawable.ic_full_star
            "half_star" -> R.drawable.ic_half_star
            else -> R.drawable.ic_empty_star
        }
    }

    override fun theme(): Int {
        return R.style.AppTheme
    }

    override fun textAppearance(name: String): Int {
        return when (name) {
            "DesignSystem.Text.H1" -> R.style.DesignSystem_Text_H1
            "DesignSystem.Text.H2" -> R.style.DesignSystem_Text_H2
            "DesignSystem.Text.H3" -> R.style.DesignSystem_Text_H3
            else -> R.style.DesignSystem_Text_Default
        }
    }
}
```

{% hint style="info" %}
When the `DesignSystem` class is extended it will require that certain methods are implemented. It is mandatory to implement all these for Beagle to work properly.
{% endhint %}

And now **you are good to go!** Please read the details below since it will address some important information that you might need later when using Beagle.

**a\)** `@BeagleComponent` responsibility is  to register the following classes:   
     `CustomActionHandler`, `DeepLinkHandler`, `HttpClient`, `DesignSystem` , `BeagleConfig`  
**b\)** `@RegisterWidget`  is responsible to register all `widgets` at the application  
**c\)** `@RegisterValidator` is responsible to register all `Validators` at the `application`   
**d\)** Classes annotated with `@BeagleComponent` and `@RegisterValidator` cannot implement parameters on its constructors. Beagle expects constructors at these classes to be empty.

