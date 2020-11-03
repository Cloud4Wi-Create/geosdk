# DeviceBase-Segment

Data model used to indicate a [`DeviceBase-Segment`](/api/dimension/device-base.md); i.e. a set of [*Device*](/api/resources/platform-created/device.md) Resources.

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
deviceId | `[String]` | ANY combination of Device IDs | All the devices whose ID is in the provided set.
deviceCustomId |`[String]` | Forbidden in requests | Provided in a response to a [Statistic](/api/basic-concepts#statistics) request when the [*By Device*](/api/dimensions/device-base#by-device) segmentation criteria is used for the [*Device Base*](/api/dimensions/device-base) Dimension.
deviceToken |`[String]` | Forbidden in requests | Provided in a response to a [Statistic](/api/basic-concepts#statistics) request when the [*By Device*](/api/dimensions/device-base#by-device) segmentation criteria is used for the [*Device Base*](/api/dimensions/device-base) Dimension. 
clientAppId | `[String]` | ANY combination of Client App IDs | All the devices belonging to a Client App whose ID is in the provided set.
osName | `[String]` | ANY combination of {`"android"`;`"ios"`} | All the devices having as operating system one of those indicated.

## Input side

Used to indicate a [Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) on the [*Device Base*](/api/dimensions/device-base.md) Dimension.
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

```json
{
    "osName" : ["android", "ios"]
}
```

## Output side

Used to indicate which *Device Base* Segment a Resource Segment refers to when a Segmentation operation is requested on the *Device Base* Dimension (see [Segmentation](/api/concepts/statistics.md#segmentation-operation)).
Depending on the specific Segmentation Criterion, different fields will be provided, as detailed [here](/api/dimensions/device-base.md#segmentation-criteria).
