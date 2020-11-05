# Motion Activity

GeoUniq SDK provides the possibility to detect the motion activity of a User and to be notified when it changes.
The motion activity represents the way the User is moving, e.g., whether he is still or walking, running, moving in a vehicle, etc.

In details, the provided motion types are the following

* STILL
* WALKING
* RUNNING
* CYCLING
* AUTOMOTIVE
* UNKNOWN

## Main features

Two main functinalities are provided by the SDK.

1. The possibility to request the current motion activity
2. The possibility to get informed (through a callback) when one or more specific motion activities start or end

The main features are the following

* **High Stability**: Motion activity changes are triggered only when there is sufficient confidence that a new motion activity is started, avoiding continuous changes between two or more activities
* **Increased precision**: The SDK combines information coming from sensor and geolocation to minimize the probability of incorrect detections
* **Always-on**: The functionality works even after the app is closed or after the reboot of the device. Once the app has "registered" to receive motion activity updates for one or more specific motion types, such registrations remains valid until they are explicitely removed; callbacks will be received even after the app is closed or after the the device is restarted. 
* **Easy of use**: There is no need to implement any paritular component in the app (e.g. Services or broadcast receivers on Android). A simple class implementing a specific interface is all you need to receive callbacks.

> On iOS the functionality stops working if the SDK is no longer able to track the device (see [iOS limitations](/sdk/guide/motion_activity/ios.md#configuring-the-info.plist))

## Usage

Motion activity detection is enabled by default both for Android and iOS SDKs

> On iOS, some configuration is necessary to be able to use motion activity information coming from hardware sensors (see [here](/sdk/guide/motion_activity/ios.md#limitations))

The information is provided through an Object providing the following information

* **Motion Type**: the type of motion, as defined [above](#motion-activity)
* **Start Time**: The time instant when the specific activity started
* **Start Position**: The geographical position where the specific activity started
* **End Time**: The time instant when the specific activity ended
* **End Position**: The geographical position where the specific activity ended

Obtaining the current motion activity is straightforward. It just needs to call a specific method which will return an object as described above.
To get informed about motion activity changes, the following steps have to be performed

1. **Implement a "callback class"**: the class has to implement a specific interface, with a method *onActivityChanged()* to receive callbacks. The method *onActivityChanged()* will contain your own logic.
2. **Register the "callback class"**: call the *registerMotionActivity()* method passing the *callback class* (the class type, not an instance of that class) and one or more motion types.
3. **Receive callbacks**: when a motion activity change is detected (and it involves at least one of the motion activities for which a *callback class* has been registered), an instance of the *callback class* is automatically instantiated by the SDK and the callback method *onActivityChanged()* is called.

See usage examples for [Android](/sdk/guide/motion_activity/android.md) and [iOS](/sdk/guide/motion_activity/ios.md)