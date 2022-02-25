# LivingArea-StatisticInput

Name        |Type      
------------|----------
select | [`LivingArea-Segment`](/api/reference/data-modelsata-models/r-segment/living-area.md) 
segmentBy | [`LivingArea-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/living-area.md) 
compute | [`LivingArea-RequestedMetrics`](/api/reference/data-modelsata-models/r-requested-metrics/living-area.md) 
filter | [`LivingArea-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/living-area.md) 

```json
{
    "select": {
        "deviceBase": {
            "inside" : {
                "deviceIds" : ["D1", "D2", "D3"],
                "applicationIds" : ["A1", "A2", "A3"],
                "osName" : ["android", "iOs"]
            },
            "intersect": {}
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
            },
            "intersect": {}
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

