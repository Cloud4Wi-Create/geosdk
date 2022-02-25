# Trigger

Data Model used to represent a [*Trigger*](../../../resources/user-created/trigger.md) Resource.

## Fields Specification

The `Trigger` data model contains all the fields common to any [user-created resource data model](../user-created/index.md).

In addition, the following fields are contained by a `Trigger` data model

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
status | `String` | Mandatory | `{"enabled", "disabled"}` | Indicates whether the trigger is enabled (active) or not.
period | [`Time-Segment`](../../d-segment/time.md) | Optional | Any valid [`Time-Segment`](../../d-segment/time.md) | If provided, indicates when the trigger must be active. If not provided, the Trigger will always be active.
event | [`TriggerEvent`](#triggerevent) | Mandatory| Any valid [`TriggerEvent`](#triggerevent) | Indicates the specific event that has o be monitored 
target | [`DeviceBase-Segment`](../../d-segment/device-base.md) | Mandatory | Any valid [`DeviceBase-Segment`](../../d-segment/device-base.md) | Indicates the devices which the trigger refers to.
hooks | [`[Hook]`](../../common/hook.md)| Optional | Any array of valid [`Hook`](../../common/hook.md) objects | a set of [Hook](../../common/hook.md) that will be used to send notifications related to trigger events through the related [Trigger Logs](../../../resources/platform-created/triggerlog.md)   


## TriggerEvent

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
type | `String` | Mandatory | `{"geofence", "homeLocationgeofence", "workLocationgeofence"}` | Indicates the type of event to be monitored 
geofence |[`Geofence`](#geofence)| Mandatory if `"type"` equals `"geofence"`. Forbidden otherwise. | Any valid [`Geofence`](#geofence) | Indicates the details of the geofence.
homeLocationGeofence |[`LOIGeofence`](#LOIgeofence)| Mandatory if `"type"` equals `"homeLocationgeofence"`. Forbidden otherwise. | Any valid [`LOIGeofence`](#LOIgeofence) | Indicates the details of the home-location geofence.
workLocationGeofence |[`LOIGeofence`](#LOIgeofence)| Mandatory if `"type"` equals `"workLocationgeofence"`. Forbidden otherwise. | Any valid [`LOIGeofence`](#LOIgeofence) | Indicates the details of the work-location geofence.

## Geofence

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
area | [`GuGeoJson`](../../common/gu-geo-json.md) | Mandatory | any valid [`GuGeoJson`](../../common/gu-geo-json.md) object | Indicates the area of the geofence 
transitions |[`[Transition]`](#transition)| Optional | Any valid transition |Indicates the type of transitions that have to be monitored.
dwellTime |`Number`| Optional. | ANY integer positive number | Indicates for how long (in seconds) the device must remain iside/outside the geofence.

## LOIgeofence

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
radius | `Number` | Mandatory | Any number in the range `[25,1000000]`
transitions |[`[Transition]`](#transition)| Optional | Any valid transition |Indicates the type of transitions that have to be monitored.
dwellTime |`Number`| Optional. | ANY integer positive number | Indicates for how long (in seconds) the device must remain iside/outside the geofence.

## Transition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
type | `String` | Mandatory | `{"enter","exit"}`| Indicates the type of transition.  
enabled |`Boolean`| Mandatory. | Indicates whether the transition is enabled or not. providing `false` is equivalent to not providing the `Transition` object


## Example Object

```json
{
	"id":"T1",
	"createdAt":"2021-01-01T00:00:00Z",
	"updatedAt":"2021-01-01T00:00:00Z",
	"name": "My Trigger",
	"description": "My first Trigger",
	"labels": ["test"],
	"status":"enabled",
	"period": {
		"intervals": [{
			"from": {
				"absolute":"2021-01-01T00:00:00Z"
			},
			"to": {
				"absolute":"2021-02-01T00:00:00Z"
			}
		}]
	},
	"target":{
		"clientAppId":["A1", "A2"]
	},
	"hooks": [{
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/triggers"
		}
	}],
	"event": {
		"type": "geofence",
		"geofence": {
			"transitions": [{
				"type": "enter",
				"enabled": true
			}, {
				"type": "exit",
				"enabled": true
			}],
			"area": {
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
			},
			"dwellTime": 300
		}
	}
}
````

