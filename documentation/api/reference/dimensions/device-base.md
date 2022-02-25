* [Documentation Home](../../../README.md)  
  * [Web API](../../index.md)  
    * [Reference](../index.md)
        * [Dimensions](index.md)

# Device Base

The *Device Base* dimension relates to the set of possible devices.
This Dimension is not determined in advance but is created and grows as new 
[*Device*](../resources/platform-created/device.md) Resources are created.
A *Device Base* Segment can represent any sub-set of all the *Device* resources.

 - **Segment Data Model**: [`DeviceBase-Segment`](../data-models/d-segment/device-base.md)
 - **Segmentation Data Model**: [`DeviceBase-Segmentation`](../data-models/d-segmentation/device-base.md)

## Segmentation Criteria

The following segmentation criteria are defined for *Device Base*.

### By Device

Allows to segment a *Device Base* Segment in subsegments of one *Device* each. 

#### Mapping on the Segmentation object

This Criterion can be indicated using a 
[`DeviceBase-Segmentation`](../data-models/d-segmentation/device-base.md) object as below.

Name    | Type | Allowe Values
--------|----- |--------------
device  | `Integer` | {`1`}

```json
{
    "device": 1
}
```

The value of the `"device"` field must be set equal to `1`. 
This is because the criterion does not require to indicate any granularity since 
resulting segments will always refer to one and only one specific *Device*. 


#### Resulting Segments

Resulting Segments are indicated on the output side through a 
[`DeviceBase-Segment`](../data-models/d-segment/device-base.md) object as below.

Name    | Type | Description
--------|----- |--------------
deviceId  | `[String]` | Will Contain only one value corresponding to the ID of the *Device* which the Segment refers to.


```json
{
    "deviceId": ["Device1"]
}
```

### By Client App

Allows to segment a *Device Base* Segment in (sub-)Segments according to the 
[Client App](../../../service-architecture.md): each Segment will be composed of all the 
*Devices* belonging to a same *Client App*.


#### Mapping on the Segmentation object

This Criterion can be indicated using a 
[`DeviceBase-Segmentation`](../data-models/d-segmentation/device-base.md) object as below.

Name    | Type | Allowe Values
--------|----- |--------------
clientApp  | `Integer`| {`1`} 


```json
{
    "clientApp": 1
}
```


The value of the `"clientApp"` field  must be set equal to `1`.
This is because the criterion does not require to indicate any granularity since 
resulting segments will always refer to one and only one specific *Client App*. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`DeviceBase-Segment`](../data-models/d-segment/device-base.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
clientAppId  | `[String]` | Will Contain only one value corresponding to the ID of the Client App which the Segment refers to.


```json
{
    "clientAppId": ["ClientApp1"]
}
```
