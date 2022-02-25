# Visit-StatisticInput

Name        |Type      
------------|----------
select | [`Visit-Segment`](/api/reference/data-modelsata-models/r-segment/visit.md) 
segmentBy | [`Visit-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/visit.md) 
compute | [`Visit-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/visit.md) 
filter | [`Visit-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/visit.md) 

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
                "explicitArea" : {}
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
                ]
            },
            "intersect": {},
            "start": {},
            "end": {}
        },
        "spatialGranularity": {
            "inside": ["metropolis", "city"]
        },
        "duration": {"gte": 0, "lt": 100}
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
        },
        "spatialGranularity": {
            "inside": {
                "byLevel": 1
            }
        }
    },
    "compute": {
        "count": true,
        "totalDuration": true
    },
    "filter": {
        "count": {"eq": 1, "neq": 1, "gt": 1, "gte": 1, "lt": 1, "lte": 1}
    }
}
```

