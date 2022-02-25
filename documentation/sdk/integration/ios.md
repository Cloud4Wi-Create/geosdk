> last update: 23-Jan-2020

# SDK Integration
 

## Table of Contents

1. [Reference versions](#reference-versions)
    1. [Xcode](#xcode)
    2. [Swift](#swift)
    3. [GeoUniq](#geouniq)
2. [Installation](#installation)
    1. [CocoaPods](#cocoapods)
    2. [Swift Package Manager](#swift-package-manager)
    3. [Manual](#manual)
3. [Project settings](#project-settings)
    1. [Mobile key](#mobile-key)
    2. [Location usage keys](#location-usage-keys)
    3. [Universal framework](#universal-framework)
    4. [Background fetch](#background-fetch)
    5. [App Tracking Transparency](#app-tracking-transparency)
4. [Basic operations](#basic-operations)
    1. [Initialization](#initialization)
    2. [Enable/Disable SDK](#enabledisable-the-sdk)
    3. [Handle user consent](#handle-user-consent)
    4. [Get Device Id](#get-device-id)

## Reference Versions

### Xcode

12.3

### Swift

5.2 with "Build Libraries for Distribution" enabled (in case of updating the swift version of the app it isn't necessary to update the framework). 
Framework with swift 4 version has been deprecated.

### GeoUniq

1.6.5 - [Changelog](/sdk/integration/changeLogIos.md)


## Installation

### CocoaPods

Add `pod 'GeoUniq-Swift5'` to your Podfile and run `pod install`. More details [CocoaPods here](https://cocoapods.org/).

### Swift Package Manager

Repository: https://github.com/geouniq/GeoUniq-Swift-Package.git

### Manual

1. Download the SDK from the [Console](https://console.geouniq.com) (drop down menu on the top-right corner)
2. Drag and Drop the file GeoUniq.xcframework into your xcode project in the Project Navigator (remember to check *"Copy items if needed"*).
3. Select Your-Project-Name general file in the Project Navigator:
    - Select Your-Target-Name
    - General tab -> Embedded Binaries section: add GeoUniq.xcframework (set 'Embed & Sign')


## Project settings

### Mobile key

Add the following key to Info.plist file (String value) with the corresponding value (that you obtained when added your app to your project)
```
GUMobileKey: 'your-mobile-key'
```


### Location usage keys

1. Add the following keys to Info.plist file (String value), the corresponding values will be shown to the user by iOS
```
NSLocationAlwaysAndWhenInUseUsageDescription: "We would like to access your locations"
NSLocationWhenInUseUsageDescription: "We would like to access your locations"
```


2. If your app supports iOS 10 add
```
NSLocationAlwaysUsageDescription: "We would like to access your locations"
```


3. Add the following key to Info.plist file (String value), it will be used to show a popup to the user before the provided by iOS. Only if the user accepted this first popup we request the permission to iOS.
```
GULocationPermissionNotDetermined: "We would like to ask your permission to access your locations"
```

### Universal framework

<b>From version 1.6.1 with the transion to XCFramework this step is not necessary!</b>

<s>In order to give you the best development experience we provide an 'Universal Framework': a framework which works both on simulator and real device.

<s>What you have to do is just add one line of code as described below:
1. <s>Select Your-Target-Name
2. <s>Build Phases tab -> add new Run Script phase after Embed Frameworks phase
3. <s>Paste `./GeoUniq.framework/run` in the script text box (Cocoapods insallation paste:  `${PODS_ROOT}/GeoUniq.framework/run`) </s>

### Background fetch

In order to obtain a greater number of positions we suggest to enable this feature. To do this carry out these two steps:

1. Select your project -> Select your target -> Select 'Signing & Capabilities' tab -> tap on '+ Capability' -> select 'Background Modes' -> check 'Background fetch'
2. In AppDelegate add this code:


```swift
//Swift
/* ------ AppDelegate.swift ------ */

func application(application: UIApplication, performFetchWithCompletionHandler completionHandler: (UIBackgroundFetchResult) -> Void){
    //call GeoUniq backgroundFetch() method
    GeoUniq.sharedInstance().backgroundFetch()
}
```

```objc
//Objective C
/* ------ AppDelegate.m ------ */

- (void) application:(UIApplication *)application performFetchWithCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler{
    //call GeoUniq backgroundFetch() method
    [[GeoUniq sharedInstance] backgroundFetch];
    completionHandler(UIBackgroundFetchResultNewData);
}

```
### App Tracking Transparency
iOS 14 introduced the permission request to get the device's IDFA. In this regard, we have introduced two methods in our framework.

The first one checking the permission status:

```swift
...
let permissionStatus = GeoUniq.sharedInstance().getATTrackingAuthorizationStatus()
...
```
And the second one that makes the request and returns the user's choice:
```swift
...
GeoUniq.sharedInstance().requestATTrackingAuthorization { (status) in
    // Use status if you want
}
...
```

It is possible to use these methods but also the methods provided directly by iOS. There is no need to communicate to our framework the outcome of the permission.
Invoke the request method as soon as possible. For example right after the enable.

```swift
...
GeoUniq.sharedInstance().enable()
GeoUniq.sharedInstance().requestATTrackingAuthorization { (status) in
    // Use status if you want
}
...
```

<b>Important: Before invoking the method for the request (both Geouniq and iOS) it is necessary to insert the key in the plist</b>
```
NSUserTrackingUsageDescription: "The identifier will be used to personalise ads across apps and websites and to conduct marketing and research analysis"
```


## Basic operations

### Initialization
To initialize the framework and allow it to collect data in the background it is necessary to add this call in the didFinishLaunchingWithOptions method (this method don't start the tracking engine)

```swift
//Swift
/* ------ AppDelegate.swift ------ */

//importing the framework
import GeoUniq

func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {

    let _ = GeoUniq.sharedInstance()

    return true
}
```

```objc
//Objective C
/* ------ AppDelegate.m ------ */

//importing the framework
#import "GeoUniq/GeoUniq-Swift.h"

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [GeoUniq sharedInstance];

    return YES;
}
```

### Enable/Disable the SDK
To start the tracking engine call enable method. You can do that into the didFinishLaunchingWithOptions method. It is possible to enable directly the tracking engine when the initialize method is called. Once enabled, the SDK will not stop until you disable it by calling GeoUniq.sharedInstance().disable()
If the application does not have the permissions or has not yet requested them, the enable method will request them. 


```swift
//Swift
/* ------ AppDelegate.swift ------ */

//importing the framework
import GeoUniq

func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {

    GeoUniq.sharedInstance().enable()

    return true
}
```

```objc
//Objective C
/* ------ AppDelegate.m ------ */

//importing the framework
#import "GeoUniq/GeoUniq-Swift.h"

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [[GeoUniq sharedInstance] enable];

    return YES;
}
```

### Handle User consent

The ability of the SDK to track the device location does not give Geouniq the permission to collect user data.
According to [GDPR](https://ec.europa.eu/commission/priorities/justice-and-fundamental-rights/data-protection/2018-reform-eu-data-protection-rules_en) regulation, you should request the User the consent to collect location data on Geouniq platform.
There are different consents that User can be grant, if at least one consent is granted, Geouniq have the permission to collect user data.

> NOTE: if your app is not under GDPR regulation, you can avoid request the consent to the user and directly inform the SDK that it has the permission to collect data on Geouniq platform. This can be done as explained below in [Setting consent explicitely](#setting-the-user-consent-explicitely)

The SDK provides a simple way to handle user consent through the `GeoUniq.sharedInstance().showPrivacyPolicyAndSet(completion: ConsentsMap)` (**_Important_ In the AppDelegate don't invoke this method in the didFinishLaunchingWithOptions but call in applicationDidBecomeActive**), as shown in the example below.
When this method is called, it will show a dialog to the user requesting the consent to collect data on GeoUniq platform. The privacy policy can also be seen by the User.
If the User accept the whole privacy policy or gives at least a consent, then the SDK will actually start sending data to the GeoUniq platform. Otherwise, it will keep performing all the other automatic operations without sending any information to the GeoUniq platform.

The closure object is used to inform the caller about the user choices.

The type of the objects contained in the object is `GeoUniq.ConsentItem`, this is an enumerated that model a single consent


```swift
//Swift

//importing the framework
import GeoUniq

...

GeoUniq.sharedInstance().showPrivacyPolicyAndSet(completion: {(consentMap) in
	// Your logic here.
    // You might exploit this callback to keep trace of the last time the alert has been shown to the user in order to avoid showing it too often			
})

...
```

```objc
//Objective C

//importing the framework
#import "GeoUniq/GeoUniq-Swift.h"
 
...

[[GeoUniq sharedInstance] showPrivacyPolicyAndSetWithCompletion:^(ConsentsMap *map) {
	// Your logic here.
    // You might exploit this callback to keep trace of the last time the alert has been shown to the user in order to avoid showing it too often
}];

...

```

**Example in AppDelegate**

```swift
//Swift
/* ------ AppDelegate.swift ------ */

//importing the framework
import GeoUniq

func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {

    let _ = GeoUniq.sharedInstance()

    return true
}

...
...

func applicationDidBecomeActive(_ application: UIApplication) {
    if !GeoUniq.sharedInstance().getPrivacyConsentsMap().containsValue(value: true) {
    		GeoUniq.sharedInstance().showPrivacyPolicyAndSet { (map) in
    			if map.containsValue(value: true) {
    				GeoUniq.sharedInstance().enable()
    			}
    		}
    }
}


```

#### Setting the user consent explicitely

The SDK also provides `GeoUniq.sharedInstance().setPrivacyConsent(consent: ConsentItem, value: Bool)` to explicitely set a consent.
If there is at least a consent granted, Geouniq is allowed to collect user data.
This is particularly useful in the following cases.

If your app is not under GDPR regulation, then you can call this method with any one `ConsentItem` and the parameter `value` equal to `true` to let the SDK collect data without requesting any consent to the User

If your app is under GDPR regulation but youn want to use your own dialog to request the consent to the User, then you have to explicitely inform GeoUniq SDK about the user choise.
This must be done in two different situations:

1. When the User takes a choise on your consent dialog: the user's choise must be comunicated to the SDK
2. Each time the app starts: you should check the current status of the consent and communicate it to GeoUniq SDK each time. Note that this is important if your app already used to request the consent to collect data to the User before to integrate GeoUniq SDK. In such a case, if the User had already given the consent and you no longer ask it to the User, GeoUniq SDK would never be informed that the User had consented data to be collected. 

Finally, you should provide the User a way to remove a consent from your app's settings.
If the User removes a consent, then you should inform the SDK by calling the method above with the releated `ConsentItem` element and parameter `value` equal to `false`.
By doing so, if there isn't at least another consent granted, the SDK will stop sending data to GeoUniq platform immediately.

There are 2 types of consents, modeled by the ConsentItem enumeration:
- ConsentItem.analisys
- ConsentItem.customization

Example on the two current consents
```swift
//Swift

//importing the framework
import GeoUniq
...

GeoUniq.sharedInstance().setPrivacyConsent(.analisys, value: true)
GeoUniq.sharedInstance().setPrivacyConsent(.customization, value: true)


```

#### Getting the consent status

The method `GeoUniq.sharedInstance().getPrivacyConsentsMap()` allows to know status of the User consents.
This is the result of the User choise after showing it the privacy policy dialog, or the value explicitely set through the `GeoUniq.sharedInstance().setPrivacyConsent(consent: ConsentItem, value: Bool)` method.


### Get Device Id

The method `GeoUniq.sharedInstance().getDeviceId()` return the id relative to the device if it has been registered, nil otherwise.


