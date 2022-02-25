# DeviceBase-Segment

Data model used to indicate a 
[`DeviceBase-Segment`](/api/dimension/device-base.md); i.e. a set of [*Device*](/api/reference/resources/resources/platform-created/device.md) Resources.

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
deviceId | `[String]` | ANY combination of Device IDs | All the devices whose ID is in the provided set.
clientAppId | `[String]` | ANY combination of Client App IDs | All the devices belonging to a Client App whose ID is in the provided set.

## Input side

Used to indicate a [Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) on the [*Device Base*](/api/reference/dimensionsdimensions/device-base.md) Dimension.
**Only one** among `deviceId`, `clientAppId`,  and `osName` fields can be provided.

**Example Input Object**

```json
{
    "deviceId" : ["D1", "D2", "D3"]
}
```

```json
{
    "applicationId" : ["A1", "A2", "A3"]
}
```

## Output side

Used to indicate which *Device Base* Segment a Resource Segment refers to when a Segmentation operation is requested on the *Device Base* Dimension (see [Segmentation](/api/concepts/statistics.md#segmentation-operation)).
Depending on the specific Segmentation Criterion, different fields will be provided, as detailed [here](/api/reference/dimensionsdimensions/device-base.md#segmentation-criteria).
