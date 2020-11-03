# Device Base

The *Device Base* Dimension is the most important Dimension as all [Device-related Resources](/api/concepts/resource-definition.md#resources) are defined on it.
This Dimension is not determined in advance but is created and grows as new [*Device*](/api/resources/platform-created/device.md) Resources are created.
A *Device Base* Segment can represent ANY sub-set of all the [*Device*](/api/resources/platform-created/device.md) Resources

 - **Resource CLasses**: All [Device-related Resources](/api/resources/platform-created/device-related/index.md)
 - **Segment Data Model**: [`DeviceBase-Segment`](/api/data-models/d-segment/device-base.md)
 - **Segment/Segmentation Key**: `"deviceBase"`
 - **Segmentation Data Model**: [`DeviceBase-Segmentation`](/api/data-models/d-segmentation/device-base.md)

## Segmentation Criteria

The following segmentation criteria are defined for *Device Base*.

### By Device

Allows to segment a *Device Base* Segment in (sub-)Segments of one *Device* each. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`DeviceBase-Segment`](/api/data-models/d-segment/device-base.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
deviceId  | `[String]` | Will Contain only one value corresponding to the ID of the *Device* which the Segment refers to.
deviceCustomId  | `[String]` | Will Contain at most one value corresponding to the Custom ID set for the *Device* which the Segment refers to. If no Custom ID has been set for the *Device*, it will be an empty Array.
deviceToken  | `[String]` | Will Contain at most one value corresponding to the Token set for the *Device* which the Segment refers to. If no Token has been set for the *Device*, it will be an empty Array.


```json
{
    "deviceId": ["Device1"],
    "deviceCustomId": ["My Device Number 5"],
    "deviceToken": ["TOKEN_FOR_PUSH_NOTIFICATIONS"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`DeviceBase-Segmentation`](/api/data-models/d-segmentation/device-base.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
device  | `Integer` | {`1`}

```json
{
    "device": 1
}
```

#### Granularity

Allows only one value as granularity: each *Device Base* Segment refers to a specific *Device*. 
The value of the `"device"` field must be set equal to `1`. 

### By Client App

Allows to segment a *Device Base* Segment in (sub-)Segments according to the [Client App](service-architecture.md): each Segment will be composed of all the *Devices* belonging to a same *Client App*.

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`DeviceBase-Segment`](/api/data-models/d-segment/device-base.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
clientAppId  | `[String]` | Will Contain only one value corresponding to the ID of the Client App which the Segment refers to.


```json
{
    "clientAppId": ["ClientApp1"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`DeviceBase-Segmentation`](/api/data-models/d-segmentation/device-base.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
clientApp  | `Integer`| {`1`} 

```json
{
    "clientApp": 1
}
```

#### Granularity

Allows only one value as granularity: each *Segment* refers to one specific *Client App*. 
The value of the `"clientApp"` field  must be set equal to `1`.

### By Os Name 

Allows to segment a *Device Base* Segment according to the name of the operating system: 
Each *Segment* is composed of all the *Devices* withe a same operating system. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`DeviceBase-Segment`](/api/data-models/d-segment/device-base.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
osName  | `[String]` | Will Contain only one value corresponding to the name of the OS which the Segment refers to.


```json
{
    "osName": ["Android"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`DeviceBase-Segmentation`](/api/data-models/d-segmentation/device-base.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
osName  | `Integer` | {`1`}

```json
{
    "osName": 1
}
```

#### Granularity

Allows only one value as granularity: each *Segment* refers to a specific Operating System. 
The value of the `"osName"` field must be set equal to `1`.
