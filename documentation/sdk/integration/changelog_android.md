# 2.9.1 Release notes (19-01-2022)
### Enhancements
* Added compatibility with Android 12
<br>

# 2.8.3 Release notes (09-09-2021)
### Fixed
* Fixed "NaN in not a valid number" crash during the creation of Position object
<br>

# 2.8.2 Release notes (02-09-2021)
### Fixed
* Fixed IllegalArgumentException releated to queue upload
<br>

# 2.8.1 Release notes (14-04-2021)
### Enhancements
* Migrated SDK repository from bintray to mymavenrepo due to bintray shutting down   
<br>

# 2.8.0 Release notes (19-02-2021)
### Improvements
* Migrated SDK to AndroidX
<br>

# 2.7.2 Release notes (26-01-2021)
### Improvements
* Improved remote geofences manager
<br>

# 2.7.1 Release notes (19-01-2021)
### Improvements
* Added a manager for remote geofences
<br>

# 2.7.0 Release notes (15-01-2021)
### Improvements
* Added automatic resolution of background location permission
* Added API that set wakeups reduction mode:
```java
    GeoUniq.getInstance(getActivity()).setWakeUpsReduction(booleanValue);
    GeoUniq.getInstance(getActivity()).isWakeUpsReduction();
```
* Added API that set balanced power mode:
```java
    GeoUniq.getInstance(getActivity()).setBalancedPowerAccuracy(booleanValue);
    GeoUniq.getInstance(getActivity()).isBalancedPowerAccuracy()
```
* Added "Accuracy Permission" information in device model
### Fixed
* NPE releated to tracker engine
* OOM during queue read and write operations
* Sometimes confirmatio duration is not updated
<br>

# 2.6.3 Release notes (12-11-2020)
### Fixed
* Fixed NPE releated to tracker engine refactor

<br>

# 2.6.0 Release notes (09-10-2020)
### Improvements
* Refactored tracker engine due to reduce the number of wake ups

<br>

# 2.5.7 Release notes (06-07-2020)

### Improvements
* Reduced delay befor queue upload
* Added "when in use" status for location permission

### Fixed
* Fixed some crash and ANR releated to queue size

<br>

# 2.5.6 Release notes (12-06-2020)

### Improvements
* Reduced number of wake-ups

<br>

# 2.5.5 Release notes (21-05-2020)

### Fixed
* Internal bug fix and improvements

<br>

# 2.5.4 Release notes (15-05-2020)

### Fixed
* Improvements on position integrity check 
* Improved device registration flow
* Added controller for remote calls
* Made Network module compatible with Android 10
* Improved always-on strategy
* Increased the number of detection during app foreground state

<br>

# 2.5.1 Release notes (10-04-2020)

### Fixed
* General bug fix

<br>

# 2.5.0 Release notes (27-03-2020)

### Improvements
* Extend position model with an array of positions that confirm visit
* Improved tracking

<br>

# 2.4.9 Release notes (23-03-2020)

### Fixed
* Fixed a bug during the read/write of consent map

<br>

# 2.4.8 Release notes (28-01-2020)

### Enhancements
* Added country code in device model

<br>

# 2.4.7 Release notes (23-01-2020)

### Enhancements
* Clean and improve codebase

### Fixed
* General bug fix

<br>

# 2.4.6 Release notes (03-12-2019)

### Fixed
* Improved tracking listener functionality

<br>

# 2.4.5 Release notes (11-11-2019)
### Enhancements
* Migration to Appcenter

### Fixed
* General bug fix

<br>

# 2.4.4 Release notes (30-09-2019)
### Enhancements
* Tracking improvements 

### Fixed
* Location history request return enqueued position not in selected date range
* Foregorund Service crash

<br>

# 2.4.3 Release notes (19-09-2019)
### Fixed
* Renamed all xml layout files to avoid filename conflicts

<br>

# 2.4.2 Release notes (09-09-2019)
### Fixed
* Fixed Foregorund Service notification
* Minor bug fix

### Enhancements
*  Now Android Studio show the GeoUniq SDK documentation automatically
*  Added limit to stored log files

<br>

2.4.1 Release notes (15-07-2019)
=============================================================
### Fixed
* Fixed a bug that in case of network error, retry to make network calls not once but endlessly.

### Enhancements
*  Enabled R8 as code shrinker

<br>

2.4.0 Release notes (08-07-2019)
=============================================================

### Enhancements
*  Refactored privacy popup, now is GDPR compliant

<br>

2.3.7 Release notes (26-06-2019)
=============================================================

### Enhancements
*  Extended Position model with bearing, altitude and vertical accuracy informations

<br>

2.3.6 Release notes (30-05-2019)
=============================================================

### Enhancements

* Now you can disable Motion Activity module adding in AndroidManifest.xml this meta data:
```xml
    <application>
    //...
        <meta-data
            android:name="com.geouniq.disable_motion_activity"
            android:value="true" />
    </application>
```
<br>

2.3.5 Release notes (08-05-2019)
=============================================================

### Enhancements

* Added new position filter based on average speed
* Added Geouniq partners list in privacy consent dialog

<br>

2.3.4 Release notes (19-04-2019)
=============================================================

### Fixed

* General bug fix

<br>

2.3.3 Release notes (09-04-2019)
=============================================================

### Fixed

* Fixed crash on Huawey devices with Android 8
