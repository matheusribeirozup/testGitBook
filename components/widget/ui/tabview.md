# TabView



```kotlin
data class TabView(
    val tabItems: List<TabItem>
) : ServerDrivenComponent
```

### tabItems



```kotlin
data class TabItem(
    val title: String? = null,
    val content: ServerDrivenComponent,
    val icon: String? = null
)
```

### title



### content



### icon



