* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Look at the trend of device registrations

By requesting a [Statistic](/api/concepts/statistics.md) on [*Device*](/api/reference/resources/platform-created/device.md) Resources it is possible to understand the trend of new device registrations globally for a [*Project*](/service-architecture.md) or for a specific [*Client App*](/service-architecture.md).
Specifically, this Statistic allows to obtain the number of new device registrations during a specific period of time.
Moreover, it is possible to [segment the Statistic](/api/concepts/statistics.md#segmentation) on the [*Time*](/api/reference/dimensions/time.md) Dimension in order to see the number of new registration each (for example) day.


A Statistic on *Device* Resources can be obtained through the following endpoint (full documentation [here](/api/reference/endpoints/statistics/device.md))

`POST https://api.geouniq.com/v1/statistics/devices`

The Body of the Request can vary according to the desired selection and segmentation.
The example below shows the body to obtain the number of new device registrations for each operating system and each day during a specific period of time.

```json
{
	"select": {
		"time": {
			"inside": {
				"intervals": [{
					"from": {
						"absolute": "2017-07-01T00:00:00Z"
					},
					"to": {
						"absolute": "2017-08-01T00:00:00Z"
					}
				}]
			}
		}
	},
	"segmentBy": {
		"deviceBase": {
			"inside": {
				"osName": 1
			}
		},
		"time": {
			"inside": {
				"continuousInterval": {
					"count": 1,
					"unit": "day"
				}
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

It can be noted that the body above restricts the Statistic in time to July 2017 (`"select.time"` filed).
In addition, two different [Segmentations](/api/concepts/statistics.md#segmentation) are requested.

1. **[*Device Base*](/api/reference/dimensions/device-base.md) dimension using the [*By Os Name*](/api/reference/dimensions/device-base.md#by-os-name) criterion**: allows to distinguish between registrations of devices with a different operating system (if you have multiple Client Apps for the same mobile platform configured for your Project, you might want to use the [*By Client App*](/api/reference/dimensions/device-base.md#by-client-app) criterion instead)
2. **[*Time*](/api/reference/dimensions/time.md) dimension using the [*Continuous Interval*](/api/reference/dimensions/time.md#continuous-interval) criterion and granularuty "1 Day"**: allows to divide the whole selected period (July 2017 in the example) into sub-periods of 24 hours each 

When a similar request is performed, the Response provided by the API will look like the following.

```json
{
	"items": [{
		"segment": {
			"deviceBase": {
				"inside": {
					"osName": ["android"]
				}
			},
			"time": {
				"inside": {
					"intervals": [{
						"from": {
							"absolute": "2017-07-01T00:00:00Z"
						},
						"to": {
							"absolute": "2017-07-02T00:00:00Z"
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
	},
	{
		"segment": {
			"deviceBase": {
				"inside": {
					"osName": ["android"]
				}
			},
			"time": {
				"inside": {
					"intervals": [{
						"from": {
							"absolute": "2017-07-02T00:00:00Z"
						},
						"to": {
							"absolute": "2017-07-03T00:00:00Z"
						}
					}]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 300
			}
		}
	},
	...
	,
	{
		"segment": {
			"deviceBase": {
				"inside": {
					"osName": ["ios"]
				}
			},
			"time": {
				"inside": {
					"intervals": [{
						"from": {
							"absolute": "2017-07-01T00:00:00Z"
						},
						"to": {
							"absolute": "2017-07-02T00:00:00Z"
						}
					}]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 197
			}
		}
	}],
	"paging": {
		"next": {
			"link": "https://api.geouniq.com/v1/statistics/devices?offset=MTAw&limit=100",
			"offset": "MTAw"
		}
	}
}
```

Each *Item* refers to a specific Operating System and a specific sub-period (`"segment.deviceBase.inside.osName"` and `"segment.time.inside.intervals"`), and provides the number of new devices registrations (`"metrics.count.absolute"`).

Note that the Request above does not provide the total number of devices but only how many devices registered each day.

If you want to obtain the total number, you could perform a single request to obtain the total number of devices registered until the beginning of your period of interest (July the 1-st in our example) and then sum the number of new registrations obtained through the request shown above.

The body of this new Request shoud be like the following

```json
{
	"select": {
		"time": {
			"inside": {
				"intervals": [{
					"to": {
						"absolute": "2017-07-01T00:00:00Z"
					}
				}]
			}
		}
	},
	"segmentBy": {
		"deviceBase": {
			"inside": {
				"osName": 1
			}
		}
	},
	"compute": {
		"count": true
	}
}
```

It can be noted that, in this case, only the end of the period of interest is indicated, which means "until that moment".
In addition, no segmentation on the *Time* Dimension is requested as we are interested in the total number of *Device* Resources that were registered on the platform "in that moment".
On the contrary, the same segmentation is kept for the *Device Base* Dimension in order to distinguish between Android and iOS devices.


In this case, the response of the API will look like the following.

```json
{
	"items": [{
		"segment": {
			"deviceBase": {
				"inside": {
					"osName": ["android"]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 2567
			}
		}
	},
	{
		"segment": {
			"deviceBase": {
				"inside": {
					"osName": ["ios"]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 1978
			}
		}
	}],
	"paging": {
		"next": null
	}
}
```

Each *Item* refers to a specific operating system (`"segment.deviceBase.inside.osName"`) and the whole selected period of time (no field `"segment.time"`)


