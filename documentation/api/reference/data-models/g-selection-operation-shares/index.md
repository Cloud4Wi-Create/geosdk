# G-SelectionOperationsShares

Data models used to indicate the [Metric Shares that come from any Dimensional Selection Condition](/api/concepts/statistics.md#metric-shares-of-an-r-segment) among those allowed by a specific Geometry *G*.

These data models are common to any type *R*, any Aggregated Metric *M*, and any Dimension *D*, whilst only depends on the specific Geometry *G* assumed by *R* on *D*.
These data models are used within [`R-Shares`](/api/reference/data-modelsata-models/r-shares/index.md) Objects and are always associated to a Dimension *D*.

These Data Models are used:

- **on the input side**: Never
- **on the output side**
    - [**when accessing Statistics**](/api/reference/endpoints/endpoints/statistics/index.md): to provide [Condition Shares](/api/concepts/statistics.md#metric-shares-of-an-r-segment) related to a [Dimensional Selection Operation](/api/concepts/resource-selection.md#dimensional-selection-operation) and [Dimensional Segmentation](/api/concepts/statistics.md#dimensional-segmentation) for a specific Operator *OP* and Dimension *D*.



A generic `G-SelectionOperationsShares` has a field for each [Dimensional Selection Operator](/api/concepts/resource-selection.md#dimensional-selection-operation) *OP* allowed by *G*, whose key is defined by [the specific Operator](/api/reference/configurations%20and%20operators.md) and whose type is always [`OverallAndSelection-Shares`](/api/reference/data-models/common/overall-and-selection-shares.md).

Each field is present only if, for the specific Dimension *D* which the object is associated to:
- either a [Dimensional Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) using the Operator *OP* has been requested (through the [`G-D-SelectionOperation`](/api/reference/data-modelsata-models/g-d-selection-operation/index.md) Object associated to the specific Dimension *D* within the [`R-Segment`](/api/reference/data-modelsata-models/r-segment/index.md) Object provided as input).
- or a [Dimensional Segmentation](/api/concepts/statistics.md#dimensional-segmentation) using the Operator *OP* has been requested (through the [`G-D-Segmentation`](/api/reference/data-modelsata-models/g-d-selection-operation/index.md) Object associated to the specific Dimension *D* within the [`R-Segmentation`](/api/reference/data-modelsata-models/r-segment/index.md) Object provided as input).


According to the [specific Geometry *G*](/api/reference/configurations%20and%20operators.md), the following `G-SelectionOperationsShares` Data Models are defined:

* [`Point-SelectionOperationsShares`](api/data-models/g-selection-operation-shares/point.md)
* [`Multipoint-SelectionOperationsShares`](api/data-models/g-selection-operation-shares/point.md)
* [`Sequence-SelectionOperationsShares`](api/data-models/g-selection-operation-shares/point.md)
* [`Interval-SelectionOperationsShares`](api/data-models/g-selection-operation-shares/point.md)
