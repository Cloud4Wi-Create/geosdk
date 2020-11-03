# Trigger

Data Model used to represent a [*Trigger*](/api/resources/user-created/trigger.md) Resource.

## Fileds Specification


Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
id    | `String` | Forbidden - Output Only |N.A. | The Resource ID.
createdAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name    | `String` | Optional | ANY `String` with length lower than 32 characters| A name for the *Trigger*. Can be used to select *Triggers* and *Trigger Logs*.
description    | `String` | Optional | ANY `String` with length lower than 128 characters| A description of the *Trigger*. Useful for visualization only.
labels  | `[String]` | Optional | At most 10 elements. Each element lower than 16 characters | A set of labels that can be associated to the *Trigger*. Can be used to select *Triggers* and *Trigger Logs*.
activeOn |[`Time-Segment`](/api/data-models/d-segment/time.md) | Optional |ANY valid `Time-Segment` object or `null` | Indicates when the *Trigger* has to be activated/de-activated. If not provided, or set to `null`, it means that the *Trigger* must be always active regardeless of the date and time.
status.enabled | `Boolean` | Optional | ANY | Indicates whether the *Trigger* is currently enabled or not. If not provided, it will be set to `false`. The value of this field can be changed to activate/deactivate the *Trigger*. When set to `false` the *Trigger* will not be active even if it should according to `"activeOn"`. If set to `true`,  the *Trigger* will be active only if it should according to `"activeOn"`.
status.active | `Boolean` | Forbidden - Output Only | ANY `Boolean` | Indicates whether the *Trigger* is currently active or not according to both the automatic activation/deactivation indicated in `"activeOn"` and the value of the `"status.enabled"` flag.
targets |`JSON` | Mandatory | N.A. | Indicates the [Targets of the *Trigger*](/api/concepts/triggers.md). If not provided or set to `null`, it is equivalent to set all its fields to `null`. In this case, each *Condition* indicated in `"eventDefinition"` will be evaluated considering the whole device-base.
targets.select |[`DeviceBase-Segment`](/api/data-models/d-segment/device-base.md) | Optional | ANY valid `DeviceBase-Segment` object or `null` | Indicates a selection of devices, i.e., a *DeviceBase-Segment*, which the *Trigger* refers to. If set to `null` or not provided, it indicates the whole device-base.
targets.segmentBy |[`DeviceBase-Segmentation`](/api/data-models/d-segmentation/device-base.md) |Optional | ANY valid `DeviceBase-Segmentation` object or `null` | Allows to set the same *Trigger* for several Targets, each of which correspond to a *DeviceBase-Segment*. The field indicates how to divide the main *Device Base* Segment indicated in `"targets.selection"` in several Segments. The event defined in `"eventDefinition"` will be monitored for each *Device Base* Segment resulting from the Segmentatoin indicated by this field. If not provided or set to `null`, the Trigger will have only one Target corresponding to the *Device Base* Segment indicated in `"targets.select"`.
eventDefinition |[`ConditionsTreeNode`](/api/data-models/common/conditions-tree-node.md) | Mandatory | ANY valid `ConditionsTreeNode` object | Defines the event to be monitored through a [*Conditions Tree*](/api/concepts/triggers.md).
hooks |`[String]` | Optional | ANY combination of valid [*Hook*](/api/resources/user-created/hook.md) IDs | The set of *Hook* Resources linked to the *Trigger*. Each of them specifies an action to perform when the event defined by the *Trigger* occurs.

```json
{
	"id": "trigger1",
	"createdAt": "2017-01-01T00:00:00Z",
	"name": "My First Trigger",
	"description": "A simple geofence for Conad Roma 1. Active only during work hours. Inactive during the weekend. Set for each Android device",
	"labels": ["geofence", "conad", "roma1", "android"],
	"status": {
        "enabled": true,
        "active": true
    },
	"activeOn": {
        "intervals": [{
            "from": {
                "absolute": "2017-01-31T00:00:00Z"
           },
           "to": null
        }],
        "periodicity": {
            "hoursOfTheDay": [10,11,12,13,14,15,16,17,18,19,20],
            "daysOfTheWeek": ["monday", "tuesday", "wednesday", "thursday", "friday"]
        }
    },
	"targets": {
        "select": {
            "osName": ["Android"]
        },
        "segmentBy": {
            "device" : 1
        }
    },
    "hooks": ["hook1"],
	"eventDefinition": {
	    "nodeType": "visit",
        "visit" : {
            "select": {
                "spatialGranularity": {
                   "inside": ["bestFit"]
                },
                "space" : {
                    "inside": {
	                    "savedAreas": {
	                        "name": ["Conad Roma Est"]
	                    }
                    }
                },
                "time": {
                    "intersect": {
                        "intervals": [{"from": {"relative":0}, "to": {"relative": 0}}]
                    }
                },
                "duration": {
                    "gte" : 60
                }
            },
            "evaluate": {
                "count": {"gt" : 0}
            }
        }
	}
}
```
