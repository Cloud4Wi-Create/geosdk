# Living Area

A *Living Area* represents the geographical area where a *Device* spends most of its time.

A *Living Area* is defined through: a) the Reference Area, whcich defines it as a [*Multipoint*](/api/geometries-and-operators.md) (with an infinite number of *Points*) on [*Space*](/api/dimensions/space.md) .

The Reference Area always corresponds to a single polygon.
Depending on whether a User moves a lot or spends almost all its time in a small area, the *Living Area* will correspond to a very big or a very small area.

## Dimesnions

*Living Areas* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)  | A *Living Area* relates to a *Registered Device*
[*Space*](/api/dimensions/space.md)   | [*Multipoint*](/api/geometries-and-operators.md) | A *Living Area* contains an infinite number of *Points* on *Space*, that correspond to its Reference Area.

## Metrics

No *Metric* is defined for *Living Areas*

## Data Model

The data model used to represent a *Living Area* is [`LivingArea`](/api/data-models/resources/platform-created/device-related/living-area.md).


## Resource Segment Data Model

The data model used to represent a *Travel* Segment is [`LivingArea-Segment`](/api/data-models/r-segment/living-area.md)

## Endpoints

- [Resources](/api/endpoints/resources/platform-created/device-related/detected-position.md)
- [Statistic](/api/endpoints/statistics/detected-position.md)

