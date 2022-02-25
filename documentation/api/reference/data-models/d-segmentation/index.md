# D-Segmentation

Data models used to indicate how a a Segment of a [Dimension](/api/concepts/resource-definition.md#dimensions) *D* has to be divided in several (sub) Segments
These data models are generically indicated as `D-Segmentation` where *D* indicates the Dimension.
These Data Models are used into [`G-D-Segmentation`](/api/reference/data-modelsata-models/g-d-segmentation/index.md) Objects. 

Specifically, they are used:

- **on the input side**: to indicate the [Segmentation Criterion and Granularity](/api/concepts/statistics.md#segmentation-criteria) to use for a specific [Dimensional Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) on *D*.
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md):[Segmented Selection Conditions](/api/concepts/statistics.md#segmentation-operation).
- **on the output side**:
    - Never


A `D-Segmentation` object indicates the Segmentation Criterion to use and the Granularity for that Criterion.

For all these data models it holds the following general rule: **only one first level field is allowed**.
This is because each field, if present, implicitely indicates the [Segmentation Criterion](/api/concepts/statistics#segmentation-criteria) to use and, for each D-Segment, only one way (one criterion) to segment it can be indicated.

Depending on the specific Dimension *D*, a different `D-Segment` Data Model is defined:

* [`DeviceBase-Segmentation`](api/data-models/d-segmentation/device-base.md) 
* [`Space-Segmentation`](api/data-models/d-segmentation/space.md) 
* [`Time-Segmentation`](api/data-models/d-segmentation/time.md) 
* [`MotionType-Segmentation`](api/data-models/d-segmentation/motion-type.md) 
* [`SpatialGranularity-Segmentation`](api/data-models/d-segmentation/spatial-granularity.md) 
* [`Airports-Segmentation`](api/data-models/d-segmentation/airports.md) 
* [`FlightRange-Segmentation`](api/data-models/d-segmentation/flight-range.md) 

