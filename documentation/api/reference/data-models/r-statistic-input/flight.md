# Flight-StatisticInput

Name        |Type      
------------|----------
select | [`Flight-Segment`](/api/reference/data-modelsata-models/r-segment/flight.md) 
segmentBy | [`Flight-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/flight.md) 
compute | [`Flight-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/flight.md) 
filter | [`Flight-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/flight.md) 

```json
{
    "select": {
        "deviceBase": {
            "inside" : {
                "deviceIds" : ["D1", "D2", "D3"],
                "applicationIds" : ["A1", "A2", "A3"],
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
    },
    "segmentaBy": {
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
    },
    "compute": {
        "count": true,
        "totalTravelledDistance": true,
        "totalDuration": true,
        "averageTravelledDistance": true,
        "averageDuration": true
    },
    "filter": {
        "count": {"eq": 1, "neq": 1, "gt": 1, "gte": 1, "lt": 1, "lte": 1},
        "totalTravelledDistance": {},
        "totalDuration":  {},
        "averageTravelledDistance":  {},
        "averageDuration":  {}
    }
}
```
