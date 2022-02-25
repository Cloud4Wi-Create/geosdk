* [Documentation Home](../../../../README.md)  
  * [Web API](../../../index.md)  
    * [Reference](../../index.md)  
        * [Data Models](../index.md)

# D-Segment

Data Models used to represent a [Segment of a Dimension](../../../concepts/resource-definition.md#dimension-segment) *D*.
These Data Models are generically indicated as `D-Segment`, where *D* represents a generic Dimension.
These Data Models are used into [`G-D-SelectionOperation`](../g-d-selection-operation/index.md) Objects.

Specifically, they are used:

- **on the input side**: to indicate the specific *D* Segment which the [Dimensional Selection Operator](../../../concepts/resource-selection.md#dimensional-selection-conditions) has to be applied to.
    - [**when accessing Resources**](../../endpoints/endpoints/resources/index.md)
    - [**when accessing Statistics**](../../endpoints/endpoints/statistics/index.md)

- **on the output side**: to indicate the specific *D* Segment which the [Dimensional Selection Operator](../../../concepts/resource-selection.md#dimensional-selection-conditions) has been applied to when a [Segmentation operation](../../../concepts/statistics.md#segmentation) has been performed for a given [Dimensional Selection Condition](../../../concepts/resource-selection.md#dimensional-selection-conditions) on *D*.
    - [**when accessing Statistics**](../../reference/endpoints/endpoints/statistics/index.md)


Depending on the specific Dimension *D*, a different `D-Segment` Data Model is defined:

* [`Boolean-Segment`](../d-segment/boolean.md) 
* [`Integer-Segment`](../d-segment/integer.md) 
* [`Number-Segment`](../d-segment/number.md) 
* [`String-Segment`](../d-segment/string.md) 
* [`DeviceBase-Segment`](../d-segment/device-base.md) 
* [`Space-Segment`](../d-segment/space.md) 
* [`Time-Segment`](../d-segment/time.md) 
* [`SpatialGranularity-Segment`](../d-segment/spatial-granularity.md) 

