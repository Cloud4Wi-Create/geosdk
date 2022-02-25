# DetectedPosition-StatisticOutput

Name        |Type      | Description
------------|----------|------------
segment | [`DetectedPosition-Segment`](/api/reference/data-modelsata-models/r-segment/detected-position.md) | Indicates which Segment of Detected Positions the item refers to. This field is not provided if no Segmentation as been requested.
metrics | [`DetectedPosition-AggregatedMetrics`](/api/reference/data-modelsata-models/r-aggregated-metrics/detected-position.md)  | Contains the aggregated metrics computed for the Statistic on Detected Positions.

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
                "explicitArea": {
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
            }
        },
        "time": {
            "intersect": {
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
                    "inside": {"global": 0.03, "selection": 0.2}
                },
                "space": {
                    "inside": {"global": 0.03, "selection": 0.2}
                },
                "time":{
                    "inside": {"global": 0.03, "selection": 0.2}
                    "intersect": {"global": 0.03, "selection": 0.2}
                    "start": {"global": 0.03, "selection": 0.2}
                    "end": {"global": 0.03, "selection": 0.2}
                }
            }
        }
    }
}
```

