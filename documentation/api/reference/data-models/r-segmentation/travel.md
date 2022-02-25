# Travel-Segmentation

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/point-device-base.md) 
space | [`Sequence-Space-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/sequence-space.md) 
time | [`Interval-Time-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/multipoint-space.md) 
motionType | [`Point-MotionType-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/point-motion-type.md)

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
        "intersect": {},
        "start": {},
        "end": {},
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

