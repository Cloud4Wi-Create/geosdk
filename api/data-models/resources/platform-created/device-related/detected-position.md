# DetectedPosition

Data Model used to represent a [*Detected Position*](/api/resources/platform-created/device-related/detected-position.md) Resource.

## Fields Specification

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](/api/data-models/common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
detectedAt | [`Date`](/api/data-models/common/date.md) | ANY valid `Date` | The date and time when the position was detected.
geo | [`GeoPoint`](/api/data-models/common/geo-point.md) | ANY valid `GeoPoint` | The geographical position
speed | `Number` | ANY | An estimation of the speed in m/s.

## Example Object




```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
        "customId": "My first device",
        "token": "TOKEN"
    },
    "detectedAt": "2016-03-11T08:31:07Z",
    "geo": {
        "lat": 43.7228778,
        "lng": 10.3991758
    },
    "speed": 5.0
}
```