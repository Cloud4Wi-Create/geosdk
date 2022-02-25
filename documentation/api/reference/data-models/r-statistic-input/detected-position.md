# DetectedPosition-StatisticInput

Name        |Type      
------------|----------
select | [`DetectedPosition-Segment`](/api/reference/data-modelsata-models/r-segment/detected-position.md) 
segmentBy | [`DetectedPosition-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/detected-position.md) 
compute | [`DetectedPosition-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/detected-position.md) 
filter | [`DetectedPosition-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/detected-position.md) 

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
            		"daysOfTheWeek": ["friday", "saturday", "sunday"],
            		"monthsOfTheYear": ["january", "december"]
            	}
            },
            "intersect": {},
            "start": {},
            "end": {}
        },
        "speed": {"gte": 0, "lt": 100}
    },
    "segmentBy": {
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
    },
    "compute": {
        "count": true
    },
    "filter": {
        "count": {"gt" : 0, "lt": 10}
    }
}
```
