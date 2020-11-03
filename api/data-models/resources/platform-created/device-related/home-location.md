# HomeLocation


Data Model used to represent a [*Home Location*](/api/resources/platform-created/device-related/home-location.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](/api/data-models/common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
geo | [`GeoPoint`](/api/data-models/common/geo-point.md) | ANY valid `GeoPoint` | The geographical position of the *Home Location*.
primary | `boolean` | ANY valid `boolean` | Whether this *Home Location* is the one where the user spends more time.

## Example Object


```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
        "customId": "My first device",
        "token": "TOKEN"
    },
    "primary": true,
    "geo": {
        "lat": -10.876,
        "lng": 15.7453
    }
}
```