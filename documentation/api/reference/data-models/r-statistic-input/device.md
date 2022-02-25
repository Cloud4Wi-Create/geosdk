# Device-StatisticInput

Name        |Type      
------------|----------
select | [`Device-Segment`](/api/reference/data-modelsata-models/r-segment/device.md) 
segmentBy | [`Device-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/device.md) 
compute | [`Device-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/device.md) 
filter | [`Device-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/device.md) 

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
            }
        }
    },
    "segmentBy": {
        "deviceBase": {
            "inside": {
                "device": 1,
                "clientApp": 1,
                "osName": 1
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
            }
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
