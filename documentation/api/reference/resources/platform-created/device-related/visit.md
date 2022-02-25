* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Resources](../../index.md)
           * [Platform-created Resources](../index.md)
                * [Device-related Resources](index.md)

# Visit

A *Visit* represents a period of time during which a *Device* dwelled in the same area.
A *Visit* can be thought at different [*Spatial Granularity* levels](../../../dimensions/spatial-granularity.md). It can represents a short period of time spent in a very small area, such as a building, or a period of time spent while visiting a town, or even a very long time spent in the same big area, as for example while dwelling in the same country.

For example, let us consider a person that gets out of its home in the morning to go to work.
He first stops few minutes at the bus stop; then gets to office; then goes out for lunch to the resturant close to the office; finally gets on the bus in the evening to come back home.
In such a situation, we would see several *Visits* at the finest granularity level, say "building", one at home, one at the bus stop in the morning, one at the office, one at the resturant, etc.
However, if we look at *Visits* with a coarser granularity, say "district", we would see only two Resources, one at his home district and one at his office district.
Finally, if we look at *Visits* at a even coarser granularity, say "country", we will se only one *Visit* as the device has always dwelled in the same area at this granularity.

A *Visit* is mainly defined through: a) the Spatial Granularity Level, which defines a *Visit* as a [*Point*](/api/reference/configurations%20and%20operators.md) on the [*Spatial Granularity*](/api/reference/dimensionsdimensions/spatial-granularity.md) Dimension; b) the Start Time and the End Time, which define the *Visit* as an [*Interval*](/api/reference/configurations%20and%20operators.md) on [*Time*](/api/reference/dimensionsdimensions/time.md); c) the Reference Position, which gives an indication about the geographical location were the device dwelled during the time of the *Visit* and defines the *Visit* as a [*Point*](/api/reference/configurations%20and%20operators.md) on [*Space*](/api/reference/dimensionsdimensions/space.md).

A *Visit* exists only if the *Registered Device* has spent a significant time within an area, which depends again on the *Spatial Granularity*: the coarser the *Spatial Granularity*, the higher the amount of time the device has to spend for a *Visit* to be created.

At the finest *Spatial Granularity*, a *Visit* generally corresponds to one [*Stationary Activity*](/api/reference/resources/resources/platform-created/device-related/activity.md), though this is not guaranteed.
However, at coarser *Spatial Granularities*, several *Actvities* could be performed during the time of the *Visit*, both *Stationary* and not.

## Dimesnions

*Visits* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/reference/dimensionsdimensions/device-base.md)   | [*Point*](/api/reference/configurations%20and%20operators.md)   | [*Point*](/api/reference/configurations%20and%20operators.md)   | A *Visit* relates to a *Device*
[*Space*](/api/reference/dimensionsdimensions/space.md)   | [*Sequence*](/api/reference/configurations%20and%20operators.md)   | A *Visit* contains two ordered *Points* on *Space*, that corresponds to its Start Position and End Position.
[*Time*](/api/reference/dimensionsdimensions/time.md)   | [*Interval*](/api/reference/configurations%20and%20operators.md)   | A *Visit* lasts for a period of time, thus it includes all the possible *Points* on *Time* between the Start and the End time.
[*Spatial Granularity* level](/api/reference/dimensionsdimensions/spatial-granularity.md)   | [*Point*](/api/reference/configurations%20and%20operators.md)   | A *Visit* has a specific Spatial Granularity Level, that is a single value on the *Spatial Granularity* Dimension.

## Metrics

*Visits* defines the following *Metrics*.

- **Duration**. The time elapsed from the Start Time and the End Time.

## Data Model

The data model used to represent a *Visits* is [`Visit`](/api/reference/data-modelsata-models/resources/platform-created/device-related/visit.md).

## Resource Segment Data Model

The data model used to represent a *Visit* Segment is [`Visit-Segment`](/api/reference/data-modelsata-models/r-segment/visit.md)

## Endpoints

- [Resources](/api/reference/endpoints/endpoints/resources/platform-created/device-related/visit.md)
- [Statistic](/api/reference/endpoints/endpoints/statistics/visit.md)
