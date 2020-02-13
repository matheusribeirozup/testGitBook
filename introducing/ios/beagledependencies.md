---
description: Here we go to explain the BeagleDependencies properties and how to use them.
---

# BeagleDependencies

Your application can change Beagle default behaviour by customising properties of the `Beagle.dependencies` instance. Each of its properties have a specific role on what Beagle is capable of, and there are some dependencies that communicates with others. This is actually why you should threat `Beagle.dependencies` as the main point of customisation, so other parts can see your modification.

Most of the time, however, you should rely on the default implementations instead of overriding them.

```text
class BeagleDependencies: BeagleDependenciesProtocol {

    var baseURL: URL?
    var networkClient: NetworkClient
    var decoder: ComponentDecoding
    var appBundle: Bundle
    var theme: Theme
    var validatorProvider: ValidatorProvider?
    var deepLinkHandler: BeagleDeepLinkScreenManaging?
    var customActionHandler: CustomActionHandler?
    var flex: FlexViewConfiguratorProtocol
    var actionExecutor: ActionExecutor
    var network: Network
    var navigation: BeagleNavigation
    var preFetchHelper: BeaglePrefetchHelping
}

```

## baseURL

It\`s used to set a base url to your application so, when you start a [BeagleScreenViewController](beaglescreenviewcontroller.md) you can use just the path, not the absolute url.

## NetworkClient

It's responsible for actually executing _network requests_. Your application will probably have to customize this part because each project has a very specific demand for their _network layer_, therefore the default implementation we provide would be too simple for your needs.

## Decoder

It's responsible for transforming JSON into _Beagle Components_ \([Widgets](../../components/widget/), [Actions](../../components/action/)\). It already have the logic to decode all default components, and in order to make it work with your custom components you can just \`register\(\)\` them on this instance.

## AppBundle

Override if you application use diferent Bundle that is not Main.

## Theme

It's responsible for storing all your styles and knows how to apply them on components.

Some widgets have a variable that lets you define the `style` of it. The name received in this variable will then be passed to the `Theme`  dependency so it can try to use that style on that component.

To configure custom styles you need to the the folowing:

```swift
// 1
static func whiteLabelStyle() -> (UILabel?) -> Void {
    BeagleStyle.label(font: .systemFont(ofSize: 15), color: .white)
}

// 2
let theme = AppTheme(styles: [
    "myStyleName": whiteLabelStyle
])

// 3
Beagle.dependencies.theme = theme
```

1. Make a function responsible to apply the style to the widget. In this case we are making a UILabel with `systemFont` and white color
2. Create a conrete instance of AppTheme\(Precisa de link\) with the names of your styles and the functions that are responsable to apply de style
3. Assign it to the dependencies

## ValidatorProvider

## DeepLinkHandler

This handler is used in [deep link navigation](../../components/widget/navigation/) action, the variable already have a default value and you can add new screens to it, or you can completly override to your implemetation.

To add a screen as a possible route for deep linking this is how using the default implementation.

```swift
let deepLinkHandler = DeeplinkScreenManager.shared
deepLinkHandler["MyDeepLinkScreen"] = MyDeepLinkScreenClass.self
Beagle.dependenciesdeepLinkHandler = deepLinkHandler
```

## CustomActionHandler

The default value for `customActionHandler` is `nil`, you can set a handler to manipulate your custom actions as needed. One way to do it is the folowing.

{% hint style="warning" %}
Custom actions are executed in global context. Be carefull with your implementations.
{% endhint %}

```swift
// 1
let customActionHandler = CustomActionHandling()
// 2
customActionHandler["myCuscomActionName"] = { context, action in // 3
    // Make any logic here
}
// 4
Beagle.dependencies.customActionHandler = customActionHandler
```

1. We initialize a variable with a default implementation of [CustomActionHandling](customactionhandling.md)
2. Register a completion block who will be executed as your action, youu need to  register your action with a name so it can be found later
3. Your custom action will recive 2 parameters, one is the BeagleContext\(need link\) and the other the [CustomAction](../../components/action/customaction.md) that triggered you block
4. Finally just assign tha variable to the dependencies.

{% hint style="info" %}
This is a exemple using the built in classes, you can make your own handler by implementing [CustomActionHandler](customactionhandling.md) in a class you want to handle actions and use it a way fits better.
{% endhint %}

## flex

## actionExecutor

## network

The `network` is responsible for the 3 main operations in the framework which are:

`fetchComponent`: Orchestrate request to fetch widgets from the server

`submitForm`: Submit form widget

`fetchImage`: Fetch images for the [networkImage](../../components/widget/ui/networkimage.md)

## navigation

The `navigation` need to hadle the [navigate](../../components/action/navigate.md) actions from your app. We already have a implementation for this and is de default value but can also be overwritten by a class who conforms with he [BeagleNavigation](beaglenavigation.md).

## preFetchHelper

