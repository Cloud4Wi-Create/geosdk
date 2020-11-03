# Dimensions

This section lists the various [*Dimensions*](/api/concepts/resource-definition.md#dimensions) defined for this API.

This section is divided in several sub-sections, one for each Dimension.
For each Dimension *D*, the following is indicated.

- **Resource Classes**. The set of [*Resource Classes*](/api/concepts/resource-definition.md) defined on Dimension *D*.
- **D-Segment Data Model**. Link to the data model used to indicate a [*D* Segment](/api/concepts/resource-definition.md#segment-of-a-dimension). Such data models are generically indicated as [`D-Segment`](/api/data-models/d-segment/index.md) for a generic Dimension *D*. This Data Model is used in [`G-D-SelectionOperation`](/api/data-models/g-d-selection-operation/index.md) Data Model.
- **Segment/Segmentation Key**. Key used to indicate a [*D* Segment](/api/concepts/resource-definition.md#segment-of-a-dimension) or a [*D* Segmentation](/api/concepts/statistics.md#segmentation-operation). This key is used in  [`R-Segment`](/api/data-models/r-segment/index.md), [`R-Segmentation`](/api/data-models/r-segmentation/index.md), and [`R-Shares`](/api/data-models/r-shares/index.md) Data Models.
- **Segmentation Data Model**. Link to the data model used to indicate a [*D* Segmentation](/api/concepts/statistics.md#segmentation-operation). Such Data Models are generically indicates as [`D-Segmentation`](/api/data-models/d-segmentation/index.md).
- **Segmentation Criteria**. The [Segmentation Criteria](/api/concepts/statistics.md#segmentation-criteria) defined by *D* and, for each of them:
  - a descritpion of the criterion;
  - how a [*D* Segment](/api/concepts/resource-definition.md#segment-of-a-dimension) deriving from a [Segmentation](/api/concepts/statistics.md#segmentation-operation) by ths criterion is represented in the response;
  - key and link to the Data Model used in [`D-Segmentation`](/api/data-models/d-segmentation/index.md) to indicate the specific Criterion;
  - how the [Granularity](/api/concepts/statistics.md#segmentation-criteria) is indicated and what are the allowed values.
  
## List of defined Dimensions

* [*Device Base*](/api/dimensions/device-base.md)
* [*Space*](/api/dimensions/space.md)
* [*Time*](/api/dimensions/time.md)
* [*Motion Type*](/api/dimensions/motion-type.md)
* [*Spatial Granularity*](/api/dimensions/spatial-granularity.md)
* [*Airports*](/api/dimensions/airports.md)
* [*Flight Route*](/api/dimensions/flight-route.md)
* [*Flight Range*](/api/dimensions/flight-range.md)
