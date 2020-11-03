# Using Tracking Listener on Android

### Implement the "callback class"

The callback class:

* Has to implement the interface `ITrackingListener`
* Class modifier must be public and have an empty default constructor

```java
   public class TrackingListener implements GeoUniq.ITrackingListener {
        public TrackingListener() {
        }

        @Override
        public void onNewPositionUpdate(Context context, GeoUniq.Location location) {
            // Your logic here. Use the provided locatoin at will
            // The Context allows you to perform operations such as accessing the storage, posting notifications, obtain Android services, etc.
        }
    }
```

### Set the "callback class"

Add the following code after call Geouniq `enable()` method:

```java
    GeoUniq.getInstance(context).registerTrackingListener(TrackingListener.class);
```