# WorkLocation


Data Model used to represent a [*Work Location*](/api/resources/platform-created/device-related/work-location.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](/api/data-models/common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
geo | [`GeoPoint`](/api/data-models/common/geopoint.md) | ANY valid `GeoPoint` | The geographical position of the *Work Location*.
primary | `boolean` | ANY valid `boolean` | Whether this *Work Location* is the one where the user spends more time.

## Example Object


```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
        "customId": "My first device",
        "token": "TOKEN"
    },
    "primmary": true,
    "geo": {
        "lat": 41.5,
        "lng": 12.4
    }
}
```