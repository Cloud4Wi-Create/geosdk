# Flight

A *Flight* represents a flight detected for a [*Device*](/api/resources/platform-created/device.md).

A *Fight* is mainly defined through: a) the Departure Time and the Arrival Time, which define the *Flight* as an *Interval* on [*Time*](/api/dimensions/time.md); b) the Departure Position and the Arrival Position, which define the *Flight* as a two-points *Sequence* on [*Space*](/api/dimensions/dpace.md); c) the Departure Airport and the Arrival Airport, which define the *Flight* as: c1) a two-points *Sequence* on [*Airports*](/api/dimensions/airports.md); c2) a *Point* on [*Flight Route*](/api/dimensions/flight-route.md); c2) a *Point* on [*Flight Range*](/api/dimensions/flight-range.md).

> Flights are defined both on the  [*Airports*](/api/dimensions/airports.md) and the [*Flight Range*](/api/dimensions/flight-range.md) Dimensions in order to make it possible to select them according to a set of departure and/or arrival airports as well as to specific routes, i.e., specific departure-arrival airports pairs.

> The [*Fligh Range Dimension*](/api/dimensions/flight-range.md) makes it possible to select *Flights* according to whether the departure and arrival airports are located in the same country, same continent, or different continents.

When a *Flight* is detected, a corresopndent *Activity* (i.e., with the same Start Time, End Time, Start Position, and End Position) with [*Motion Type*](/api/dimensions/motion-type.md) equal to "flying" will exist for the *Device*.

## Dimesnions

*Flights* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/dimensions/device-base.md)   | [*Point*](/api/geometries-and-operators.md)  | A *Flight* relates to a *Registered Device*
[*Space*](/api/dimensions/space.md)   | [*Point*](/api/geometries-and-operators.md) | A *Flight* contains two ordered *Points* on *Space*, that correspond to its Start Position and End Position.
[*Time*](/api/dimensions/time.md)   | [*Interval*](/api/geometries-and-operators.md)| A *Flight* lasts for a period of time, thus it includes all the possible *Points* on *Time* between the Start and the End time.
[*Airports*](/api/dimensions/airports.md) | A *Flight* contains two ordered *Points* on *Airports*, that correspond to its Departure Airport and Arrival Airport.
[*Flight Route*](/api/dimensions/flight-route.md)| [*Point*](/api/geometries-and-operators.md)  | A *Flight* correspond to a single *Point* on *Flight Route*, that corresponds to the pair Departure Airport-Arrival Airport.
[*Flight Range*](/api/dimensions/flight-range.md) | A *Flight* correspond to a single *Point* on *Flight Range*, that depends on whether the Departure and Arrival Airports are located in the same country, same continent, or different continents .

## Metrics

*Flights* define the following *Metrics*.

- **Duration**. The time elapsed from the Start Time and the End Time.
- **Travelled Distance**. An estimation of the distance covered by the *Flight*.

## Data Model

The data model used to represent a *Flights* is [`Flight`](/api/data-models/resources/platform-created/device-related/flight.md).


## Resource Segment Data Model

The data model used to represent a *Flight* Segment is [`Flight-Segment`](/api/data-models/r-segment/flight.md)

## Endpoints

- [Resources](/api/endpoints/resources/platform-created/device-related/flight.md)
- [Statistic](/api/endpoints/statistics/flight.md)
