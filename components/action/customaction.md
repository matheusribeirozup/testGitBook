# CustomAction

Finally, there is the **CustomAction** class. This class will define custom actions, such as an action that creates a customized `Dialog`. In this way, Action **is an interface** that allows you to define actions that can be performed by `Widget`s. This is your structure:

```kotlin
data class CustomAction(
    val name: String,
    val data: Map<String, String>
) : Action
```

### name

CustomAction **definition name**.

### data

Attribute in map format with key and value in `String` for **sending data for the action**.

