# Activity

An *Activity* represents a consecutive period of time during which a [*Device*](/api/reference/resources/resources/platform-created/device.md) has performed a specific type of movement, said [*Motion Type*](/api/reference/dimensionsdimensions/motion-type.md), such as a walk, a run, a travel in a vehicle, etc.
However, it can also represents a period of time during which the device has been almost stationary, which is said *Stationary Activity*.

> A *Stationary Activity* is characterized by a [*Motion Type*](/api/reference/dimensionsdimensions/motion-type.md) of value equal to "stationary".

An *Activity* is mainly defined through: a) the Motion Type, which defines it as a [*Point*](/api/reference/configurations%20and%20operators.md) on the [*Motion Type*](/api/reference/dimensionsdimensions/motion-type.md) Dimension; b) the Start Time and the End Time, which define the it as an [*Interval*](/api/reference/configurations%20and%20operators.md) on [*Time*](/api/reference/dimensionsdimensions/time.md); c) the Path, corresponding to the set of [*Detected Position*](/api/reference/resources/resources/platform-created/device-related/detected-position.md) detected from the Start and End times, which defines it as a [*Sequence*](/api/reference/configurations%20and%20operators.md) on [*Space*](/api/reference/dimensionsdimensions/space.md).

> For a *Stationary Activity*, the path will contain only one [*Detected Position*](/api/reference/resources/resources/platform-created/device-related/detected-position.md).

The whole set of *Activity* Resources of a same *Registered Device* defines its "movement history".
*Activities* compose an ordered list and are such that the end time of one of them always correspond to the start time of the next one, up to the *Activity* that is still in progress.

Whilst a single *Activity* Resource has one and only one Motion Type, it is possible that two consecutive *Motion Acitivity* Resources are created with the same Motion Type.
This could happen if the characteristics of the movement change significantly, for example in terms of average speed.

## Dimesnions

*Activities* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/reference/dimensionsdimensions/device-base.md)   | [*Point*](/api/reference/configurations%20and%20operators.md)   | An *Activity* relates to a *Device*
[*Space*](/api/reference/dimensionsdimensions/space.md)   | [*Sequence*](/api/reference/configurations%20and%20operators.md)   | An *Activity* assumes several ordered values on *Space*, once for each *Detected Position* in its Path.
[*Time*](/api/reference/dimensionsdimensions/time.md)   | [*Interval*](/api/reference/configurations%20and%20operators.md)   | An *Activity* lasts for a period of time, thus it includes all the possible *Points* on *Time* between the Start and the End time.
[*Motion Type*](/api/reference/dimensionsdimensions/motion-type.md) | [*Point*](/api/reference/configurations%20and%20operators.md) | An *Activity* is characterized by a specific *Motion Type*

## Metrics

An *Activity* defines the following *Metrics*.

- **Duration**. The time elapsed from the Start Time and the End Time.
- **Travelled Distance**. An estimation of the distance travelled during the period of time which the *Activity* refers to.
- **Average Speed**. The average speed computed as ratio between the Travelled Distance and the Duration.
- **Start-End Distance**. The distance between the first and the last position of the Path.
- **Straight Index**. The ratio between the Start-End Distance and the Travelled Distance, which gives an indication of how the device moved on a straight path.

## Data Model

The data model used to represent an *Activity* is [`Activity`](/api/reference/data-modelsata-models/resources/platform-created/device-related/activity.md).


## Resource Segment Data Model

The data model used to represent a *Activity* Segment is [`Activity-Segment`](/api/reference/data-modelsata-models/r-segment/activity.md)

## Endpoints

- [Resources](/api/reference/endpoints/endpoints/resources/platform-created/device-related/activity.md)
- [Statistic](/api/reference/endpoints/endpoints/statistics/activity.md) 


