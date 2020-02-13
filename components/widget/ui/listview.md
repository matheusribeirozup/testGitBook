# ListView



```kotlin
data class ListView(
    val rows: List<ServerDrivenComponent>,
    val remoteDataSource: String? = null,
    val loadingState: ServerDrivenComponent? = null,
    val direction: ListDirection = ListDirection.VERTICAL
) : ServerDrivenComponent
```

### rows



### remoteDataSource



### loadingState



### direction



```kotlin
enum class ListDirection {
    VERTICAL,
    HORIZONTAL
}
```



