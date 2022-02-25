* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Data models](../index.md)
          * [Common Data Models](index.md)

# DeviceReference

Data model used as a reference to a [Device](../../resources/platform-created/device.md) resource within [Device-Realted Resources](../../resources/platform-created/device-related/index.md)

## Fields Specificcation

Name        | Type      | Possible Values | Description
------------|----------|----------------|-----------
id |`String` | Any valid Resource ID. Not provided when accessing third-party data | The ID assigned to the [Device](../../resources/platform-created/device.md) Resource
clientAppId |`String` | Any valid Resource ID. Not provided when accessing third-party data | The ID assigned to the [Client App](../../../../service-architecture.md) which the device belongs to
customId |`String` | Any value. Not provided when accessing third-party data | The custom ID if set for the device 
idfa | `String` | Any | The Advertising ID if available for the device

```json
{
  "id": "device1",
  "clientAppId": "app1",
  "customId": "my device",
  "idfa": "550e8400-e29b-41d4-a716-446655440000"
}
```
