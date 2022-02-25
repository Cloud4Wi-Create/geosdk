* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Count the number of devices in a place at a given time

The number of devices that are in a specific point of intersets (POI) at a given time can be obtained through a [Statistic](/api/concepts/statistics.md) on [Detected Positions](/api/reference/resources/platform-created/device-related/position.md) at the following endpoint ([full doc here](/api/reference/endpoints/statistics/detected-position.md)):

`POST https://api.geouniq.com/v1/statistics/detected-positions` 



The body of the request has to contain:
* a [Selection Operation](/api/concepts/resource-selection.md) on the [*Space*](/api/reference/dimensions/space.md) Dimension (`"select.space.inside"`).
Specifically, the [*Space Segment*](/api/reference/data-models/d-segment/space.md) has to indicate the geographical area corresponding to the specific POI (in the example below, the area is provided as a circle);
* a [Selection Operation](/api/concepts/resource-selection.md) on the [*Time*](/api/reference/dimensions/time.md) Dimension (`"select.time.intersect"`).
Specifically, the [*Time Segment*](/api/reference/data-models/d-segment/time.md) has to indicate the time instant we are interseted in (in the example below we consider "now").
Note that the time interval has the same value for "from" and "to" and that we are using the "intersect" operator. This way, we are selecting the last position before the indicated instant for each device.
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
			"intersect": {
				"intervals": [{
				    "from": {
				        "relative": 0
				    },
				    "to": {
				        "relative": 0
				    }
				}]
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

The Response provided by the API will contain only one [*Item*](/api/reference/general-aspects/pagination.md).
This Item contains the counter of the number of positions found within the selected area at the indicated time (`"metrics.count.absolute"`).
Since for each device at most one position can be found (due to the selection on Time), we are actually count the number of different devices that were in the area at the specified instant. 

### Example Response body

```json
{
	"items": [{
		"segment": null,
		"metrics": {
			"count": {
				"absolute": 2
			}
		} 
	}],
	"paging": {
		"next": null
	}
}
```
