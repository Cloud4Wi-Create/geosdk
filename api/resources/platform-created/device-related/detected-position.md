# Detected Position

A *Detected Position* represents the position of a [*Device*](/api/resources/platform-created/device.md) at a specific time.
It is the rawest data provided by this API.

## Dimensions

*Detected Positions* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Detected Position* relates to a single *Device*
[*Space*](/api/dimensions/space.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Detected Position* assumes a single value on *Space*, that is the geographical location.
[*Time*](/api/dimensions/time.md)   | [*Interval*](/api/geometries-and-operators.md)   | Each *Detected Position* is considered valid for a period of time, though only a single timestamp is indicated in the related Data Model.

## Metric Attributes

The following Metric Attributes are defined for *Detected Position*:

- *speed*: gives an indication of the average speed during the validity period of a *Detected Position*.

## Resource Data Model

The data model used to represent a *Detected Position* is [`DetectedPosition`](/api/data-models/resources/platform-created/device-related/detected-position.md)

## Resource Segment Data Model

The data model used to represent a *Detected Position* Segment is [`Detectedposition-Segment`](/api/data-models/r-segment/detected-position.md)

## Endpoints

- [Resources](/api/endpoints/resources/platform-created/device-related/detected-position.md)
- [Statistic](/api/endpoints/statistics/detected-position.md)
