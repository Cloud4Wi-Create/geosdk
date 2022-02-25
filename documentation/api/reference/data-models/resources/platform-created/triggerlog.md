* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Data models](../../index.md)
          * [Resources data models](../index.md)
             * [Platform-created resources data models](index.md)

# TriggerLog

Data model used to represent a [TriggerLog](../../../resources/platform-created/triggerlog.md) Resource.

## Fields Specification

Name        |Type      | Possible Values |  Description
------------|----------|----------------|----------- 
trigger | [`UserCreatedResourceReferenece`](../../user-created/index.md)| Any valid [`UserCreatedResourceReferenece`](../../user-created/index.md) | The details of the [*Trigger*](/api/reference/resources/resources/user-created/trigger.md) resource which the *Triggerlog* refers to.
device | [`Device-Reference`](../../common/device-reference.md) | ANY valid [`Device-Reference`](../../common/device-reference.md) | reference information of the device which the *TriggerLog* resource refers to
event | [`EventLog`](#eventlog) | Any valid [`EventLog`](#eventlog) | contains information related to the specific event 

## EventLog

Name        |Type      | Possible Values |  Description
------------|----------|----------------|----------- 
type | `String`| `{"geofence"}` | The type of event.
geofence | [`GeofenceLog`](#geofencelog) | Provided only when `"type"` equals `"geofence"`; ANY valid [`GeofenceLog`](#geofencelog) | contains information specific to the geofence event  

## GeofenceLog

Name        |Type      | Possible Values |  Description
------------|----------|----------------|----------- 
type | `String`| `{"enter", exit}` | The transition type.
time | [`Date`](../../common/date.md) | ANY valid [`Date`](../../common/date.md) | The time instant whenthe transition occurred 

## Example Object

```json
{
  "trigger": "5964b7d5d5f455000133fe3e",
  "device": {
      "id": "device1",
      "clientAppId": "app1",
      "customId": "my device",
      "idfa": "550e8400-e29b-41d4-a716-446655440000"
  },
  "event":{
    "type": "geofence",
    "geofence":{
      "type": "enter",
      "time":"2021-01-01T00:00:00Z"
    }
  }
}
```
