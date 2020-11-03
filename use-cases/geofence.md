# Geofences

Geofences can be set by creating specific [*Trigger*](/api/resources/user-created/trigger.md) Resources.

To create a generic *Trigger*, follow the [related guide](/guide/triggers.md).

Here, we consider that a geofence has to monitor when a single device enters or leave a specific area.
This means that the event defined by the *Trigger* involves one single device at time and thus the Tragets of the *Trigger* have to be set as documented [here](/guide/triggers.md#events-that-involve-only-one-device).

In the following, we mainly focus on the following different kinds of geofecnes and how they are mapped on the `"eventDefinition"` field of the *Trigger*.

* [Enters geofence](#enters-geofence): trigger as soon as the device enters the area
* [Enters and dwells geofence](#enters-and-dwells-geofence): trigger when the device has been in the area for a specified amount of time
* [Exits geofence](#leaves-geofence): trigger as soon as the device leaves the area

## Enters geofence

An "enters" geofence can be mapped into the condition "The number of *Detected Positions* inside the area of interest in any given moment is higher than zero".
Such a condition becomes true as soon as a the device sends a position update within the area of interest.
The *Trigger* will trigger in that moment and will not trigger anymore until the device sends a position update outside the area and inside again.

The JSON object that has to be associated with the `"eventDefinition"` field must be as it follows.


```json
{
	"nodeType": "detectedPosition",
	"detectedPosition": {
		"select": {
			"space": {
				"inside": {
					"explicitArea": {
						"type": "Feature",
						"geometry": null,
						"properties": {
							"circles": [{
								"center": {
									"lat": 10.0,
									"lng": 10.0
								},
								"radius": 100
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
		"evaluate": {
			"count": {
				"gt": 0
			}
		}
	}
}
```

> Note that, the area of interest is a circle indicated through a [`GuGeoJson`](/api/data-models/d-segment/space.md) Object. Change the coordinates and radius according to your needs

The following request allows to set an "enters" geofence [for each device of the device-base](/guide/triggers.md#the-event-has-to-be-monitored-for-each-device-of-the-device-base).

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"example geofence","targets":{"select":null,"segmentBy":{"device":1}},"status":{"enebled":false},"eventDefinition":{"nodeType":"detectedPosition","detectedPosition":{"select":{"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}},"time":{"intersect":{"intervals":[{"from":{"relative":0},"to":{"relative":0}}]}}},"evaluate":{"count":{"gt":0}}}}}'
```

> **Note that the *Trigger* is disabled (`"status":{"enebled":false}`).**

## Leaves geofence

A "exits" geofence can be mapped into the condition "The number of *Detected Positions* inside the area of interest in any given moment is equal to zero".
Such a condition becomes true as soon as a the device sends a position update outside the area of interest.
The *Trigger* will trigger in that moment and will not trigger anymore until the device sends a position update inside the area and outside again.

The JSON object that has to be associated with the `"eventDefinition"` field must be as it follows.


```json
{
	"nodeType": "detectedPosition",
	"detectedPosition": {
		"select": {
			"space": {
				"inside": {
					"explicitArea": {
						"type": "Feature",
						"geometry": null,
						"properties": {
							"circles": [{
								"center": {
									"lat": 10.0,
									"lng": 10.0
								},
								"radius": 100
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
		"evaluate": {
			"count": {
				"eq": 0
			}
		}
	}
}
```

> Note that, the area of interest is a circle indicated through a [`GuGeoJson`](/api/data-models/d-segment/space.md) Object. Change the coordinates and radius according to your needs

The following request allows to set an "exits" geofence [for each device of the device-base](/guide/triggers.md#the-event-has-to-be-monitored-for-each-device-of-the-device-base).


```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"example geofence","targets":{"select":null,"segmentBy":{"device":1}},"status":{"enebled":false},"eventDefinition":{"nodeType":"detectedPosition","detectedPosition":{"select":{"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}},"time":{"intersect":{"intervals":[{"from":{"relative":0},"to":{"relative":0}}]}}},"evaluate":{"count":{"eq":0}}}}}'
```

> **Note that the *Trigger* is disabled (`"status":{"enebled":false}`).**


## Enters and dwells geofence

An "enters and dwells" geofence can be mapped into the condition "The number of *Visits* of duration higher than *T* inside the area of interest in any given moment is higher than zero".

The JSON object that has to be associated with the `"eventDefinition"` field must be as it follows, where the specific amount of time *T* has to be indicated in the field `"visit.select.duration.gte"`.

```json
{
    "nodeType": "visit",
    "visit" : {
        "select": {
            "spatialGranularity": {
               "inside": ["exactFit"]
            },
            "space" : {
                "inside": {
					"explicitArea": {
						"type": "Feature",
						"geometry": null,
						"properties": {
							"circles": [{
								"center": {
									"lat": 10.0,
									"lng": 10.0
								},
								"radius": 100
							}]
						}
					}
                }
            },
            "time": {
                "intersect": {
                    "intervals": [{"from": {"relative":0}, "to": {"relative": 0}}]
                }
            },
            "duration": {
                "gte" : 600
            }
        },
        "evaluate": {
            "count": {"gt" : 0}
        }
    }
}
```

> Note that, the area of interest is a circle indicated through a [`GuGeoJson`](/api/data-models/d-segment/space.md) Object while the dwelling time is indicated by `"visit.select.duration.gte"` field. 
You should change the coordinates and radius of the circle and the dwelling time according to your needs.

The following request allows to set an "enters and dwells" geofence [for each device of the device-base](/guide/triggers.md#the-event-has-to-be-monitored-for-each-device-of-the-device-base).

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"example geofence","targets":{"select":null,"segmentBy":{"device":1}},"status":{"enebled":false},"eventDefinition":{"nodeType":"visit","visit":{"select":{"spatialGranularity":{"inside":["exactFit"]},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}},"time":{"intersect":{"intervals":[{"from":{"relative":0},"to":{"relative":0}}]}},"duration":{"gte":600}},"evaluate":{"count":{"gt":0}}}}}'
```

> **Note that the *Trigger* is disabled (`"status":{"enebled":false}`).**

