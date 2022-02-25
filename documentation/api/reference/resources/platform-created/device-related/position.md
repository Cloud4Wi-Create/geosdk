* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Resources](../../index.md)
           * [Platform-created Resources](../index.md)
                * [Device-related Resources](index.md)
# Position

A *Position* represents the position of a [*Device*](../device.md) at a specific time.
It is the rawest data provided by this API.

## Dimensions

*Detected Positions* are defined on the following *Dimensions*.

Dimension  | Configuration | Description
------------------  |-------------  |---------  
[*Device Base*](../../../dimensions/device-base.md)   | [*Point*](../../../configurations-and-operators.md)   | A *Detected Position* relates to a single *Device*
[*Space*](../../../dimensions/space.md)   | [*Point*](../../../configurations-and-operators.md)  | A *Detected Position* assumes a single value on *Space*, that is the geographical location.
[*Time*](../../../dimensions/time.md)   | [*Interval*](../../../configurations-and-operators.md)   | Each *Detected Position* is considered valid for a period of time, though only a single timestamp is indicated in the related Data Model.

## Metric Attributes

The following Metric Attributes are defined for *Detected Position*:

- *speed*: gives an indication of the average speed during the validity period of a *Detected Position*.

## Resource Data Model

The data model used to represent a *Detected Position* is [`DetectedPosition`](../../../data-models/resources/platform-created/device-related/detected-position.md)

## Resource Segment Data Model

The data model used to represent a *Detected Position* Segment is [`Detectedposition-Segment`](../../../data-models/r-selection/detected-position.md)

## Endpoints

- [Resources](../../../endpoints/resources/platform-created/device-related/detected-position.md)
- [Statistic](../../../endpoints/statistics/detected-position.md)
