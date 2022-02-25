# Visit-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-device-base.md) 
space | [`Point-Space-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-space.md) 
time | [`Interval-Time-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/interval-time.md) 
spatialGranularity | [`Point-SpatialGranularity-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-spatial-granularity.md) 
duration | [`ComparisonCondition`](/api/reference/data-modelsata-models/common/comparison-condition.md) 

```json
{
    "deviceBase": {
        "inside" : {
            //only one field allowed
            "deviceId" : ["D1", "D2", "D3"], 
            "applicationId" : ["A1", "A2", "A3"],
            "osName" : ["android", "iOs"]
        }
    },
    "space": {
        "inside" : {
            "explicitArea": {
                "features": [
                    {
                        "geometry": null,
                        "properties": {
                            "circles": [
                                {
                                    "center": {
                                        "lat": 41.898202,
                                        "lng": 12.492034
                                    },
                                    "radius": 1000
                                }
                            ]
                        },
                        "type": "Feature"
                    }
                ],
                "type": "FeatureCollection"
            }
        }
    },
    "time": {
        "inside" : {
            "intervals" : [
                {
                    "from" : {
                        //only one between absolute and relative fields is allowed
                        "absolute": "2016-01-01T00:00:00Z",
                        "relative": -100
                    },
                    "to" : {
                        //only one between absolute and relative fields is allowed
                        "absolute": "2016-01-01T00:00:00Z",
                        "relative": -100
                    }
                }
            ]
        },
        // Multiple operators allowed. Use the same object as above for "time.inside"
        "intersect": {},
        "start": {},
        "end": {}
    },
    "spatialGranularity": {
        "inside": ["metropolis", "city"]
    },
    "duration": {"gte": 0, "lt": 100}
}
```

