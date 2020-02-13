---
description: Common examples showing how to use Beagle in a Android Application
---

# Android

### Creating a Widget

Steps into creating a customized widget:

1. **Create** a class to represent your customized widget, for example: `MyWidget`
2. **Annotate** this class with `@RegisterWidget` annotation
3. **Extend** this class from `WidgetView` Class
4. **Implement** the `toView` method.

```kotlin
@RegisterWidget
class MyWidget(
    val myAttribute: String
) : WidgetView {

    // This method is responsible to transform your Widget in a native View
    override fun toView(context: Context) = MyCustomView(context).apply {
        setMyAttribute(myAttribute)
    }
}
```



```kotlin
// how declare:
val declarative = LazyWidget(
    url = "http://www.fetchwidget.com/very-large-widget",
    initialState = Text("Loading...")
)
```

