# G-D-SelectionOperation

Models used to indicate any possible combination of [Dimensional Selection Operations](/api/concepts/resource-selection.md#dimensional-selection-conditions) for a Resource type that assumes a given [Geometry *G* on a given Dimension *D*](/api/concepts/resource-definition.md#geometries).

These Data Models are generically indicated as `G-D-Selection`, where *G* represents a generic Geometry and *D* a generic Dimension.
These Data Models are used into [`R-Segment`](/api/reference/data-modelsata-models/r-segment/index.md) Objects to indicate [Dimensional Selection Conditions](/api/concepts/resource-selection.md#dimensional-selection-conditions) for *R* on each Dimension *D*.

Specifically, they are used

- **on the input side**: to indicate the set of desired [Dimensional Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) for a given Dimension *D*.
    - [**when accessing Resources**](/api/reference/endpoints/endpoints/resources/index.md)
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md)
- **on the output side**:
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md): to indicate the [Dimensional Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) that has been applied for a Dimension *D*.


Depending on the specific Geometry *G* and Dimension *D*, a different `G-D-Segment` Data Model is defined:

* [`Point-DeviceBase-SelectionOperation`](api/data-models/g-d-selection-operation/point-device-base.md)
* [`Point-Space-SelectionOperation`](api/data-models/g-d-selection-operation/point-space.md)
* [`Point-Time-SelectionOperation`](api/data-models/g-d-selection-operation/point-time.md)
* [`Point-SpatialGranularity-SelectionOperation`](api/data-models/g-d-selection-operation/point-spatial-granularity.md)
* [`Point-MotionType-SelectionOperation`](api/data-models/g-d-selection-operation/point-motion-type.md)
* [`Multipoint-Space-SelectionOperation`](api/data-models/g-d-selection-operation/multipoint-space.md)
* [`Sequence-Space-SelectionOperation`](api/data-models/g-d-selection-operation/sequnce-space.md)
* [`Sequence-Airports-SelectionOperation`](api/data-models/g-d-selection-operation/sequnce-airports.md)
* [`Interval-Time-SelectionOperation`](api/data-models/g-d-selection-operation/interval-time.md)

