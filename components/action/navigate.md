# Navigate

The `Navigate` class handles **transition actions between screens** in the application. This is your structure:

```kotlin
data class Navigate(
    val type: NavigationType,
    val shouldPrefetch: Boolean? = false,
    val path: String? = null,
    val data: Map<String, String>? = null,
    val screen: Screen? = null
) : Action
```

### type

{% hint style="info" %}
This is a mandatory attribute and to work correctly the `path` attribute must be set, except for the `POP_VIEW` and `FINISH_VIEW`.
{% endhint %}

These component deals with 7 type of actions, that are represented by a `Enum` class:

```kotlin
enum class NavigationType {
    OPEN_DEEP_LINK,
    ADD_VIEW,
    SWAP_VIEW,
    FINISH_VIEW,
    POP_VIEW,
    POP_TO_VIEW,
    PRESENT_VIEW
}
```

* `ADD_VIEW`

When declared with this type, the action that will be performed is the **opening of a new screen** with the link passed in the `path` attribute. This screen will also be **stacked at the top** of the hierarchy of views in the application flow.

* `FINISH_VIEW`

This action closes the current screen.

* `OPEN_DEEP_LINK`

This action uses the informed `path` to execute the action declared in the deeplink that was **defined for the application**.

{% hint style="warning" %}
It is worth mentioning that if a deeplink handler is not informed, there will be no action. To register a handler, a class must be created that implements `DeepLinkHandler` and is tagged with `@BeagleComponent.`
{% endhint %}

* `PRESENT_VIEW`

Present a new screen with the link declared in the `path` attribute. This attribute basically has the same functionality as `ADD_VIEW`, however **starting a new flow**.

* `POP_TO_VIEW`

It is responsible for returning the stack of screens in the application flow **to a specific screen**.

* `POP_VIEW`

Attribute that adds the action of returning to the stack of added screens, **whether a dialog or not**.

* `SWAP_VIEW`

This attribute, when selected, opens a screen with the `path` informed from a new flow and **clears the stack of previously loaded screens**.

### shouldPrefetch

Boolean attribute that tells Beagle if the navigation request should be **previously loaded** or not.

### path

Attribute that contains the navigation request **endpoint**.

### data

Map attribute used when navigation is `OPEN_DEEP_LINK` to pass the necessary information in `String` format.

### screen

This attribute has **two distinct functions** according to the `path`:

1. If the `Navigate` object is built **without** a `path`, the **screen will be rendered** instead of making the service call.
2. If the path response **fails**, the screen acts as a **fallback**.





