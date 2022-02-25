* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Finding devices that have visited a specific POI

The set of devices that have visited a specific point of interest (POI) in a specific time interval can be obtained through a [Statistic](/api/concepts/statistics.md) on [Detected Positions](/api/reference/resources/platform-created/device-related/position.md) at the following endpoint ([full doc here](/api/reference/endpoints/statistics/detected-position.md)):

`POST https://api.geouniq.com/v1/statistics/detected-positions` 



The body of the request has to contain:
* a [Selection Operation](/api/concepts/resource-selection.md) on the [*Space*](/api/reference/dimensions/space.md) Dimension (`"select.space.inside"`).
Specifically, the [*Space Segment*](/api/reference/data-models/d-segment/space.md) has to indicate the geographical area corresponding to the specific POI (in the example below, the area is provided as a circle);
* a [Selection Operation](/api/concepts/resource-selection.md) on the [*Time*](/api/reference/dimensions/time.md) Dimension (`"select.time.start"`).
Specifically, the [*Time Segment*](/api/reference/data-models/d-segment/time.md) has to indicate the time interval we are interseted in (in the example below, we consider the last 10 minutes).
* a [Segmentation Operation](/api/concepts/statistics.md#segmentation-operation) on the [*Device Base*](/api/reference/dimensions/device-base.md) Dimension.
Specifically, the criterion to use is [by device](/api/reference/dimensions/device-base.md#segmentation-criteria) in order to aggregate Detected Position for each specific device.
* the `"compute"` field indicating to compute the aggregated metric `count`

### Example Request body

```json
{
	"select": {
		"space": {
			"inside": {
				"explicitArea": {
				    "type" : "Feature",
				    "geometry" : null,
				    "properties" : {
				        "circles" : [{
				            "center": {"lat": 10.0, "lng": 10.0},
				            "radius": 50
				        }]
				    }
				}
			}
		},
		"time": {
			"start": {
				"intervals": [{
				    "from": {
				        "relative": -600
				    },
				    "to": {
				        "relative": 0
				    }
				}]
			}
		}
	},
	"segmentBy": {
		"deviceBase": {
			"inside": {
				"device": 1
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

The Response provided by the API will contain a set of [*Items*](/api/reference/general-aspects/pagination.md) each of which is related to a specific device (`"segment.deviceBase.inside.deviceId"`).
Each Item contains the counter of the number of positions found for that device within the selected area and time period (`"metrics.count.absolute"`).
Since we are not interested in the number of positions but only in whether the device has visited the area, we can neglect the count and only consider the device ID contained in each Item

### Example Response body

```json
{
	"items": [{
		"segment": {
			"deviceBase": {
				"inside": {
					"deviceId": ["D1"]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 2
			}
		} 
	},{
		"segment": {
			"deviceBase": {
				"inside": {
					"deviceId": ["D2"]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 6
			}
		} 
	}],
	"paging": {
		"next": null
	}
}
```

If we are only interested in the number of devices and not in which specifc devices, then we can also neglect the Device IDs and simply count the number of items contained in the response

> The response of the API is paginated, so you need to retrieve all pages as explained [here](/api/reference/general-aspects/pagination.md)
