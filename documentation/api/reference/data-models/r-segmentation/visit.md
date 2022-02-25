# Visit-Segmentation

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/point-device-base.md) 
space | [`Multipoint-Space-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/multipoint-space.md) 
time | [`Interval-Time-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/interval-time.md) 
spatialGranularity | [`Point-SpatialGranularity-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/point-spatial-granularity.md) 

```json
{  
    "deviceBase": {
        "inside": {
            "device": 1,
            "clientApp": 1,
            "osName": 1
        }
    },
    "space": {
        "inside": {
            "geohash": 5
        },
        "intersect":{}
    },
    "time": {
        "inside":{
            "continuousInterval" : {
                "count" : 3,
                "unit" : "days"
            },
            "periodicInterval" : {
            	"offset": 5,
            	"periodicity": "daily"
            }
        },
        "intersect": {},
        "start": {},
        "end": {}
    },
    "spatialGranularity": {
        "inside": {
            "level": 1
        }
    }
}
```

