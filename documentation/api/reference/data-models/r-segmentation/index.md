# R-Segmentation

Data Models used to indicate a [Segmentation Operation](/api/concepts/statistics.md#segmentation-operation) for a generic Resource type *R*.
These Data Models are generically indicated as `R-Segmentation`.
Similarly to an [`R-Segment`](/api/reference/data-modelsata-models/r-segment/index.md), an `R-Segmentation` can be derived considering which [Geometry](/api/concepts/resource-definition.md#geometries) *G* the specific resource type *R* assumes on each Dimension *D*, indicated as *G-D*. e.g. *Point-Space*, *Interval-Time*, etc.

For a specific *R*, the related `R-Segmentation` has a field for each Dimension *D* on which *R* is defined whose key is specified by the specific [Dimension](/api/reference/dimensionsdimensions/index.md) and whose Data Model is `[G-D-Segmentation`](/api/data-models/g-d-segmentation/index.md).


These Data Models are used:

- **on the input side**: 
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md): to indicate the desired Segmentation. 
- **on the output side**:
    - Never

According to the specific Resource type *R*, the following `R-Segmentation` Data Models are defined:

* [`DetectedPosition-Segmentation`](api/data-models/r-segmentation/detected-position.md)
* [`Activity-Segmentation`](api/data-models/r-segmentation/activity.md)
* [`Visit-Segmentation`](api/data-models/r-segmentation/visit.md)
* [`Travel-Segmentation`](api/data-models/r-segmentation/travel.md)
* [`HomeLocation-Segmentation`](api/data-models/r-segmentation/home-location.md)
* [`WorkLocation-Segmentation`](api/data-models/r-segmentation/work-location.md)
* [`LivingArea-Segmentation`](api/data-models/r-segmentation/living-area.md)
* [`Flight-Segmentation`](api/data-models/r-segmentation/flight.md)
