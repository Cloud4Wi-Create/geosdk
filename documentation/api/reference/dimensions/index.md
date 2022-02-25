* [Documentation Home](../../../README.md)  
  * [Web API](../../index.md)  
    * [Reference](../index.md)
    
# Dimensions

This section lists the various [*dimensions*](../../concepts/resource-definition.md#dimensions) 
defined by this API.

The section is divided in several subsections, one for each dimension.
Each subsection contains the following.

- **Segment Data Model**. 
Data model used to indicate a 
[*D* Segment](../../concepts/resource-definition.md#segment-of-a-dimension). 
Such data models are generically indicated as [`D-Segment`](../../reference/data-models/d-segment/index.md) for a generic Dimension *D*.
- **Segmentation Data Model**. 
Data model used to indicate a 
[*D* Segmentation](../../concepts/statistics.md#segmentation-operation). 
Such Data Models are generically indicates as [`D-Segmentation`](../../reference/data-models/d-segmentation/index.md).
- **Segmentation Criteria**. 
The [Segmentation Criteria](../../concepts/statistics.md#segmentation-criteria) 
defined for *D* and, for each of them:
  - a description of the criterion;
  - how the specific criterion is indicated in the 
  [`D-Segmentation`](../../reference/data-models/d-segmentation/index.md) object;
  - how a [*D* Segment](../../concepts/resource-definition.md#segment-of-a-dimension) 
  deriving from a [Segmentation](/api/concepts/statistics.md#segmentation-operation) 
  with the specific criterion is represented in the response;
  - how the [granularity](../../concepts/statistics.md#segmentation-criteria) 
  is indicated and what are the allowed values.
  
## List of defined Dimensions

* [*Device Base*](device-base.md)
* [*Space*](space.md)
* [*Time*](time.md)
* [*Spatial Granularity*](spatial-granularity.md)

