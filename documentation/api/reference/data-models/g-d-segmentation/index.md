# G-D-SelectionOperation

Data Models used to indicate any possible combination of [Dimensional Segmentations](/api/concepts/statistics.md#dimensional-segmentation) for any Resource type *R* that assumes a given [Geometry *G* on a given Dimension *D*](/api/concepts/resource-definition.md#geometries).

These models are generically indicated as `G-D-Segmentation`, where *G* represents a generic Geometry and *D* a generic Dimension.
These Data Models are used into [`R-Segmentation`](/api/reference/data-modelsata-models/r-segmentation/index.md) Objects to indicate [Dimensional Segmentations](/api/concepts/statistics.md#dimensional-segmentation) for *R* on each Dimension *D*.

Specifically, they are used

- **on the input side**
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md):to indicate the set of desired [Dimensional Segmentations](/api/concepts/statistics.md#dimensional-segmentation) for a given Dimension *D*.
- **on the output side**:
    - Never


Depending on the specific Geometry *G* and Dimension *D*, a different `G-D-Segmentation` Data Model is defined:

* [`Point-DeviceBase-Segmentation`](api/data-models/g-d-segmentation/point-device-base.md)
* [`Point-Space-Segmentation`](api/data-models/g-d-segmentation/point-space.md)
* [`Point-Time-Segmentation`](api/data-models/g-d-segmentation/point-time.md)
* [`Point-SpatialGranularity-Segmentation`](api/data-models/g-d-segmentation/point-spatial-granularity.md)
* [`Point-MotionType-Segmentation`](api/data-models/g-d-segmentation/point-motion-type.md)
* [`Multipoint-Space-Segmentation`](api/data-models/g-d-segmentation/multipoint-space.md)
* [`Sequence-Space-Segmentation`](api/data-models/g-d-segmentation/sequence-space.md)
* [`Sequence-Airports-Segmentation`](api/data-models/g-d-segmentation/sequence-airports.md)
* [`Interval-Time-Segmentation`](api/data-models/g-d-segmentation/interval-time.md)

