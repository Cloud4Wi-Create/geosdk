* [Documentation Home](../../../../README.md)
    * [Web API](../../../index.md)
        * [Reference](../../index.md)
            * [Data Models](../index.md)
                * [Common Data Models](index.md)

# HookEvent

Data model used to represent an event occurred on the platform 
that has to be notified through a [Hook](hook.md).

Name | Type | Possible Values | Description 
--------|--------|--------|--------
eventType | `String` | {`"resourcesCreated"`;`"resourcesUpdated"`} | Indicates the type of event
resourcesCreated | [`ResourceEvent`](#resourceevent)| ANY valid [`ResourceEvent`](#resourceevent) | Carries the details of the created resources
resourcesUpdated | [`ResourceEvent`](#resourceevent)| ANY valid [`ResourceEvent`](#resourceevent) | Carries the details of the updated resources

## ResourceEvent

Name | Type | Possible Values | Description 
--------|--------|--------|--------
resourceType | `String` | The name of any [resource](../../resources/index.md) defined for this API | indicates the type of resource involved in the event 
Xs | [`JSON`]| An array of ANY valid resource data model according to the resourceType indicated | The set of resources involved in the event

> Example `HookEvent` in case of [TriggerLog](../../resources/platform-created/triggerlog.md) resources 
>created as consequence of a trigger event.

````json
{
	"eventType": "resourcesCreated",
	"resourcesCreated": {
		"resourceType": "triggerLog",
		"triggerLogs": [{
			"trigger": "5964b7d5d5f455000133fe3e",
			"device": {
				"id": "device1",
				"clientAppId": "app1",
				"customId": "my device",
				"idfa": "550e8400-e29b-41d4-a716-446655440000"
			},
			"event": {
				"type": "geofence",
				"geofence": {
					"type": "enter",
					"time": "2021-01-01T00:00:00Z"
				}
			}
		}]
	}
}
````
