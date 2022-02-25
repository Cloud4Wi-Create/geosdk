# Obtain a spatial heatmap of Home/Work locations

The heatmap of Home or Work locations can be obtained through a request to the related [Statistic Endpoint](/api/reference/endpoints/statistics/index.md).  (full documentation for [Home](/api/reference/endpoints/statistics/home-location.md) and [Work](/api/reference/endpoints/statistics/work-location.md))

* **Home Locations:** `POST https://api.geouniq.com/v1/statistics/homes`
* **Work Locations:** `POST https://api.geouniq.com/v1/statistics/works`

The body of the request can contain a [Selection Operation](/api/concepts/resource-selection.md) on the [*Space*](/api/reference/dimensions/space.md) Dimension to indicate the area of interest.
If no Space selection is indicated, then the whole world is considered.

In addition, the body of the request has to contain a [Segmentation Operation](/api/concepts/statistics.md#segmentation-operation) on the [*Space*](/api/reference/dimensions/space.md) Dimension, which will indicate how to divide the area indicated through the Space Selection.
Specifically, the [*Space-Segmentation*](/api/reference/data-models/d-segmentation/space.md) has to indicate the ["by geohash" criterion](api/dimensions/space.md#segmentation-criteria) with a granularity at will.
The granulatiy indicates the lenght of the geohash prefix for the resulting sub-areas and should be choosen according to the extension of the selcted area.

The whole hearth surface is divided into 32^i sub-areas, whee *i* is the lenght of the geohash. 
Each sub-area will be a recatangular cell whose extension changes according to the geohash lenght (see [here](/api/reference/dimensions/space.md#resulting-sub-areas))

### Example Request body

The following example allows to obtain an heatmap of the whole world (no space selection) which will be divide into about 32000 sub-areas (32^3)

```json
{
	"segmentBy": {
		"space": {
			"inside": {
				"geohash": 3
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

The example below selects a circular area with radius equal to 100 Km.
The whole area will be divided into sub-areas with geohash of lenght 5. 


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
		"space": {
			"inside": {
				"geohash": 5
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

It is possible to limit the selection to the sole "primary" Home/Work location of each device by adding a related Selection Operation, as in the example below.
This way, at most one Home/Work location will be counted for each device

```json
{
	"select": {
        "primary": {
    	    "inside": [true]
        }
	}
	"segmentBy": {
		"space": {
			"inside": {
				"geohash": 3
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

## Response

The Response provided by the API will contain a set of [*Items*](/api/reference/general-aspects/pagination.md) each of which refers to a specific sub-area and indicates the number of resources (i.e., Home or Work locations, depending on what Resource the request refers to) found in that area.

More in detail, the `"segment"` field refers to the resulting Segment, that in this case contains the indication of the sub-area.
The area is indicated through a [`GuGeoJSON`](/api/reference/data-models/common/gu-geo-json.md) object which contains both the geohash of the area and the coordinates of the resulting polyghon.
In addition, also the bounding-box is provided.
The `"metric"` field contains the count of resources found in the sub-area

```json
{
	"items": [{
		"segment": {
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
				    				[-10.0, 10.0],
				    				[-10.0, -10.0]
				    			]
				    		]
				        },
				        "properties" : {
				            "geohashes": ["sxdbc"]
				        }
				    }
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 100
			}
		}
	}],
	"paging": {
		"next": null
	}
}
```