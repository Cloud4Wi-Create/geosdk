# DetectedPosition-Segmentation

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/point-device-base.md) 
space | [`Point-Space-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/point-space.md) 
time | [`Interval-Time-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/interval-time.md) 

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
        }
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
    }
}
```

