# Home Location

A *Home Location* represents the geographical position where presumably a User resides.

Unlike *Living Areas*, more than one *Home Location* could be related to the same *Device* in case a User ususally resides in several different locations, as for instance in case of a User that moves in a different city during week for work and then comes back to its home during week-ends.
However, the total number of *Home Locations* related to a same *Device* is always limited to very few units.

Similarly, it could be possible that no *Home Location* is identified for a *Device*.

A *Home Location* is defined through: a) the Reference Position, whcich defines it as a [*Point*](/api/geometries-and-operators.md) on [*Space*](/api/dimensions/space.md)

## Dimesnions

*Home Locations* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Home Location* relates to a *Registered Device*
[*Space*](/api/dimensions/space.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Home Location* is a single *Point* on *Space*, that correspond to its Reference Position.

## Metrics

No *Metric* is defined for *Home Locations*

## Data Model

The data model used to represent a *Home Location* is [`HomeLocation`](/api/data-models/resources/platform-created/device-related/home-location.md).


## Resource Segment Data Model

The data model used to represent a *HomeLocation* Segment is [`HomeLocation-Segment`](/api/data-models/r-segment/home-location.md)

## Endpoints

- [Selection](/api/endpoints/resources/platform-created/device-related/home-location.md)
- [Statistic](api/endpoints/statistics/home-location.md) 

