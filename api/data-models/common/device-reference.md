# DeviceReference

Data model used as a reference to a [Device](/api/resources/platform-created/device.md) Resource within [Device-Realted Resources](/api/resources/platform-created/device-related/index.md)

## Fields Specificcation

Name        | Type      | Possible Values | Description
------------|----------|----------------|-----------
id |`String` | Any valid Resource ID. Not provided when accessing third-party data | The ID assigned to the [Device](/api/resources/platform-created/device.md) Resource
clientAppId |`String` | Any valid Resource ID. Not provided when accessing third-party data | The ID assigned to the [Client App](/service-architecture.md) which the device belongs to
customId |`String` | Any value. Not provided when accessing third-party data | The custom ID if set for the device 
idfa | `String` | Any | The Advertising ID if available for the device
