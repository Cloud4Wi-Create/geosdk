# Device-StatisticOutput

Name        |Type      | Description
------------|----------|------------
segment | [`Device-Segment`](/api/reference/data-modelsata-models/r-segment/device.md) | Indicates which Segment of *Device* Resources the item refers to. This field is not provided if no Segmentation as been requested.
metrics | [`Device-AggregatedMetrics`](/api/reference/data-modelsata-models/r-aggregated-metrics/device.md)  | Contains the aggregated metrics computed for the Statistic on *Device* Resources.

```json
{
	"segment": {
		"deviceBase": {
			"inside": {
				"clientAppId": ["A1"]
			}
		},
		"time": {
			"inside": {
				"intervals": [{
					"from": {
						"absolute": "2017-01-01T00:00:00Z"
					},
					"to": {
						"absolute": "2017-01-01T01:00:00Z"
					}
				}]
			}
		}
	},
	"metrics": {
		"count": {
			"absolute": 200
	}
}
```

