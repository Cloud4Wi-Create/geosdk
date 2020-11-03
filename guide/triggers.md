# Trigger Basic steps

To set a Trigger, the following basic steps must be performed.

- Create a [*Hook*](/api/resources/user-created/hook.md)
- Create a [*Trigger*](/api/resources/user-created/trigger.md) defining the desired Event and link it to the *Hook*

---

# Create a *Hook*

*Hooks* can be created through the related [Endpoint](/api/endpoints/resources/user-created/hook/create.md).

Currently, only [*Web Hooks*](/api/resources/user-created/hook.md#web-hook) are provided, which allow to receive a Web Notification to an URL of choice.

The example request below allows to create a *Web Hook*.
First, [obtain a valid access token](/guide/obtain-access-token.md) and use it for `<ACCESS_TOKEN>` placeholder.
Then, provide a valid URL for the `"web.url"` field.

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/hooks \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"My First Hook","description":"A simple web hook","labels":["test"],"type":"web","web":{"url":"https://api.mydomain.com/geouniq/test"}}'
```


---

# Create a Trigger

*Triggers* can be created through the related [Endpoint](/api/endpoints/resources/user-created/trigger/create.md).

When a *Trigger* is created, several parameters have to be decided, which are related to some different aspects.
Such parameters are set through the fields of the [`Trigger`](/api/data-models/resources/user-created/trigger.md) Object provided in the body of the Request.
In detail, the following main aspects have to be considered.

1. When the *Trigger* has to be active. This is ruled by the [`"activeOn"`](/api/data-models/resources/user-created/trigger.md) field.
2. What is the Target, or what are the Targets, of the *Trigger*. This is ruled by the [`"targets"`](/api/data-models/resources/user-created/trigger.md) field.
3. What is the event that has to be monitored. This is ruled by the [`"eventDefinition"`](/api/data-models/resources/user-created/trigger.md) field.
4. What has to be done when the event occurs. This is ruled by the set of *Hooks* linked to the *Trigger* through the field [`"hooks"`](/api/data-models/resources/user-created/trigger.md).

Concerning point 1, in most cases you want a *Trigger* to be active indefinitely, until it gets completely deleted.
If this is the case, simply do not provide the `"activeOn"` field or set it to `null`.
Otherwise, have a look at how a [`TimeSegment`](/api/data-models/d-segment/time.md) Object is defined.
In addition, regardless of the `"activeOn"` field, a *Trigger* can be enabled and disabled through a specific "flag": [`"status.enabled"`](/api/data-models/resources/user-created/trigger.md).
This flag must be explicitely set to `true`, otherwise it will assume the default value `false` and the *Trigger* will never be active.
You can change the value of this filed by updating the *Trigger* in any moment through the related [endpoint](/api/endpoints/resources/user-created/trigger/update.md).



Concerning point 2, some common cases are described below.

Concerning point 3, some common use cases are provided [here](/use-cases/index.md).

Finally, concerning point 4, you simple have to provide one or more *Hook* IDs in the [`"hooks"`](/api/data-models/resources/user-created/trigger.md) field.
In the following, we always consider to link an example *Hook* with ID `"hook1"`.
You should substitue that value with a valid *Hook* ID for the request to be valid.


## Deciding the Targets of a *Trigger*

A *Trigger* can have one or more Targets.
When a *Trigger* has more than one Target, the event defined by the *Trigger* will be monitored for each Target.
This is equivalent to create several *Triggers*, one for each Target.
However, in many cases, creating a single *Trigger* with several Targets can be very useful.
Note that, a single Target can correspond to a single device but also to several devices.
This mainly depends on whether the actual event that has to be monitored involves only one device or several devices.

In this guide, only the first case is treated.

### Events that involve only one device

In most cases, one is interested in monitoring an event that involves only one device.
This is the case of a geofence, where one is interested in monitoring when a device "enters", "enters and dwells", or "leaves" a specific area.
In this case, even if the actual event refers to only one device, it is very likely that one wnats to monitor the same kind of event for each device of its device-base, or for several of them.


In the following, some common example cases are provided.

#### The event has to be monitored for each device of the device-base

In this case, it is possible to create only one *Trigger* that will be "replicated" for each device, even for those that will be created in the future.
To achieve this goal, the [`"targets"`](/api/data-models/resources/user-created/trigger.md) field has to be set as it follows.


```json
{
    "targets": {
        "select": null,
        "segmentBy": {
            "device": 1
        }
    }
}
```

`"select": null` means "the whole device-base"; `"segmentBy": {"device": 1}` means "create a Target for each device belonging to the group identified by `"select"`".

The following example request creates a *Trigger* for each device of the device-base.
Note that:

* The *Trigger* is disabled (`"status.enabled": false`).
* The event (`"eventDefinition"` filed) means "when the first position update is received"

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"targets":{"select":null,"segmentBy":{"device":1}},"status":{"enebled":false},"eventDefinition":{"nodeType":"detectedPosition","detectedPosition":{"evaluate":{"count":{"gt":0}}}},"hooks":["hook1"]}'
```

