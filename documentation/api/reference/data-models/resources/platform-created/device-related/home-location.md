* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../../index.md)  
    * [Reference](../../../../index.md)
        * [Data models](../../../index.md)
		    * [Resources Data models](../../index.md)
                * [Platform-created Resources Data models](../index.md)
                    * [Device-related Resources Data models](index.md)

# HomeLocation


Data Model used to represent a [*Home Location*](../../../../resources/platform-created/device-related/home-location.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](../../../common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
geo | [`GeoPoint`](../../../common/geo-point.md) | ANY valid `GeoPoint` | The geographical position of the *Home Location*.
primary | `boolean` | ANY valid `boolean` | Whether this *Home Location* is the one where the user spends more time.

## Example Object


```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
        "customId": "My first device",
         "idfa": "550e8400-e29b-41d4-a716-446655440000"
    },
    "primary": true,
    "geo": {
        "lat": -10.876,
        "lng": 15.7453
    }
}
```
