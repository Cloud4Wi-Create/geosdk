# Travel-StatisticInput

Name        |Type      
------------|----------
select | [`Travel-Segment`](/api/reference/data-modelsata-models/r-segment/travel.md) 
segmentBy | [`Travel-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/travel.md) 
compute | [`Travel-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/travel.md) 
filter | [`Travel-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/travel.md) 

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
        "spatialGranularity": {
            "inside": ["metropolis", "city"]
        },
        "duration": {"gte": 0, "lt": 100},
        "travelledDistance": {"gte": 0, "lt": 100},
        "averageSpeed": {"gte": 0, "lt": 100},
        "startEndDistance": {"gte": 0, "lt": 100},
        "straightIndex": {"gte": 0, "lt": 100},
        "stationaryIndex": {"gte": 0, "lt": 100}
    },
    "segmentBy": {
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
        "spatialGranularity": {
            "inside": {
                "byLevel": 1
            }
        }
    },
    "compute": {
        "count": true,
        "totalTravelledDistance": true,
        "totalDuration": true,
        "averageTravelledDistance": true,
        "averageDuration": true,
        "averageStartEndDistance": true,
        "averageSpeed": true,
        "averageStraightIndex": true,
        "averageStationaryIndex": true
    },
    "filter": {
        "count": {"eq": 1, "neq": 1, "gt": 1, "gte": 1, "lt": 1, "lte": 1},
        "totalTravelledDistance": {},
        "totalDuration":  {},
        "averageTravelledDistance":  {},
        "averageDuration":  {},
        "averageStartEndDistance":  {},
        "averageSpeed":  {},
        "averageStraightIndex":  {}
        "averageStationaryIndex": {}
    }
}
```

