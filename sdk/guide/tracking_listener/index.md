# Tracking Listener

The Tracking Listener functinoality allows a mobile app to receive all the location updates detected by the SDK and use them at will (e.g., send them to a remote server or process them according to a custom logic).

## Usage

To use the functionality, the following steps have to be performed:

1. **Implement a "callback class"**: the class has to implement a specific interface, with a method *onNewLocationUpdate(location Location)* to receive location updates through callbacks. The method *onNewLocationUpdate(location Location)* will contain your own logic.
2. **Register the "callback class"**: call the *setTrackingListener(class Class)* method passing the *callback class* (the class type, not an instance of that class).
3. **Receive callbacks**: when a position is detected by the SDK, an instance of the *callback class* is automatically instantiated  and the callback method *onNewLocationUpdate(location Location)* is called.

> NOTE: Once a "callback class" has been registered, it will receive location upodates until it is de-registered. You do not need to register the "callback class" when the app restarts or the system reboots.
However, registering the same "callback class" more times has no effect, so you can simple call the registration method everytime your app is started.

> NOTE: Different calls of the callback method are not assured to be performed on the same instance of the "callback class" and in general a new instance of the same class might be created each time.
Therefore, your logic should not depend on internal variables of the "callback class".

> NOTE: On Android, you do not need to implemnt and keep active any background service to receive location updates. The "callback class" is all you need.

The detailed documentation for Android and iOS can be found here:
* [Android](/sdk/guide/tracking_listener/android.md)
* [iOS](/sdk/guide/tracking_listener/ios.md)
