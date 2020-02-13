# Screen



```kotlin
data class Screen(
    val safeArea: SafeArea? = null,
    val navigationBar: NavigationBar? = null,
    val header: ServerDrivenComponent? = null,
    val content: ServerDrivenComponent,
    val footer: ServerDrivenComponent? = null
)
```

### safeArea



### navigationBar



### header



### content



### footer



```kotlin
data class SafeArea(
    val top: Boolean? = null,
    val leading: Boolean? = null,
    val bottom: Boolean? = null,
    val trailing: Boolean? = null
)
```

### top



### leading



### bottom



### trailing



```kotlin
data class NavigationBar(
    val title: String,
    val showBackButton: Boolean? = null,
    val style: String? = null,
    val navigationBarItems: List<NavigationBarItem>? = null
)
```

### title



### showBackButton



### style



### navigationBarItems



```kotlin
data class NavigationBarItem(
    val text: String,
    val image: String? = null,
    val action: Action
)
```

### text



### image



### action



