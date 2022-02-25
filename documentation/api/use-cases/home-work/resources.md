# Retrieving the Home/Work Locations of one or more specific device

The Home or Work location of a specific set of device can be obtained through a simple request to the related [Resource Endpoint](/api/reference/endpoints/resources/index.md).  (full documentation for [Home](/api/reference/endpoints/resources/platform-created/device-related/home-location.md) and [Work](/api/reference/endpoints/resources/platform-created/device-related/work-location.md))

* **Home Locations:** `POST https://api.geouniq.com/v1/selections/homes`
* **Work Locations:** `POST https://api.geouniq.com/v1/selections/works`

The body of the request has to contain a [Selection Operation](/api/concepts/resource-selection.md) on the [*Device Base*](/api/reference/dimensions/device-base.md) Dimension.
Specifically, the [*DeviceBase-Segment*](/api/reference/data-models/d-segment/device-base.md) has to contain the set of IDs of the Devices of interest (e.g., `"<D1>"`, `"<D2>"`, etc.).

### Example Request body

```json
{
	"deviceBase": {
		"inside": {
			"deviceId": ["<D1>", "<D2>",  "<D3>"]
		}
	}
}
```

It is possible to limit the selection to the only "primary" Home/Work location of each device by adding a related Selection Operation.

```json
{
	"deviceBase": {
		"inside": {
			"deviceId": ["<D1>", "<D2>",  "<D3>"]
		}
	},
	"primary": {
	    "inside": [true]
	}
}
```

## Response
The Response provided by the API will contain a set of [*Items*](/api/reference/general-aspects/pagination.md) each of which represents a Home/Work Location Resource (same [data model](/api/reference/data-models/resources/platform-created/device-related/home-location.md)).

### Example Response body

```json
{
	"items": [    {
        "device": {
            "id": "D1"
        },
        "primary": true,
        "geo": {
            "Lat": 42.16
            "Lng": 12.78
        }
    },{
        "device": {
            "id": "D2"
        },
        "primary": true,
        "geo": {
            "Lat": 43.14
            "Lng": 13.12
        }
    },
    {
        "device": {
            "id": "D2"
        },
        "primary": false,
        "geo": {
            "Lat": 44.16
            "Lng": 13.78
        }
    }],
	"paging": {
		"next": null
	}
}
```

Each returned Item contains the ID of the device which the Home/Work location refers to, the geographical coordinates of the location, and a boolean flag indicating whether this is the primary Home/Work location for that device.
In the example above, we received one location for Device *D1*, two locations for Device *D2*, whilst no one for Device *D3*

Similarly to the example above, it is possible to obtain the whole set of Home/Work Locations by simply removing the selection condition on the *Device Base* (empty json object `{}`) or, for a specific [Client App](/service-architecture.md#service-architecture), with the following selection condition

```json
{
	"deviceBase": {
		"inside": {
			"clientAppId": ["<A1>", "<A2>"]
		}
	}
}
```