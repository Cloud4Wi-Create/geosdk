* [Documentation Home](../../../README.md)
   * [Web API](../../index.md)
      * [Use Cases](../index.md)

# Triggers

This section provides examples explaining how to create and use Triggers.
See [here](../../overview.md#triggers) for an overview of the functionality.

## Reference Documentation

* [Trigger Resource](../../reference/resources/user-created/trigger.md)
* [Trigger Endpoints](../../reference/endpoints/resources/user-created/trigger/index.md)
* [TriggerLog Resource](../../reference/resources/platform-created/triggerlog.md)
* [TriggerLog Selection Endpoints](../../reference/endpoints/resources/platform-created/triggerlog.md)

## Main steps
Triggers allow to define an event to be monitored for devices and to get notified when they occur.
The type of Trigger indicates the type of event to be monitored.

> Currently, only geofence triggers are available.

The first step is to create a Trigger resource, like in the example below

```
  curl --request POST \
    --url https://api.geouniq.com/v1/triggers \
    --header 'authorization: Bearer <ACCESS_TOKEN>' \
    --header 'content-type: application/json' \
    --data '{"name":"My Trigger","description":"My first Trigger","labels":["test"],"hooks":[{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/triggers"}}],"period":{"intervals":[{"from":"2021-01-01T00:00:00Z","to":"2021-02-01T00:00:00Z"}]},"event":{"type":"geofence","geofence":{"transitions":[{"type":0,"enabled":true},{"type":1,"enabled":true}],"area":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10,"lng":10},"radius":100}]}}}}}'
  ```
  
Once a Trigger has been created, the platform will monitor the related event until the Trigger is valid.
When an event is detected for a device, the platform:

* Creates a [Trigger Log](../../reference/resources/platform-created/triggerlog.md) resource that indicates the details of the event, that is the Trigger it relates to, 
the involved device, the time when the event occurred, and other details that can depend on the specific event type.

* Processes the [Hook](../../reference/data-models/common/hook.md) associated with the Trigger if any has been provided

Trigger Log resources can be accessed through the [related endpoints](../../reference/endpoints/resources/platform-created/triggerlog.md).

Hooks can be used to receive a notification when the platform detects a trigger event.
In particular, [Web Hooks](../../reference/data-models/common/hook.md#webhook) can be used to receive a notification via an
HTTP request on a URL of your choice. 
See [here](../receiving-web-hooks.md) to learn how to receive Web Hooks. 

## Example of Geofence Triggers

The following example shows the body to request a geofence trigger.
The `"period"` field carries a [`Time-Segment`](../../reference/data-models/d-segment/time.md) 
object indicating the validity period of the Trigger.

The `"event"` field carries the details of the event to be monitored, 
that is a geofence, whilst the field `"geofence"` field carries the details of the geofence.  
The geofence indicates an area, through a [GuGeoJSON](../../reference/data-models/common/gu-geo-json.md) 
object, and a set of transitions that have to be monitored.  
Two different transitions are defined, namely `"enter"` and `"exit"`.


```json
{
	"name": "My Trigger",
	"description": "My first Trigger",
	"labels": ["test"],
	"hooks": [{
		"type": "web",
		"web": {
			"url": "https://mydomain.com/gu-hooks/triggers"
		}
	}],
	"period": {
		"intervals": [{
			"from": "2021-01-01T00:00:00Z",
			"to": "2021-02-01T00:00:00Z"
		}]
	},
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
			}
		}
	}
}
```