#### The event has to be monitored for each device belonging to an explicit set

In this case, it is possible to create only one *Trigger* that will be "replicated" for each device belonging to an explicit set, which is indicated by providing a set of Device IDs.
To achieve this goal, the [`"targets"`](/api/data-models/resources/user-created/trigger.md) field has to be set as it follows.


```json
{
    "targets": {
        "select": {
            "deviceId": ["device1", "device2", "device3"]
        },
        "segmentBy": {
            "device": 1
        }
    }
}
```

`"select": {"deviceId": ["device1", "device2", "device3"]}` means "devices whose ID is in the provided array"; `"segmentBy": {"device": 1}` means "create a Target for each device belonging to the group identified by `"select"`".

The following example request creates a *Trigger* for each device belonging to an explicit group.
Note that:

* The *Trigger* is disabled (`"status.enabled": false`).
* The set of Device IDs provided in the `"deviceId"` array are invalid, which makes the whole request invalid.
* The event (`"eventDefinition"` filed) means "when the first position update is received".

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"targets":{"select": {"deviceId": ["device1", "device2", "device3"]},"segmentBy":{"device":1}},"status":{"enebled":false},"eventDefinition":{"nodeType":"detectedPosition","detectedPosition":{"evaluate":{"count":{"gt":0}}}},"hooks":["hook1"]}'
```

#### The event has to be monitored for one device only

In this case, the *Trigger* must have only one Target.
This case is a similar to the previous one but: a) only the ID of the specific Device has to be provided in the `"deviceId"` array; b) the field `"segmentBy"` is not necessary and can be omitted.
In detail, the [`"targets"`](/api/data-models/resources/user-created/trigger.md) field has to be set as it follows.


```json
{
    "targets": {
        "select": {
            "deviceId": ["device1"]
        }
    }
}
```


The following example request creates a *Trigger* for only one Device.
Note that:

* The *Trigger* is disabled (`"status.enabled": false`).
* The Device ID provided in the `"deviceId"` array is invalid, which makes the whole request invalid.
* The event (`"eventDefinition"` filed) means "when the first position update is received".

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"targets":{"select": {"deviceId": ["device1"]}},"status":{"enebled":false},"eventDefinition":{"nodeType":"detectedPosition","detectedPosition":{"evaluate":{"count":{"gt":0}}}},"hooks":["hook1"]}'
```

----

# Receiving Web Notifications

Each time the event defined by a *Trigger* linked to a *WebHook* occurs, a *Web Notification* is sent to the indicated URL throuhg the following HTTP request.

The HTTP Request is specified [here](/api/resources/user-created/hook.md#web-notification-request-specification).
The Request carries a body like the following.

`"trigger"` contains information about the specific *Trigger* that has led to sending the Web Notification.
`"involvedTarget"` tells for which Target of the Trigger the event occurred. This is particularly useful when a Trigger has more than one Target.
In the example below, the Traget is composed of only one device whose ID, Custom ID (if set on the mobile side), and Token (if set on the mobile side) are provided.
Finally, the field `triggeredAt` tells when it was identified by GeoUniq Trigger platform.


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
    "triggeredAt": "2016-01-01T01:00:25Z"
}
```

