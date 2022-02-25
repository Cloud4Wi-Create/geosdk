* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)
        * [Resources](../index.md)
           * [Platform-created Resources](index.md)
           
# Device

A *Device* relates to a single installation of a [Client App](../../../../service-architecture.md) on a physical device.
It represents the most important Resource type as it 
**defines the** ***[Device Base](../../dimensions/device-base.md)*** **Dimension**.  
All the [Device-related resources](device-related/index.md) make reference to a specific *Device* resource.
By convention, this API also defines that *Device* is itself defined on the *Device Base* Dimension. 

## Dimensions

*Devices* are defined on the following Dimensions.

Dimension  | Configuration | Description
------------------  |-------------  |---------  |
[*Device Base*](../../dimensions/device-base.md)   |  [*Point*](../../configurations-and-operators.md)  | Each *Device* is an element of the *Device Base*
[*Time*](../../dimensions/space.md)   | [*Point*](../../configurations-and-operators.md)   | A *Device* is a single *Point* on *Time*, that correspond to its Registration Time.

## Metrics

No metric is defined for *Device*

## Resource Data Model

The data model used to represent a *Device* is [`Device`](../../data-models/resources/platform-created/device.md)

## Resource Segment Data Model

The data model used to represent a *Device* Segment is [`Device-Segment`](../../data-models/r-selection/device.md)

## Endpoints

- [Selection](../../endpoints/platform-created/device/selection.md)
- [Statistic](../../endpoints/platform-created/device/statistic.md)

