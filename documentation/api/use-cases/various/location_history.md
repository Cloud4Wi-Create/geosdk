* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Get the location history of a device

The location history of a device (i.e. the set of [Detected Positions](/api/reference/resources/platform-created/device-related/position.md) of that device in a given time interval) 
can be obtained through a request at the following endpoint ([full doc here](/api/reference/endpoints/resources/platform-created/device-related/detected-position.md)):

`POST https://api.geouniq.com/v1/selections/detected-positions` 

The body of the request has to contain a [Selection Operation](/api/concepts/resource-selection.md) on the [*Device Base*](/api/reference/dimensions/device-base.md) Dimension (`"deviceBase.inside"`).
Specifically, the [*Device Base Segment*](/api/reference/data-models/d-segment/device-base.md) has to indicate the [Device ID](/service-architecture.md#device-registration-device-ids-and-device-base) of interest.

> Note that it's also possible to provide more than one Device ID at time

Optionally, it's possible to restrict the selection to a specific time interval by providing a [Selection Operation](/api/concepts/resource-selection.md) on the [*Time*](/api/reference/dimensions/time.md) Dimension (`"time.start"`).

## Example Request body

> Time expressed through the relative fields: from 86400 seconds ago up to 0 seconds ago

```json
{
	"deviceBase": {
		"inside": {
			"deviceId": ["D1"]
		}
	},
	"time": {
		"start": {
			"intervals": [{
			    "from": {
			        "relative": -86400
			    },
			    "to": {
			        "relative": 0
			    }
			}]
		}
	}
}
```

> Time expressed through the absolute fields: from 1st Jan 2018 to 2nd Jan 2018

```json
{
	"deviceBase": {
		"inside": {
			"deviceId": ["D1"]
		}
	},
	"time": {
		"start": {
			"intervals": [{
			    "from": {
			        "absolute": "2018-01-01T00:00:00Z"
			    },
			    "to": {
			        "absolute": "2018-01-02T00:00:00Z"
			    }
			}]
		}
	}
}
```

The Response provided by the API will contain a set of [*Items*](/api/reference/general-aspects/pagination.md) each of which represent a [Detected Positions](/api/reference/resources/platform-created/device-related/position.md) reosurce related to the specific device.


### Example Response body

```json
{
    "items": [
        {
            "device": {
                "id": "D1"
            },
            "detectedAt": "2018-01-01T16:23:34Z",
            "geo": {
                "Lat": 50.445718,
                "Lng": -3.560455
            },
            "speed": 3.2
        },
        {
            "device": {
                "id": "D1"
            },
            "detectedAt": "2018-01-01T16:23:59Z",
            "geo": {
                "Lat": 50.446893,
                "Lng": -3.559082
            },
            "speed": 3.2
        },
        {
            "device": {
                "id": "D1"
            },
            "detectedAt": "2018-01-01T16:25:34Z",
              "geo": {
                "Lat": 50.447725,
                "Lng": -3.55773
            },
            "speed": 2.3
        }
    ],
    "paging": {
        "next": {
            "link": "https://api.geouniq.com/v1/selections/detected-positions?limit=3&offset=Mw%3D%3D",
            "offset": "Mw=="
        }
    }
}
```