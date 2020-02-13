# Text



```kotlin
data class Text(
    val text: String,
    val style: String? = null,
    val alignment: TextAlignment? = null
) : Widget()
```

### text



### style



### alignment



```kotlin
enum class TextAlignment {
    LEFT,
    CENTER,
    RIGHT
}
```

* `LEFT`



* `CENTER`



* `RIGHT`

