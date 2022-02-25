# WorkLocation-StatisticInput

Name        |Type      
------------|----------
select | [`WorkLocation-Segment`](/api/reference/data-modelsata-models/r-segment/work-location.md) 
segmentBy | [`WorkLocation-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/work-location.md) 
compute | [`WorkLocation-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/work-location.md) 
filter | [`WorkLocation-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/work-location.md) 

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
        }
    },
    "segmentBy": {
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
        }
    },
    "compute": {
        "count": true
    },
    "filter": {
        "count": {"gte": 0, "lt": 10}
    }
}
```

