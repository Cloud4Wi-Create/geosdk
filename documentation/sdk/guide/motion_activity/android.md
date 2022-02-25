# Using Motion Activity on Android

## Get the current motion activity

The following example shows how to get a [`MotionActivity`](#related-reference-doc) object representing the current motion activity.

```java
import android.app.Activity;
import com.geouniq.android.GeoUniq;
import com.geouniq.android.GeoUniq.MotionActivity;
import com.geouniq.android.GeoUniq.GeoPoint;

import java.util.Date;

/**
 * Created by angelocoiro on 25/06/18.
 */

public class MyActivity extends Activity {

    private void myMethod() {
        MotionActivity motionActivity = GeoUniq.getInstance(this).getCurrentMotionActivity();

        //Implements logic according to the current motion type, start time, or start position
        MotionActivity.Type type = motionActivity.type();
        Date startTime = motionActivity.startTime();
        GeoPoint point = motionActivity.startPosition();
        // your logic here
    }
}
```

## Register for motion activity changes

### Implement the "callback class"

The callback class:

* Has to implement the interface [`IMotionActivityListener`](#related-reference-doc)
* Must be public
* Cannot be an inner class
* Cannot be an anonymous class
* Must have the default constructor 

The `Context` object provided as input parameter in the [`IMotionActivityListener.onActivityChanged()`](#releted-reference-doc) callback method can be used to start a `Service`, send a notification, or use any other Android functionality that requires a `Context` object.

```java
import android.content.Context;

import com.geouniq.android.GeoUniq.GeoPoint;
import com.geouniq.android.GeoUniq.IMotionActivityListener;
import com.geouniq.android.GeoUniq.MotionActivity;

import java.util.Date;

public class MotionActivityListener implements IMotionActivityListener {

    public void onActivityChanged(Context context, MotionActivity started, MotionActivity finished) {
        // Your own logic here; for example:
        // get the type of the new motion acitivty
        MotionActivity.Type startedType = started.type();
        // get the start time
        Date startedAt = started.startTime();
        // get the start position
        GeoPoint p = started.startPosition();
        // Do something
    }
}
```

### Register the "callback class"

The example below shows how to register a Class to receive a callback when the motion activity changes.
It is possible to register any set of [`MotionActivity.Type`](#related-reference-doc), or all the possible values of the [`MotionActivity.Type`](#related-reference-doc) enumeration.
Registering the same Class more times with the same set of activities has no effect; so it is safe to call the registration method more time even if the same Class has already been registered.
For an exaustive explanation, see the [reference documentation](#related-reference-doc).

```java
import com.geouniq.android.GeoUniq

public class MyMainActivity extends Activity {
    
    // Example: register your callback class in the onCreate method of your main activity
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        this.registerMotionActivityListener();
    }

    private void registerMotionActivityListener() {

        // register for a specific set of motion type
        MotionActivity.Type[] types = new MotionActivity.Type[]{MotionActivity.Type.WALKING, MotionActivity.Type.AUTOMOTIVE};
        // or, for all types
        types = MotionActivity.Type.values();

        GeoUniq.getInstance(this).registerMotionActivityListener(MotionActivityListener.class, types);
    }
}
```

## Disable Motion Activity
Motion Activity engine can be disabled adding in AndroidManifest.xml this meta data:
```xml
    <application>
    //...
        <meta-data
            android:name="com.geouniq.disable_motion_activity"
            android:value="true" />
    </application>
```