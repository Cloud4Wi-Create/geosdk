# Visit

Data Model used to represent a [*Visit*](/api/resources/platform-created/device-related/visit.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
device | [`DeviceReference`](/api/data-models/common/device-reference.md) | ANY valid `DeviceReference` | Indicates which *Device* the Resource refers to. 
startedAt | [`Date`](/api/data-models/common/date.md) | ANY valid `Date` | The date and time when the *Visit* started.
endedAt | [`Date`](/api/data-models/common/date.md) | ANY valid `Date` | The date and time when the *Visit* finished. If `null`, then the *Visit* is still in progress.
inProgress | `Boolean` | ANY valid `Boolean` | Whether the Visit is still in progress or not
geo.area | [`GuGeoJSON`](/api/data-models/common/gu-geo-json.md) | ANY valid `GuGeoJSON` | The geographical area which the *Visit* refers to.
geo.referencePosition | [`GeoPoint`](/api/data-models/common/geo-point.md) | ANY valid `GeoPoint` | A reference position for the Visit.
granularityLevel | `String` | One of the values defined for [Spatial Granularity](/api/dimensions/spatial-granularity.md) | The spatial granularity level.
duration | `Integer` | Any `n > 0` | The duration of the *Visit* in seconds.

## Example Object


```json
{
    "device" : {
        "id": "56fa6815af4ecd00010b000a",
        "customId": "My first device",
        "token": "TOKEN"
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