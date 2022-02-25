# Campaign

Data Model used to represent a [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) Resource.

## Fields Specificcation

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
id | `String` | Forbidden - Output Only | N.A. | The Resource ID.
createdAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name | `String` | Optional | Any `String` of length lower than 32 characters | A name for the *Campaign*
description | `String` | Optional | Any `String` of length lower than 128 characters | A description for the *Campaign*
labels | `[String]` | Optional | At most 10 `String` elements of length lower than 16 characters | A set of labels associated to the *Campaign*
realTimeMonitoring | `JSON` | Optional | Any valid object according to the fields `realTimeMonitoring.X` described in the following | A JSON object related to the real-time monitoring functionality
realTimeMonitoring.status | `String` | Mandatory if the main object is provided | {`"enabled"`;`"disabled"`} | Indicates whether the real-time monitoring functionality has to be anabled or not for the campaign
period | `JSON` | Mandatory | Any valid object according to the fields `period.X` described in the following | A JSON object indicating the period of the campaign
period.start | [`Date`](/api/reference/data-modelsata-models/common/date.md) | Mandatory | Any valid [`Date`](/api/reference/data-modelsata-models/common/date.md) | Indicates the start date and time of the campaign
period.end | [`Date`](/api/reference/data-modelsata-models/common/date.md) | Mandatory | Any valid [`Date`](/api/reference/data-modelsata-models/common/date.md) | Indicates the end date and time of the campaign
targetPOIs | [`TargetPOIs`](/api/reference/data-models/target-pois) | Mandatory | Only one [`TargetPOIs`](/api/reference/data-models/target-pois) object currently supported | A set of  [`TargetPOIs`](#target-pois) objects indicating the target POIs
targetAudience | [`Audience`](/api/reference/data-modelsata-models/common/audience.md) | Optional | Only one  [`Audience`](/api/reference/data-modelsata-models/common/audience.md) object currently supported | A set of  [`Audience`](/api/reference/data-modelsata-models/common/audience.md) objects indicating the target audience of the campaign
identifyExposed | [`Visit-Segment`](/api/reference/data-modelsata-models/r-segment/visit.md) | Mandatory if `"type"` is `"outOfHome"`. Forbidden otherwise | Any valid [`Visit-Segment`](/api/reference/data-modelsata-models/r-segment/visit.md) | Indicates how to identifies users exposed to the advertising for OOH campaigns
visitsHook | [`Hook`](/api/reference/data-modelsata-models/common/hook.md) | Optional | Any valid [`Hook`](/api/reference/data-modelsata-models/common/hook.md) | An hook to deliver informations about the identified visits to the target POIs when real-time monitoring is enabled
exposedHook | [`Hook`](/api/reference/data-modelsata-models/common/hook.md) | Optional | Any valid [`Hook`](/api/reference/data-modelsata-models/common/hook.md) | An hook to deliver informations about the identified exposed users for OOH campaigns


## Example Object

```json
{
  "id": "campaign1",
  "name": "my campaign",
  "description": "my first campaign",
  "type": "outOfHome",
  "realTimeMonitoring": {
    "status": "enabled"
  },
  "period": {
    "start": "2020-05-01T00:00:00Z",
    "end": "2020-05-10T00:00:00Z"
  },
  "targetPOIs": [
    {
      "custom": {
        "type": "FeatureCollection",
        "features": [
          {
            "type": "Feature",
            "properties": {
              "id": "Place 1",
              "circles": [
                {
                  "center": {
                    "lat": 10.0,
                    "lng": 10.0
                  },
                  "radius": 15
                }
              ]
            },
            "geometry": null
          }
        ]
      },
      "standard": {
        "category": [
          "category1"
        ],
        "brand": [
          "brand1"
        ],
        "administrativeArea": [
          {
            "conutry": "IT",
            "area": {
              "level": "Regione",
              "name": [
                "Campania",
                "Basilicata"
              ]
            }
          }
        ]
      }
    }
  ],
  "identifyExposed": {
    "time": {
      "inside": {
        "intervals": [
          {
            "from": {
              "absolute": "2020-05-01T00:00:00Z"
            },
            "to": {
              "absolute": "2020-05-10T00:00:00Z"
            }
          }
        ]
      }
    },
    "space": {
      "inside": {
        "explicitArea": {
          "type": "FeatureCollection",
          "features": [
            {
              "type": "Feature",
              "properties": {
                "id": "Place 1"
              },
              "geometry": {
                "type": "Polygon",
                "coordinates": [
                  [
                    [
                      100.0,
                      0.0
                    ],
                    [
                      101.0,
                      0.0
                    ],
                    [
                      101.0,
                      1.0
                    ],
                    [
                      100.0,
                      1.0
                    ],
                    [
                      100.0,
                      0.0
                    ]
                  ]
                ]
              }
            },
            {
              "type": "Feature",
              "properties": {
                "id": "Place 2"
              },
              "geometry": {
                "type": "Polygon",
                "coordinates": [
                  [
                    [
                      100.0,
                      1.0
                    ],
                    [
                      101.0,
                      1.0
                    ],
                    [
                      101.0,
                      2.0
                    ],
                    [
                      100.0,
                      2.0
                    ],
                    [
                      100.0,
                      1.0
                    ]
                  ]
                ]
              }
            }
          ]
        }
      }
    },
    "spatialGranularity": {
      "inside": [
        "exact"
      ]
    }
  },
  "visitsHook": {
    "type": "web",
    "web": {
      "url": "https://mydomain.com/gu-hooks/visits"
    }
  },
  "exposedHook": {
    "type": "web",
    "web": {
      "url": "https://mydomain.com/gu-hooks/exposed"
    }
  }
}
```