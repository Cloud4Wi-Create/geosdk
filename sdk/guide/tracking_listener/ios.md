# Using Tracking Listener on iOS

### Implement the "callback class"

The callback class:

* Has to implement the interface `GUTrackingListener`
* Must have the required init 

Swift
```swift
import GeoUniq

class TrackingListener: GUTrackingListener {
	
	required init() {
	}
	
	func onNewLocationUpdate(_ location: GULocation) {
		// your code here
	}
}

```
Objective-C
```objc
#import "GeoUniq/GeoUniq-Swift.h"

@interface TrackingListener: NSObject <GUTrackingListener> {
	
}
@end

@implementation TrackingListener

- (id)init {
	self = [super init];
	return  self;
    }

- (void)onNewLocationUpdate:(GULocation * _Nonnull)location {
	// your code here
    }

@end

```

### Set the "callback class"

Swift 
```swift
import GeoUniq

class AppDelegate: UIResponder, UIApplicationDelegate {
    var window: UIWindow?
    
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
    
    GeoUniq.sharedInstance().enable()
    
    ...
    
	GeoUniq.sharedInstance().setTrackingListener(listener: TrackingListener.self)
    
    ...
}
```
Objective-C
```objc
#import "AppDelegate.h"
#import "GeoUniq/GeoUniq-Swift.h"
#import "TrackerListener.h"

@interface AppDelegate ()

@end

@implementation AppDelegate


- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

	[[GeoUniq sharedInstance] enable];
	
	...
	
	[[GeoUniq sharedInstance] setTrackingListenerWithListener: [TrackingListener self]];
	
	...
	
	return YES;
}
```

