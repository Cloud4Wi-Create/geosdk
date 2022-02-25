# Flight-Segment

Name        |Type      
------------|----------
deviceBase | [`Point-DeviceBase-Selection`]() 
space | [`Sequence-Space-Selection`]() 
time | [`Interval-Time-Selection`]() 
airports | [`Sequence-Airports-Selection`]() 
flightRange | [`Point-FlightRange-Selection`]() 
duration | [`ComparisonCondition`]() 
travelledDistance | [`ComparisonCondition`]() 

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
    "airports": {
        "inside" : {
            "iataCode" : ["FCO", "JFK"],
            "continent" : ["Europe", "Asia"],
            "country": ["Italy", "Japan"],
            "city": ["Rome", "Milan"],
        },
        "intersect" : {},
        "start" : {},
        "end" : {}
    },
    "flightRange":{
        "inside" : {
            "national" : true,
            "international" : false,
            "intercontinental": true
        }
    },
    "duration": {"gte": 0, "lt": 100},
    "travelledDistance": {"gte": 0, "lt": 100}
}
```
