* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../../index.md)  
    * [Reference](../../../../index.md)
        * [Data models](../../../index.md)
		    * [Resources Data models](../../index.md)
                * [Platform-created Resources Data models](../index.md)
                    * [Device-related Resources Data models](index.md)

# WorkLocation


Data Model used to represent a [*Work Location*](../../../../resources/platform-created/device-related/work-location.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](../../../common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
geo | [`GeoPoint`](../../../common/geopoint.md) | ANY valid `GeoPoint` | The geographical position of the *Work Location*.
primary | `boolean` | ANY valid `boolean` | Whether this *Work Location* is the one where the user spends more time.

## Example Object


```json
{
    "device" : {
        "id": "device1",
        "clientAppId": "app1",
        "customId": "my device",
        "idfa": "550e8400-e29b-41d4-a716-446655440000"
    },
    "primmary": true,
    "geo": {
        "lat": 41.5,
        "lng": 12.4
    }
}
```
