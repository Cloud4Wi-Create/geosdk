# Using Motion Activity on iOS

## Limitations

On iOS the functionality will not work if the SDK is not able to track the device position.
This means that, for the functinality to work, it is necessary that:

1. The "Always" Location permission is granted to the app
2. The Location functionality is active for the device


## Enable the use motion activity sensors

The use of the native iOS motion activity feature, which is based on HW sensors, requires to ask the related permission to the User.
Until the permission is not granted, GeoUniq SDK will infer the motion activity exclusively on the basis of the information coming from the tracking, thus with a lower accuracy.
The request of the permission will display a dialog to the User which can then decide to allow or deny the use of the functionality to the app. 

> Starting from iOS 10, it is necessary to add the following key to the info.plist file in order to be able to use motion activity information comnig from sensors.
```
Key: NSMotionUsageDescription | Type: String | Value: "your message explaining why you want to use motion activity"
```

To request permission call the method

```swift 
GeoUniq.sharedInstance().requestMotionActivityPermission()

```

From iOS 11.0 is possible to check the status of permission 
```swift 
GeoUniq.sharedInstance().getMotionActivityPermission()

```

## Get the current motion activity
The following example shows how to get a `GUMotionActivity` object representing the current motion activity.

```swift 
import Geouniq

public class MyClass: NSObject {

    ...

    func myfunc() {
	    	if let activity = GeoUniq.sharedInstance().getCurrentActivity() {
		    	let motionType = activity.type
		    	let startTime = activity.startTime
		    	let endTime = activity.endTime // is optional
	    	}
    	}
}
```

## Register for motion activity changes

### Implement the "callback class"

The callback class:

* Has to implement the interface `GUActivityDelegate`
* Must have the required init 

```swift
import GeoUniq

class motionActivityListener: GUActivityDelegate {
	
	required init() {
	}
	
	func onActivityChanged(started: GUMotionActivity, finished: GUMotionActivity) {
		// your code here
	}
}


```

### Register the "callback class"

The example below shows how to register a Class to receive a callback when the motion activity changes.
It is possible to register any set of `GUMotionType`, or all the possible values of the `GUMotionType` enumeration.
Registering the same Class more times with the same set of activities has no effect; so it is safe to call the registration method more time even if the same Class has already been registered.
You can register the listener in any class, here is an example in the appDelegate:

```swift

import GeoUniq

class AppDelegate: UIResponder, UIApplicationDelegate {
    var window: UIWindow?
    
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
    ...
    
    // For register class to all activity changes
    GeoUniq.sharedInstance().registerAllActivityChange(motionActivityListener.self)
    
    // For register class specific activity changes
    GeoUniq.sharedInstance().registerActivityChange(motionActivityListener.self, motionType: .automotive)
    
    ...
}
```