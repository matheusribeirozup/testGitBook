---
description: This protocol have the function responsible for handle the navigate actions
---

# BeagleNavigation

## The protocol

```swift
public protocol BeagleNavigation {
    func navigate(action: Navigate, context: BeagleContext, animated: Bool)
}
```

## Default implementation

There is a implementation for with this protocol as a default value used in the [BeagleDependencies](beagledependencies.md), this implemetation treats the actions a way we consider more intuitive.

### openDeepLink

This action will do a push to a native ViewController based on the path received.

{% hint style="info" %}
ViewController is getted locally
{% endhint %}

### swapView

Will replace the entire pile of ViewControllers with a new one thats is passe.

{% hint style="info" %}
ViewController is getted remotely
{% endhint %}

### addView

Just add another ViewController to the pile with a push operation. This ViewController can be getted remotely or locally.

{% hint style="info" %}
ViewController is getted locally or remotely
{% endhint %}

### presentView

Present a new ViewController with the deafult system animation.

{% hint style="info" %}
ViewController is getted locally or remotely
{% endhint %}

### finishView

Dismiss all the ViewControllers pil.

### popView

Pop the last ViewController.

### popToView

Pop to a specific ViewController.

