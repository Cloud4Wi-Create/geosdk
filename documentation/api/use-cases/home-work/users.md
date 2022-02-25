# Find Users with Home/Work location in a given area

The set of Users that live or work in a given area can be obtained by requesting a Statistic on Home or Work locations.
(full documentation for [Home](/api/reference/endpoints/statistics/home-location.md) and [Work](/api/reference/endpoints/statistics/work-location.md) Statistics Endpoints)

* **Home Locations:** `POST https://api.geouniq.com/v1/statistics/homes`
* **Work Locations:** `POST https://api.geouniq.com/v1/statistics/works`

The body of the request has to contain a [Selection Operation](/api/concepts/resource-selection.md) on the [*Space*](/api/reference/dimensions/space.md) Dimension indicating the area of interest.

In addition, the body of the request has to contain a [Segmentation Operation](/api/concepts/statistics.md#segmentation-operation) on the [*Device Base*](/api/reference/dimensions/device-base.md) Dimension, which will indicate to divide the whole device base into sets of one device each.
Specifically, the [*DeviceBase-Segmentation*](/api/reference/data-models/d-segmentation/device-base.md) has to indicate the ["by device" criterion](api/dimensions/device-base.md#segmentation-criteria).

### Example Request body

```json
{
	"select": {
		"space": {
			"inside": {
				"explicitArea": {
					"type": "Feature",
					"geometry": null,
					"properties": {
						"circles":[{
							"center": {
								"lat": 10.0,
								"lng": 10.0
							},
							"radius": 100000
						}]
					}
				}
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

It is possible to limit the selection to the only "primary" Home/Work location of each device by adding a related Selection Operation, as in the example below.

```json
{
	"select": {
        "primary": {
    	    "inside": [true]
        }
	}
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

## Response

The Response provided by the API will contain a set of [*Items*](/api/reference/general-aspects/pagination.md) each of which refers to a specific device and indicates the number of resources (i.e., Home or Work locations, depending on what Resource the request refers to) found in that area for that device.

More in detail, the `"segment"` field refers to the resulting Segment, that in this case contains the ID of a specific device.
The `"metric"` field contains the count of resources found in the selected area for that device.
Note that, if no resource has been found for a specific device, then the related item will not be provided in the response.
Thus, whether a User lives/works in a given area is simply indicated by an item whose `"segment"` field contains the related Device ID.
To obtain the full list of devices with Home/Work location in the indicated area, it is necessary to obtain all the items by requesting successive pages (see [pagination](/api/reference/general-aspects/pagination.md))

```json
{
	"items": [{
		"segment": {
			"deviceBase": {
				"inside": {
				    "deviceId": ["D1"],
				    "deviceCustomId": ["myUserID"]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 1
			}
		}
	}],
	"paging": {
		"next": null
	}
}
```


