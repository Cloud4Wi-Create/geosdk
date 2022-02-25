* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../../index.md)  
    * [Reference](../../../../index.md)
        * [Data models](../../../index.md)
		    * [Resources Data models](../../index.md)
                * [Platform-created Resources Data models](../index.md)
                    * [Device-related Resources Data models](index.md)

# Visit

Data Model used to represent a [*Visit*](../../../../resources/platform-created/device-related/visit.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](../../../common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
startedAt | [`Date`](../../../common/date.md) | ANY valid `Date` | The date and time when the *Visit* started.
endedAt | [`Date`](../../../common/date.md) | ANY valid `Date` | The date and time when the *Visit* finished. If `null`, then the *Visit* is still in progress.
inProgress | `Boolean` | ANY valid `Boolean` | Whether the Visit is still in progress or not
geo.area | [`GuGeoJSON`](../../../common/gu-geo-json.md) | ANY valid `GuGeoJSON` | The geographical area which the *Visit* refers to.
geo.referencePosition | [`GeoPoint`](../../../common/geo-point.md) | ANY valid `GeoPoint` | A reference position for the Visit.
granularityLevel | `String` | One of the values defined for [Spatial Granularity](../../../../dimensions/spatial-granularity.md) | The spatial granularity level.
duration | `Integer` | Any `n > 0` | The duration of the *Visit* in seconds.

## Example Object


```json
{
    "device" : {
       "id": "device1",
        "clientAppId": "app1",
        "customId": "my device",
        "idfa": "550e8400-e29b-41d4-a716-446655440000"
    },
    "startedAt": "2016-03-11T08:30:00Z",
    "endedAt": "2016-03-11T08:40:00Z",
    "geo":{
        "referencePosition": {
            "lat": 10.0,
            "lng": 10.0
        },
        "area": {
            "type" : "feature",
            "geometry" : { 
                "type": "Polygon", 
                "bbox": [-10.0, -10.0, 10.0, 10.0],
                "coordinates": [
                    [
                        [-10.0, -10.0],
                        [10.0, -10.0],
                        [10.0, 10.0],
                        [-10.0, 10.0]
                    ]
                ]
            },
            "properties" : null
        }
    },
    "granularityLevel": "building",
    "duration": 600
}
```
