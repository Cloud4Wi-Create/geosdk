# Triggerlog

Data Model used to represent a [*Triggerlog*](/api/resources/platform-created/triggerlog.md) Resource.

## Fields Specificcation

Name        |Type      | Possible Values |  Description
------------|----------|----------------|----------- 
triggerId | `String`| Any valid [*Trigger*](/api/resources/user-created/trigger.md) ID | The ID of the [*Trigger*](/api/resources/user-created/trigger.md) which the *Triggerlog* refers to.
triggeredAt [`Date`](/api/data-models/common/date.md) | ANY valid `Date` | The date and time when the event defined by the related [*Trigger*](/api/resources/user-created/trigger.md) has been detected.
target | [`DeviceBase-Segment`](/api/dimensions/device-base.md) | Any valid [`DeviceBase-Segment`](/api/dimensions/device-base.md)| The specific target, among those defined by the related [*Trigger*](/api/resources/user-created/trigger.md), for which the event occurred (see [target of a *Trigger*](/api/concepts/triggers.md#targets-definition))
deliveries | `[[Delivery](#delivery)]`| Any valid [Delivery](#delivery) Object | A set of [Delivery](#delivery) Objects, one for each [*Hook*](/api/resources/user-created/hook.md) linked to the related [*Trigger*](/api/resources/user-created/trigger.md).

## Example Object

```json
{
	"triggerId": "5964b7d5d5f455000133fe3e",
	"triggeredAt": "2017-07-11T11:50:06Z",
	"target": {
		"deviceId": [
			"5964b920052d45000134ec92"
		]
	},
	"deliveries": [{
		"hookId": "5964b6acd5f455000133fe3c",
		"status": "Delivered",
		"executedAt": "2017-07-11 11:50:06.912 +0000 UTC"
	}]
}
```

# Delivery

Models the result of the action defined by a [*Hook*](/api/resources/user-created/hook.md); i.e., whether it succeeded or not.  

Name        |Type      | Possible Values |  Description
------------|----------|----------------|-----------
hookId | `String` | Any valid [*Hook*](/api/resources/user-created/hook.md) ID | The ID of the [*Hook*](/api/resources/user-created/hook.md) which the `Delivery` refers to.
status | `String` | `{"Delivered", "Failed"}` | The status of the `Delivery`.
executedAt | [`Date`](/api/data-models/common/date.md) | ANY valid `Date` | The date and time when the action defined by the [*Hook*](/api/resources/user-created/hook.md) has been performed.

## Example Object

```json
{
	"hookId": "5964b6acd5f455000133fe3c",
	"status": "Delivered",
	"executedAt": "2017-07-11T11:50:06Z"
}
```
