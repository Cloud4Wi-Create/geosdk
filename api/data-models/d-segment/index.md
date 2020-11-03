# D-Segment

Data Models used to represent a [Segment of a Dimension](/api/concepts/resource-definition.md#dimension-segment) *D*.
These Data Models are generically indicated as `D-Segment`, where *D* represents a generic Dimension.
These Data Models are used into [`G-D-SelectionOperation`](/api/data-models/g-d-selection-operation/index.md) Objects.

Specifically, they are used:

- **on the input side**: to indicate the specific *D* Segment which the [Dimensional Selection Operator](/api/concepts/resource-selection.md#dimensional-selection-conditions) has to be applied to.
    - [**when accessing Resources**](/api/endpoints/resources/index.md)
    - [**when accessing Statistics**](/api/endpoints/statistics/index.md)

- **on the output side**: to indicate the specific *D* Segment which the [Dimensional Selection Operator](/api/concepts/resource-selection.md#dimensional-selection-conditions) has been applied to when a [Segmentation operation](/api/concepts/statistics.md#segmentation) has been performed for a given [Dimensional Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) on *D*.
    - [**when accessing Statistics**](/api/endpoints/statistics/index.md)


Depending on the specific Dimension *D*, a different `D-Segment` Data Model is defined:

* [`DeviceBase-Segment`](api/data-models/d-segment/device-base.md) 
* [`Space-Segment`](api/data-models/d-segment/space.md) 
* [`Time-Segment`](api/data-models/d-segment/time.md) 
* [`MotionType-Segment`](api/data-models/d-segment/motion-type.md) 
* [`SpatialGranularity-Segment`](api/data-models/d-segment/spatial-granularity.md) 
* [`Airports-Segment`](api/data-models/d-segment/airports.md) 
* [`FlightRange-Segment`](api/data-models/d-segment/flight-range.md) 
