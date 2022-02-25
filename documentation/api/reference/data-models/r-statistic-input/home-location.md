# HomeLocation-StatisticInput

Name        |Type      
------------|----------
select | [`HomeLocation-Segment`](/api/reference/data-modelsata-models/r-segment/home-location.md) 
segmentBy | [`HomeLocation-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/home-location.md) 
compute | [`HomeLocation-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/home-location.md) 
filter | [`HomeLocation-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/home-location.md) 

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

