# Flight-Segmentation

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-Segmentation`]() 
space | [`Sequence-Space-Segmentation`]() 
time | [`Interval-Time-Segmentation`]() 
airports | [`Sequence-Airports-Segmentation`]() 
flightRange | [`Point-FlightRange-Segmentation`]() 

```json
{  
    "deviceBase": {
        "inside": {
            "byDevice": 1,
            "byClientApp": 1,
            "byOsName": 1
        }
    },
    "space": {
        "inside": {
            "byGeohash": 5
        },
        "intersect": {},
        "start": {},
        "end": {}
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
    "airports": {
        "inside": {
            "byIataCode": 1
            "byContinent": 1
            "byCountry": 1
            "byCity": 1
        },
        "intersect": {},
        "start": {},
        "end": {}
    }
}
```

