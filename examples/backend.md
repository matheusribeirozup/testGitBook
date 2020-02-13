---
description: Common examples showing how to use Beagle in a BFF
---

# Backend

## Creating a custom component

Extend the appropriate component base class from the framework. If it is a widget, add the provided `@RegisterWidget` annotation so it will be properly serialized.

{% tabs %}
{% tab title="Widget" %}
```kotlin
@RegisterWidget
class MyWidget: Widget
```
{% endtab %}

{% tab title="Screen" %}
```kotlin
class MyScreen: Screen
```
{% endtab %}

{% tab title="Action" %}
```kotlin
class MyAction: Action
```
{% endtab %}
{% endtabs %}

