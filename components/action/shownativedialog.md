# ShowNativeDialog

The `ShowNativeDialog` class will **show dialogues natively**, such as an error alert indicating alternative flows, business system errors and others. This is your structure:

```kotlin
data class ShowNativeDialog(
    val title: String,
    val message: String,
    val buttonText: String
) : Action
```

{% hint style="info" %}
All attributes for this component are mandatory.
{% endhint %}

### title

Attribute that corresponds to the **title** of the `Dialog`.

### message

Attribute that is shown in the `Dialog` **message**.

### buttonText

**Name of the button** present in the `Dialog`.

