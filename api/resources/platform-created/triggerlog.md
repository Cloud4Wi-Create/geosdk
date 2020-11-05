# Triggerlog

A *Triggerlog* models a single occurrence of an event defined by a [*Trigger*](/api/resources/user-created/trigger.md).
*Triggerlog* Resources are automatically created by GeoUniq analytics platform each time the event defined by a specific *Trigger* is detected.

## Dimensions

*Triggerlog* are defined on the following Dimensions.

Dimension  | Geometry | Description
------------------  |-------------  |---------  |
[*Time*](/api/dimensions/space.md)   | [*Point*](/api/geometries-and-operators.md)   | A *Triggerlog* is a single *Point* on *Time*, that correspond to the time when the related event has been detected.

## Trigger Relationship

A *Triggerlog* Resource has a relationship with a specific *Trigger* Resource.
This API allows to select *Triggerlogs* according to this relationship by means of a [UserCreatedResource-Segment](/api/data-models/common/user-created-resource-segment.md)


## Metrics

No metric is defined for *Triggerlog*

## Resource Data Model

The data model used to represent a *Triggerlog* is [`Triggerlog`](/api/data-models/resources/platform-created/triggerlog.md)

## Resource Segment Data Model

The data model used to represent a *Triggerlog* Segment is [`Triggerlog-Segment`](/api/data-models/r-segment/triggerlog.md)

## Endpoints

- [Resources](/api/endpoints/resources/triggerlog.md)
- [Statistic](/api/endpoints/statistics/triggerlog.md)

