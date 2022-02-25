# Visit-StatisticOutput

Name        |Type      | Description
------------|----------|------------
segment | [`Visit-Segment`](/api/reference/data-modelsata-models/r-segment/visit.md) | Indicates which Segment of Visits the item refers to. This field is not provided if no Segmentation as been requested.
metrics | [`Visit-AggregatedMetrics`](/api/reference/data-models/r-aggreated-metrics/visit.md)  | Contains the aggregated metrics computed for the Statistic on Visits.

```json
{
	"segment": {
    	"deviceBase": {
            "inside" : {
                "deviceId" : ["D1"]
            }
        },
		"space": {
			"inside": {
				"savedAreas": {
					"name": ["Rome"]
				}
			}
		},
		"time": {
			"inside": {
				"intervals": [{
					"from": {
						"relative": 0
					},
					"to": {
						"relative": 0
					}
				}]
			},
			"intersect": {
				"intervals": [{
					"from": {
						"relative": 0
					},
					"to": {
						"relative": 0
					}
				}]
			},
			"start": {
				"intervals": [{
					"from": {
						"relative": 0
					},
					"to": {
						"relative": 0
					}
				}]
			},
			"end": {
				"intervals": [{
					"from": {
						"relative": 0
					},
					"to": {
						"relative": 0
					}
				}]
			}
		},
		"spatialGranularity": {
			"inside": ["metropolis"]
		},
		"duration": {
			"lte": 2
		}
	},
	"metrics": {
		"count": {
			"absolute": 200,
			"shares": {
				"overall": {
					"global": 0.01,
					"selection": 0.1
				},
				"deviceBase": {
					"inside": {
						"overall": 0.03,
						"selection": 0.2
					}
				},
				"space": {
					"inside": {
						"overall": 0.03,
						"selection": 0.2
					}
				},
				"time": {
					"inside": {
						"overall": 0.03,
						"selection": 0.2
					},
					"intersect": {
						"overall": 0.03,
						"selection": 0.2
					},
					"start": {
						"overall": 0.03,
						"selection": 0.2
					},
					"end": {
						"overall": 0.03,
						"selection": 0.2
					}
				},
				"spatialGranularity": {
					"inside": {
						"overall": 0.03,
						"selection": 0.2
					}
				}
			}
		}
	}
}
```

