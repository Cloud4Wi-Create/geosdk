# Travel

A *Travel* represents a movement between two [*Visits*](/api/resources/platform-created/device-related/visit.md) at the same [*Spatial Granularity* level](/api/dimensions/spatial-granularity.md).
Thus, like *Visits*, *Travels* are defined at different *Spatial Granularity* levels.

Depending on the *Spatial Granularity*, a *Travel* can represent different things.
At the "building" level, a *Travel* could correspond to a brief walk to get to the shop next to home, whilst at the "country" level it could correspond to the long journey a user had to get to the destination of its vacation.

A *Travel* is mainly defined through: a) the Spatial Granularity Level, which defines a *Travel* as a [*Point*](/api/geometries-and-operators.md)  on the [*Spatial Granularity* level](/api/dimensions/spatial-granularity.md) Dimension; b) the Start Time and the End Time, which define the *Travel* as an [*Interval*](/api/geometries-and-operators.md) on [*Time*](/api/dimensions/time.md); c) the Start Position and the End Position, which define the *Travel* as a two-points [*Sequence*](/api/geometries-and-operators.md) on [*Space*](/api/dimensions/space.md).


## Dimesnions

*Travels* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Travel* relates to a *Device*
[*Space*](/api/dimensions/space.md)   | [*Sequence*](/api/geometries-and-operators.md)   | A *Travel* contains two ordered *Points* on *Space*, that corresponds to its Start Position and End Position.
[*Time*](/api/dimensions/time.md)   | [*Interval*]((/api/geometries-and-operators.md)   | A *Travel* lasts for a period of time, thus it includes all the possible *Points* on *Time* between the Start and the End time.
[*Spatial Granularity* level](/api/dimensions/spatial-granularity.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Travel* has a specific Spatial Granularity Level, that is a single value on the *Spatial Granularity Dimension*.

## Metrics

*Travels* define the following *Metrics*.

- **Duration**. The time elapsed from the Start Time and the End Time.
- **Travelled Distance**. An estimation of the distance travelled during the period of time which the *Travel* refers to.
- **Start-End Distance**. The distance between the first and the last position of the Path.
- **Straight Index**. The ratio between the Start-End Distance and the Travelled Distance, which gives an indicatio of how the device moved on a straight path.
- **Average Speed**. The average speed computed as ratio between the Travelled Distance and the Duration.
- **Stationary Index**. The share of time spent on [*Activities*](/api/resources/platform-created/device-related/activity.md) with [*Motion Type*](/api/dimensions/motion-type.md) "stationary" with respect to the total duration of the *Travel*.

## Data Model

The data model used to represent a *Travels* is [`Travel`](/api/data-models/resources/platform-created/device-related/travel.md).

## Resource Segment Data Model

The data model used to represent a *Travel* Segment is [`Travel-Segment`](/api/data-models/r-segment/travel.md)

## Endpoints

- [Resources](/api/endpoints/resources/platform-created/device-related/travel.md)
- [Statistic](/api/endpoints/statistics/travel.md)
