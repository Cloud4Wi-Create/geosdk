# Device

A *Device* relates to a single installation of a [Client App](/service-architecture.md) on a physical device.
It represents the most important Resource Class as it **defines the** ***[Device Base](/api/dimensions/device-base.md)*** **Dimension**.
All the [Device-related Resources](/api/resources7platfrom-created/device-related/index.md) make reference to a specific *Device* Resource.
By convention, this API also defines that *Device* is itself defined on the *Device Base* Dimension. 

## Dimensions

*Devices* are defined on the following Dimensions.

Dimension  | Geometry | Description
------------------  |-------------  |---------  |
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)   | Each *Device* is an element of the *Device Base*
[*Time*](/api/dimensions/space.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Device* is a single *Point* on *Time*, that correspond to its Registration Time.

## Metrics

No metric is defined for *Device*

## Resource Data Model

The data model used to represent a *Device* is [`Device`](/api/data-models/resources/platform-created/device.md)

## Resource Segment Data Model

The data model used to represent a *Device* Segment is [`Device-Segment`](/api/data-models/r-segment/device.md)

## Endpoints

- [Resources](/api/endpoints/resources/device-related/device.md)
- [Statistic](/api/endpoints/statistics/device.md)

