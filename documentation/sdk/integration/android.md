# SDK Integration

## Changelog
> You can find a complete changelog [here](https://gitlab.com/geouniq/documentation/blob/master/sdk/integration/changelog_android.md)

## Table of Contents

1. [Project Configuration](#project-configuration)
    1. [Gradle](#gradle-configuration)
    2. [Manifest](#manifest-configuration)
    3. [ProGuard](#proguard-configuration)
    4. [Mobile Key](#providing-the-mobile-key)
2. [Basic Operations](#basic-operations)
    1. [Enabling/Disabling the SDK](#enablingdisabling-the-sdk)
    2. [Handling blocking issues](#handling-blocking-issues)
    3. [Handling User consent](#handling-user-consent)
    4. [Getting the device ID](#getting-the-device-id)

## Project Configuration

### Gradle Configuration

Open the file build.gradle file of the application module (not the main project) on Android Studio.
Add the following lines to import geouniq url repository

```gradle
android {
    //...
	repositories {
	    maven { url "https://mymavenrepo.com/repo/PzY5Lw6PNZ938XDfVtzf/" }
    }
}
```

Add the following dependency

```gradle
dependencies{
    implementation 'com.geouniq.android:sdk-library:x.y.z'
}
```
> Replace x.y.z with a specific version of library that you can find [here](https://mymavenrepo.com/repo/PzY5Lw6PNZ938XDfVtzf/com/geouniq/android/sdk-library/)

### Manifest Configuration
The library already declare the basic permissions that needs, if your app meets the Google Play Store policies for background location, make sure you've declared permission to access background location:
```xml
<uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
```

### ProGuard Configuration

The library already contains its ProGuard configuration file, which will be merged with your application's during the build process.

### Providing the Mobile Key

The Mobile Key generated for your app when you configured your project (see [here](/project-configuration.md)) must be provided as a string resource with name `"geouniq_mobile_key"`.

This can be done by putting the following line into the Gradle build script of your app (*build.gradle* file of your app module)

```gradle
defaultConfig {
    //...
    it.resValue("string", "geouniq_mobile_key", "YOUR_MOBILE_KEY")
}
```

It could be convenient to set a different value for the debug and the relase build types.

> Note that the certificates used for the two build types are generally different, and thus their SHA1 fingerprint will be different. 
For this reason, you should create two different Clietn Apps, one for the debug and one for the release build, each with its own fingerprint (see [Project Configuration](/project-configuration.md)).
A common solution is to create two different projects, one for test and one for production, and create an Android Client App on each project, using the debug fingerprint for the test project and the release fingerprint for the production project.


```gradle
buildTypes {
    release {
        //...
        it.resValue("string", "geouniq_mobile_key", "YOUR_PRODUCTION_MOBILE_KEY")
    }
    debug {
        //...
        it.resValue("string", "geouniq_mobile_key", "YOUR_TEST_MOBILE_KEY")
    }
}
```

## Basic operations

* [Enabling/Disabling the SDK](#enablingdisabling-the-sdk)
* [Handling blocking issues](#handling-blocking-issues)
* [Handling User consent](#handling-user-consent)
* [Getting the device ID](#getting-the-device-id)

### Enabling/Disabling the SDK

The SDK can be enabled and disabled at runtime.
To make GeoUniq SDK start, you need to enable it by calling the method `GeoUniq.enable()` at least once.

You might do that into the main activity of your app, as in the example below.

Once enabled, the SDK will not stop until you disable it by calling `GeoUniq.disable()`. That is, it will keep performing automatic operations, such as tracking the device position, even after a device reboot or an update of the app.
Disabling the SDK at runtime is useful if you want the SDK to stop completely. For example, you could remotely control a configuration parameter of your app to stop the SDK for all or some of your installations.

> If you simply don't want Geouniq to keep collecting location data for a specific User, you can do that without completely disabling the SDK (see [Handle User consent](#handle-user-consent)). This way you can still exploit the mobile-side functionalities that the SDK provides without having Geouniq collecting data for the specific user


```java
public class MainActivity extends Activity {

    private GeoUniq geoUniq;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        this.geoUniq = GeoUniq.getInstance(this);
        this.geoUniq.enable();
    }
}
```

### Handling blocking issues

For the SDK to be able to accomplish its main task, that is tracking the device position, the following requirements must be met:

* The foreground location permission must be granted to the app
* The background location permission must be granted to the app, if it meets the Google Play Store policies for background location
* The location functionality must be enabled on the device
* Google Play Services must be installed on the device (almost always met)

The SDK provides a simple way for checking all the requirements and optionally solve the related issues.
Solving an issue generally implies showing an alert to the User. Depending on the specific requirement, a different alert will be shown.

The example below shows hot to check for all requirements and solve them.
In the example, the check is performed on the `onStart()` method of the main activity

```java
public class MainActivity extends Activity {

    private GeoUniq geoUniq;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        this.geoUniq = GeoUniq.getInstance(this);
        this.geoUniq.enable();
    }

    @Override
    protected void onStart() {
        super.onStart();
        // This is to automatically handle location permission and other possible issues that would prevent GeoUniq to work correctly
        this.setErrorListener();
    }


    /**
     * Sets an Error listener to automatically handle those situations that would prevent the SDK to work properly
     */
    private void setErrorListener(){

        this.geoUniq.setErrorListener(new GeoUniq.IErrorListener() {
            @Override
            public void onError(GeoUniq.RequestResult requestResult) {
                if(requestResult.hasResolution()){
                    requestResult.startResolution(MainActivity.this);
                }
            }
        });
    }
}

```

### Handling User consent

The ability of the SDK to track the device location does not give Geouniq the permission to collect user data.
According to [GDPR](https://ec.europa.eu/commission/priorities/justice-and-fundamental-rights/data-protection/2018-reform-eu-data-protection-rules_en) regulation, you should request the User the consent to collect location data to Geouniq platform.
There are different consents that User can be grant, if at least one consent is granted, Geouniq have the permission to collect user data.

> NOTE: if your app is not under GDPR regulation, you can avoid request the consent to the user and directly inform the SDK that it has the permission to collect data on Geouniq platform. This can be done as explained below in [Setting consent explicitely](#setting-the-user-consent-explicitely)

The SDK provides a simple way to handle user consent through the `showPrivacyPolicyAndSet()` method of the `GeoUniq` class, as shown in the example below.
When this method is called, it will show a dialog to the User requesting the consent to collect data on GeoUniq platform. The privacy policy can also be seen by the User.
If the User accept the whole privacy policy or gives at least a consent, then the SDK will actually start sending data on GeoUniq platform. Otherwise, it will keep performing all the other automatic operations without sending any information on GeoUniq platform.

The `GeoUniq.IPrivacyPolicyListener` object is used to inform the caller about the user choices, that are wrapped in the `GeoUniq.IConsentsMap` object.
The type of the objects contained in the map is `GeoUniq.ConsentItem`, this is an enumerated that model a single consent.

The method `showPrivacyPolicySwitchesAndSet()`, show a dialog to the User requesting permission for each single consent.

> The example below show how to perform consents request. If all consents are not granted, privacy consent view is shown, else location permission request is performed.
In the first case, after User response, if there is at least a consent granted, location permission request is performed.

```java
public class MainActivity extends Activity {
    private static final int LOCATION_PERMISSION_REQUEST_CODE = 620;
    private GeoUniq geoUniq;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        this.initGeoUniq();
        this.requestConsentsIfNeeded();
    }

    @Override
    public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);

        if (requestCode == LOCATION_PERMISSION_REQUEST_CODE) {
            if (checkLocationPermission()) {
                //LOCATION PERMISSION GRANTED, ADD YOUR LOGIC HERE
            } else {
                //LOCATION PERMISSION NOT GRANTED
            }
        }
    }

    private void initGeoUniq() {
        this.geoUniq = GeoUniq.getInstance(this);
        this.geoUniq.enable();
    }

    private void requestConsentsIfNeeded() {
        if (!geoUniq.getPrivacyConsentsMap().containsValue(true)) {
            // ALL CONSENTS ARE NOT GRANTED, LET'S SHOW PRIVACY POLICY VIEW
            this.geoUniq.showPrivacyPolicyAndSet(this, new GeoUniq.IPrivacyPolicyListener() {
                @Override
                public void onResponse(GeoUniq.IConsentsMap statusMap) {
                    if (statusMap.containsValue(true)) {
                        // THERE IS AT LEAST A CONSENT GRANTED, LET'S REQUEST THE LOCATION PERMISSION
                        requestLocationPermission();
                    } else {
                        // ALL CONSENTS ARE NOT GRANTED
                    }
                }
            });
        } else {
            // THERE IS AT LEAST A CONSENT GRANTED, LET'S REQUEST THE LOCATION PERMISSION
            requestLocationPermission();
        }
    }

    private boolean checkLocationPermission() {
        return ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS_FINE_LOCATION) == PackageManager.PERMISSION_GRANTED;
    }

    private void requestLocationPermission() {
        ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, LOCATION_PERMISSION_REQUEST_CODE);
    }
}
```

#### Setting the user consent explicitely

The SDK also provides `setPrivacyConsent(ConsentItem consentItem, boolean isGranted)` method of the `GeoUniq` class to explicitely set a consent.
If there is at least a consent granted, Geouniq is allowed to collect user data.
This is particularly useful in the following cases.

If your app is not under GDPR regulation, then you can call this method with any one `ConsentItem` and the parameter `isGranted` equal to `true` to let the SDK collect data without requesting any consent to the User

If your app is under GDPR regulation but youn want to use your own dialog to request the consent to the User, then you have to explicitely inform GeoUniq SDK about the user choise.
This must be done in two different situations:

1. When the User takes a choise on your consent dialog: the user's choise must be comunicated to the SDK
2. Each time the app starts: you should check the current status of the consent and communicate it to GeoUniq SDK each time. Note that this is important if your app already used to request the consent to collect data to the User before to integrate GeoUniq SDK. In such a case, if the User had already given the consent and you no longer ask it to the User, GeoUniq SDK would never be informed that the User had consented data to be collected. 

Finally, you should provide the User a way to remove a consent from your app's settings.
If the User removes a consent, then you should inform the SDK by calling the method above with the releated `ConsentItem` element and parameter `isGranted` equal to `false`.
By doing so, if there isn't at least another consent granted, the SDK will stop sending data to GeoUniq platform immediately.

There are 2 types of consents, modeled by the GeoUniq.ConsentItem enumeration:
- GeoUniq.ConsentItem.ANALYSIS
- GeoUniq.ConsentItem.CUSTOMIZATION_AND_ADTARGETING

> This is an example that shown how to comunicate the current status of constents to GeoUniq SDK when app starts

```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
    
        boolean analysisConsent = readAnalysisConsentStatusFromStorage();
        GeoUniq.getInstance(this).setPrivacyConsent(GeoUniq.ConsentItem.ANALYSIS, analysisConsent);    
        
        boolean adTargetingConsent = readAdTargetingConsentStatusFromStorage();
        GeoUniq.getInstance(this).setPrivacyConsent(GeoUniq.ConsentItem.CUSTOMIZATION_AND_ADTARGETING, adTargetingConsent);
    }
    
    private boolean readAdTargetingConsentStatusFromStorage() {
        // RETURN THE ADTARGETING CONSENT READ FROM STORAGE 
    }

    private boolean readAnalysisConsentStatusFromStorage() {
        // RETURN THE ANALYSIS CONSENT READ FROM STORAGE 
    }
}
```

> The following code shows an example of a custom request flow for analysis consent

```java
public class MainActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        showAnalysisConsentsRequestDialog(this, new IAnalysisConsentsListener() {
            @Override
            public void onUserResponse(boolean isGranted) {
                // COMMUNICATE THE USER'S RESPONSE TO THE GEOUNIQ SDK
                GeoUniq.getInstance(MainActivity.this).setPrivacyConsent(GeoUniq.ConsentItem.ANALYSIS, isGranted);
            }
        });
    }

    private void showAnalysisConsentsRequestDialog(Context context, IAnalysisConsentsListener analysisConsentsListener) {
        // SHOW HERE YOUR CUSTOM DIALOG THAT ASK THE USER FOR ANALYSIS CONSENT

        // COMMUNICATE THE USER'S RESPONSE TO THE LISTENER
        analysisConsentsListener.onUserResponse(userResponse);
    }

    interface IAnalysisConsentsListener {
        public void onUserResponse(boolean isGranted);
    }
}
```

#### Getting the consent status

The method `IConsentsMap getPrivacyConsentsMap()` of `GeoUniq` class allows to know the status of the User consents.
This is the result of the User choise after showing it the privacy policy dialog, or the value explicitely set through the `setPrivacyConsent(ConsentItem consentItem, boolean isGranted)` method.
To check a single consent, there is the method `boolean getPrivacyConsent(ConsentItem)` that return `true`if the consent is granted, `false` otherwise

#### Configurations

There are two configurations for Privacy popup, Default and Media, you can also customize it as you prefer. 
[Here](https://gitlab.com/geouniq/documentation/blob/master/sdk/integration/privacy_popup_customization_android.md) you can find a guide.

## Getting the Device ID

As soon as the SDK starts for the first time, a [Device ID](/service-architecture.md#device-registration-device-ids-and-device-base) is assigned to that specific installation of your app.

> The Device ID assigned to an installation might change in case of rare events, for example if the local storage of the device gets erased.

The SDK provides two different ways to obtain the Device ID.

### Getting the Device ID through a Device ID listener

The first method to obtain the Device ID is to set a `IDeviceIdListener`, as shown in the example below.
When a listener is set, the SDK immediately returns the Device ID through the `onDeviceIdAvailable()` callback if the Device ID is already available.
Otherwise, it will call the callback method as soon as the ID is obtained.

> The best practice for an app that want to collect on a backend systems the Device ID assigned to each installation, is to set a `IDeviceIdListener` each time it starts.
The mobile app would receive the Device ID each time and should always send it to the backend system.
Then, the backend system should overwrite any previously stored value if the new received value is different.

```java
public class MainActivity extends Activity {

    private GeoUniq geoUniq;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        this.geoUniq = GeoUniq.getInstance(this);
        this.setDeviceIdListener();
    }

    /**
     * Sets a listener to received the ID assigned to this device
     */
    private void setDeviceIdListener(){

        this.geoUniq.setDeviceIdListener(new GeoUniq.IDeviceIdListener() {

            @Override
            public void onDeviceIdAvailable(String deviceId) {
                Log.d("GeoUniq", "Device ID received: "+deviceId);
            }
        });
    }
}
```

### Getting the Device ID by calling an explicit class method

The second way is to call the `GeoUniq.getDeviceId()` method.
This method returns the value of the Device ID if it has already been obtained or `null` if the Device ID has not been obtained yet.
