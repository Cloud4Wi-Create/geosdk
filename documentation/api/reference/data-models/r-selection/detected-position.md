# DetectedPosition-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-device-base.md) 
space | [`Point-Space-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/point-space.md) 
time | [`Interval-Time-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/interval-time.md) 
speed | [`ComparisonCondition`](/api/reference/data-modelsata-models/common/comparison-condition.md) 

```json
{
    "deviceBase": {
        "inside" : {
            "deviceId" : ["D1", "D2", "D3"],
            "applicationId" : ["A1", "A2", "A3"],
            "osName" : ["android", "iOs"]
        }
    },
    "space": {
        "inside" : {
            "explicitArea" : {},
            "implicitAreas" : ["living", "home", "work"],
            "savedAreas" : {}
        }
    },
    "time": {
        "inside" : {
            "intervals" : [
                {
                    "from" : {
                        "absolute": "2016-01-01T00:00:00Z",
                        "relative": -100
                    },
                    "to" : {
                        "absolute": "2016-01-01T00:00:00Z",
                        "relative": -100
                    }
                }
            ],
            "periodicity" : {
        		"offset": -2,
        		"hoursOfTheDay": [1, 2, 6, 7, 8, 9, 21, 22],
        		"daysOfTheWeek": ["FRY", "SAT", "SUN"],
        		"monthsOfTheYear": ["JAN", "DEC"]
        	}
        },
        "intersect": {},
        "start": {},
        "end": {}
    },
    "speed": {"gte": 0, "lt": 100}
}
```

