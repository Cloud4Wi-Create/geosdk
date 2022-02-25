# Activity-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-SelectionOperation`]() 
space | [`Sequence-Space-SelectionOperation`]() 
time | [`Interval-Time-SelectionOperation`]() 
motionType | [`Point-MotionType-SelectionOperation`]()
duration | [`ComparisonCondition`]() 
travelledDistance | [`ComparisonCondition`]() 
averageSpeed | [`ComparisonCondition`]() 
startEndDistance | [`ComparisonCondition`]() 
startightIndex | [`ComparisonCondition`]() 

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
        },
        "intersect": {},
        "start": {},
        "end": {}
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
    "motionType": {
        "inside": ["stationary", "walking"]
    },
    "duration": {"gte": 0, "lt": 100},
    "travelledDistance": {"gte": 0, "lt": 100},
    "averageSpeed": {"gte": 0, "lt": 100},
    "startEndDistance": {"gte": 0, "lt": 100},
    "straightIndex": {"gte": 0, "lt": 100}
}
```

