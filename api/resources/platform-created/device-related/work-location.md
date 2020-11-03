# Work Location

A *Work Location* represents the geographical position where presumably a User works.

Similarly to *Home Locations*, more than one *Work Location* could be related to the same *Device* in case a User ususally works in several different locations.
However, even in this case, the total number of *Work Locations* related to a same *Device* is always limited to very few units.

Similarly, it could be possible that no *Work Location* is identified for a *Device*. This is not so unlikely as several professions do not imply a specific work location. 

A *Work Location* is defined through: a) the Reference Position, whcich defines it as a [*Point*](/api/geometries-and-operators.md) on [*Space*](/api/dimensions/space.md).

## Dimesnions

*Work Locations* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Work Location* relates to a single  *Device*
[*Space*](/api/dimensions/space.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Work Location* is a single *Point* on *Space*, that correspond to its Reference Position.

## Metrics

No *Metric* is defined for *Work Locations*

## Data Model

The data model used to represent a *Work Location* is [`WorkLocation`](/api/data-models/resources/platform-created/device-related/work-location.md).

## Resource Segment Data Model

The data model used to represent a *Work Location* Segment is [`WorkLocation-Segment`](/api/data-models/r-segment/work-location.md)

## Endpoints

- [Resources](/api/endpoints/resources/platform-created/device-related/work-location.md)
- [Statistic](/api/endpoints/statistics/work-location.md) 
