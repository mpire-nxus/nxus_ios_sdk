## Summary
TechMpire nxus platform SDK for iOS developers

## Get iOS SDK
Download the SDK from <a href="http://distribution.nxus.mobi/libs/ios-mpire-nxus-measurement-v1_1_0.zip">here</a>. We also have Cocoapods supported for library distribution so please check repository provided <a href="https://github.com/mpire-nxus/nxus_ios_cocoapod">here</a>

## Embedding the SDK
To use the SDK, you have to drag the static library files to your project. Just open the project and drag the include folder and libMpireNxusMeasurement.a file into Xcode window, under your project name.

<img src="http://distribution.nxus.mobi/images/ios/image_1.png">

## Adding linker flag
The final step is to add the -ObjC linker flag. The linker tries to be efficient about only including needed code, which can sometimes exclude static library code. With this flag, all the Objective-C classes and categories in the library are loaded properly.

Click on the <b>Build Settings</b> tab and locate <b>Other Linker Flags</b>. In the popover, add the <b>-ObjC</b> flag.

<img src="http://distribution.nxus.mobi/images/ios/image_3.png">

## SDK initialisation
After you completed the previous step, you are ready to initialise the library and start sending events.
Open <b>AppDelegate.m</b> class and import the library header file:
```
#import "include/MpireNxusMeasurement/MpireNxusMeasurement.h"
```

Then, initialise it within AppDelegate's <b>didFinishLaunchingWithOptions</b> method:
```
[MpireNxusMeasurement initializeLibrary:@"YOUR_API_KEY"];
```

## Sending custom events
You can send custom events by calling the method <b>trackEvent</b>:
```
[MpireNxusMeasurement trackEvent:@"event-name"];
```

If you have any additional parameters you would like to send, pass in an instance of <b>NSMutableDictionary</b>:
```
NSMutableDictionary *params = [[NSMutableDictionary alloc] init];
[params setValue:@"value" forKey:@"key"];
[MpireNxusMeasurement trackEvent:event params:params];
```

## Sending predefined events
You can send predefined events using the SDK, with following methods:
```
[MpireNxusMeasurement trackEventInstall:params];
[MpireNxusMeasurement trackEventOpen:params];
[MpireNxusMeasurement trackEventRegistration:params];
[MpireNxusMeasurement trackEventPurchase:params];
[MpireNxusMeasurement trackEventLevel:params];
[MpireNxusMeasurement trackEventTutorial:params];
[MpireNxusMeasurement trackEventAddToCart:params];
[MpireNxusMeasurement trackEventCheckout:params];
[MpireNxusMeasurement trackEventInvite:params];
[MpireNxusMeasurement trackEventAchievement:params];
```
Every method takes additional parameters using <b>NSMutableDictionary</b>:
```
NSMutableDictionary *params = [[NSMutableDictionary alloc] init];
[params setValue:@"value" forKey:@"key"];
```

## Logging
To enable logging, call the method debuggingEnabled before library initialisation:
```
[MpireNxusMeasurement debuggingEnabled:YES];
```