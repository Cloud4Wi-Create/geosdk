* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Resources](../../index.md)
           * [Platform-created Resources](../index.md)
                * [Device-related Resources](index.md)
                
# Work Location

A *Work Location* represents the geographical position where a User presumably works.

Similarly to [*Home Locations*](home-location.md), more than one *Work Location* could be related to the same *Device* in case a User ususally works in several different locations.
However, even in this case, the total number of *Work Locations* related to a same *Device* is always limited to very few units.

Similarly, it could be possible that no *Work Location* is identified for a *Device*. This is not so unlikely as several professions do not imply a specific work location. 

A *Work Location* is defined through: a) the Reference Position, whcich defines it as a [*Point*](/api/reference/configurations%20and%20operators.md) on [*Space*](/api/reference/dimensionsdimensions/space.md).

## Dimesnions

*Work Locations* are defined on the following *Dimensions*.

Dimension  | Geometry | Description
------------------  |-------------  |---------  
[*Device Base*](/api/reference/dimensionsdimensions/device-base.md)   | [*Point*](/api/reference/configurations%20and%20operators.md)   | A *Work Location* relates to a single  *Device*
[*Space*](/api/reference/dimensionsdimensions/space.md)   | [*Point*](/api/reference/configurations%20and%20operators.md)   | A *Work Location* is a single *Point* on *Space*, that correspond to its Reference Position.

## Metrics

No *Metric* is defined for *Work Locations*

## Data Model

The data model used to represent a *Work Location* is [`WorkLocation`](/api/reference/data-modelsata-models/resources/platform-created/device-related/work-location.md).

## Resource Segment Data Model

The data model used to represent a *Work Location* Segment is [`WorkLocation-Segment`](/api/reference/data-modelsata-models/r-segment/work-location.md)

## Endpoints

- [Resources](/api/reference/endpoints/endpoints/resources/platform-created/device-related/work-location.md)
- [Statistic](/api/reference/endpoints/endpoints/statistics/work-location.md) 
