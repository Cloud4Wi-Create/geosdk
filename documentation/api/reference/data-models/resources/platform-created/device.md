* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../../index.md)  
    * [Reference](../../../../index.md)
        * [Data models](../../../index.md)
		    * [Resources Data models](../../index.md)
                * [Platform-created Resources Data models](index.md)

# Device

Data Model used to represent a [*Device*](/api/reference/resources/resources/platform-created/device.md) Resource.

## Fields Specification

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
id | `String` | ANY valid [Device ID](/service-architecture.md) | The ID assigned to GeoUniq Analytics platform to the specific [Device](/service-architecture.md) 
createdAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | ANY valid `Date` | The date and time when the *Device* has been registered
os | `JSON` | N.A. | Info on the operating system of the device
os.name | `String` | {`"android"`; `"ios"`} | The name of the operating system
os.version | `String` | ANY | The version of the operating system
clientApp | `JSON` | N.A. | Info on the [Client App](/service-architecture.md) which the *Device* belongs to
clientApp.id | `String` | ANY valid Client App ID | The ID assigned by GeoUniq Analytics platform to the specific Client App
clientApp.name | `String` | ANY | The package name (for Android) or the Bundle Id (for iOS), as provided for the Client App when it has been [configured for the Project](/service-architecture.md)
customId | `String` | ANY | The Custom Id set for the *Device* if any. `null` otherwise.
token | `String` | ANY | The Token set for the *Device* if any. `null` otherwise.

## Example Object

```json
{
    "id": "56fa6815af4ecd00010b000a",
    "createdAt": "2016-03-29T11:33:41Z",
    "os": {
        "name": "android",
        "version": "5.0.2"
    },
    "clientApp": {
        "id": "56e0946fd7298a0001a5f414",
        "name": "com.geouniq.example"
    },
    "customId": "My first device"
}
```
