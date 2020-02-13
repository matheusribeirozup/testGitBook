# Form



```kotlin
data class Form (
    val path: String,
    val method: FormMethodType,
    val child: ServerDrivenComponent
) : ServerDrivenComponent
```

### path



### method



```kotlin
enum class FormMethodType {
    GET,
    POST,
    PUT,
    DELETE
}
```

### child

| Attribute | Description | Required |
| :--- | :--- | :--- |
| `path` |  | yes |
| `method` |  | yes |
| `child` |  | yes |

