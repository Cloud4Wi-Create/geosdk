# Hook

*Hook* Resources represent a building block for the [Trigger Platform](/api/concepts/triggers.md).

In detail, a *Hook*:

* can be linked to one or more [*Trigger*](/api/resources/user-created/trigger.md) Resources
* defines an action to be performed when the event defined by a *Trigger* linked to it occurs.

A *Hook* Resource is mainly chracterized by:

* **Resource ID and creation time**. Assigned by the Cloud4Wi Geo Services Platform.
* **Name, Description, and Labels.** Descriptive Information provided when the Resource is created.
* **Type**. Indicates the type of *Hook*.
* **Type Specific Information.** Information specific of each type of *Hook*.


Currently, the following types of *Hook* are defined.

* ***WebHook***. Allows to receive a [Web Notification](#web-notification) through an HTTP POST Request to a specified URL.

## Resource Data Model

The data model used to represent a *Hook* is [`Hook`](/api/data-models/resources/user-created/hook.md)

## Endpoints

- [Create single Resource](/api/endpoints/resources/user-created/hook/create.md)
- [Read whole Collection](/api/endpoints/resources/user-created/hook/read-collection.md)
- [Read single Resource](/api/endpoints/resources/user-created/hook/read-resource.md)
- [Update single Resource](/api/endpoints/resources/user-created/hook/update.md)
- [Delete single Resource](/api/endpoints/resources/user-created/hook/delete.md)

<a name="web-notification"></a>
# Web Notification Request Specification

**METHOD**: POST

**URL**: The url indicated in the `"url"` field of the related [`WebHook`](/api/data-models/resources/user-created/hook.md#web-hook) Object.

**REQUEST BODY**

Name | Type |   Description
------------|------------|------------
trigger    | `JSON` | Info about the [*Trgigger*](/api/resources/user-created/trigger.md), as defined for a [`Trigger`](/api/data-models/resources/user-created/trigger.md) Object.
trigger.id   | `String` | Value of the `"id"` field of the related `Trigger` Object.
trigger.name   | `String` | Value of the `"name"` field of the related `Trigger` Object.
trigger.description   | `String` | Value of the `"description"` field of the related `Trigger` Object.
trigger.labels   | `[String]` | Value of the `"labels"` field of the related `Trigger` Object.
involvedTarget |[`DeviceBase-Segment`](/api/data-models/d-segment/device-base.md)| Indicates the specific Target for which the event occurred. This is indicated through a *Device Base* Segment Object constructed according to the [*Device Base* Segmentation](/api/dimensions/device-base.md#segmentation-criteria) indicated in the `"targets.segmentBy"` field of the related `Trigger` Object.
triggeredAt | [`Date`](/api/data-models/common/date.md) | The date and time when the event was identified by Cloud4Wi Geo Services Platform.
occuredAt | [`Date`](/api/data-models/common/date.md) | The date and time when the event actually occured.



```json
{
    "trigger" : {
        "id": "Trigger1",
        "name": "My Trigger",
        "description": "My first trigger",
        "labels": ["test", "geofence"],
    },
    "involvedTarget": {
        "deviceId": ["Device1"],
        "deviceCustomId": ["My Device Number 5"],
        "deviceToken": ["TOKEN_FOR_PUSH_NOTIFICATIONS"]
    },
    "triggeredAt": "2016-01-01T01:00:25Z",
    "occurredAt": "2016-01-01T01:00:03Z"
}
```






