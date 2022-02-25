* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../../index.md)  
    * [Reference](../../../../index.md)
        * [Data models](../../../index.md)
		    * [Resources Data models](../../index.md)
                * [Platform-created Resources Data models](../index.md)
                    * [Device-related Resources Data models](index.md)

# Position

Data Model used to represent a [*Position*](../../../../resources/platform-created/device-related/position.md) Resource.

## Fields Specification

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](../../../common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
detectedAt | [`Date`](../../../common/date.md) | ANY valid `Date` | The date and time when the position was detected.
geo | [`GeoPoint`](../../../common/geo-point.md) | ANY valid `GeoPoint` | The geographical position
speed | `Number` | ANY | An estimation of the speed in m/s.

## Example Object

```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
            "clientAppId": "app1",
            "customId": "My first device",
            "idfa": "550e8400-e29b-41d4-a716-446655440000"
    },
    "detectedAt": "2016-03-11T08:31:07Z",
    "geo": {
        "lat": 43.7228778,
        "lng": 10.3991758
    },
    "speed": 5.0
}
```
