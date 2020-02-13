# ScrollView



```kotlin
data class ScrollView(
    val children: List<ServerDrivenComponent>,
    val scrollDirection: ScrollAxis? = null,
    val scrollBarEnabled: Boolean? = null
) : ServerDrivenComponent
```

### children



### scrollDirection



### scrollBarEnabled



```kotlin
enum class ScrollAxis {
    VERTICAL,
    HORIZONTAL
}
```

* `VERTICAL`



* `HORIZONTAL`



