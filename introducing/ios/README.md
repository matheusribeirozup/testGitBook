---
description: Getting started with Beagle for iOS
---

# Beagle iOS

## Setting up the dependency

### Requirements

* iOS 10.0+
* Xcode 10.1+
* Swift 4.2+

## Installation

### CocoaPods

[CocoaPods](https://cocoapods.org/) is a dependency manager for Cocoa projects. For usage and installation instructions, visit their website. To integrate Beagle into your Xcode project using CocoaPods, specify it in your `Podfile`:

```text
pod 'BeagleUI'
```

### Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks. To integrate Beagle into your Xcode project using Carthage, specify it in your `Cartfile`:

```text
github "ZupIT/darwin-beagle-ios"
```

## Initialization

In you **AppDelegate** put this code

```swift
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ...
    Beagle.dependencies = BeagleDependencies(appName: "myAppName")
    ...
    }
}
```

