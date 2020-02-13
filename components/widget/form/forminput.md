# FormInput



```kotlin
data class FormInput(
    val name: String,
    val required: Boolean? = null,
    val validator: String? = null,
    val errorMessage: String? = null,
    val child: InputWidget
) : ServerDrivenComponent
```

### name



### required



### validator



### errorMessage



### child



```kotlin
interface InputWidget : ServerDrivenComponent
```



