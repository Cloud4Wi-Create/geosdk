# Activity-StatisticOutput

Name        |Type      | Description
------------|----------|------------
segment | [`Activity-Segment`](/api/reference/data-modelsata-models/r-segment/activity.md) | Indicates which Segment of Activities the item refers to. This field is not provided if no Segmentation as been requested.
metrics | [`Activity-AggregatedMetrics`](/api/reference/data-modelsata-models/r-aggregated-metrics/activity.md)  | Contains the aggregated metrics computed for the Statistic on Activities.

```json
{
    "segment": {
        "deviceBase": {
        	"inside": {
        		"clientAppId": ["A1"]
        	}
        },
        "space": {
            "inside": {
                "type" : "feature",
                "geometry" : { 
                    "type": "Polygon", 
                    "bbox": [-10.0, -10.0, 10.0, 10.0],
                    "coordinates": [
            			[
            				[-10.0, -10.0],
            				[10.0, -10.0],
            				[10.0, 10.0],
            				[-10.0, 10.0]
            			]
            		]
                },
                "properties" : null
            }
        },
        "time": {
            "inside": {
                "intervals": [{
                    "from":{"relative": 0},
                    "to":{"relative": 0}
                }]
            },
            "intersect": {
                "intervals": [{
                    "from":{"relative": 0},
                    "to":{"relative": 0}
                }]
            },
            "start": {
                "intervals": [{
                    "from":{"relative": 0},
                    "to":{"relative": 0}
                }]
            },
            "end": {
                "intervals": [{
                    "from":{"relative": 0},
                    "to":{"relative": 0}
                }]
            }
        },
        "speed": {"lte": 2}
    },
    "metrics": {
        "count" : {
            "absolute": 200,
            "shares": {
                "overall": {"global": 0.01, "selection": 0.1}
                "deviceBase": {
                    "inside": {"global": 0.01, "selection": 0.1}
                },
                "space": {
                    "inside": {"global": 0.01, "selection": 0.1}
                },
                "time":{
                    "inside": {"global": 0.01, "selection": 0.1},
                    "intersect": {"global": 0.01, "selection": 0.1},
                    "start": {"global": 0.01, "selection": 0.1},
                    "end": {"global": 0.01, "selection": 0.1}
                }
            }
        }
    }
}
```

