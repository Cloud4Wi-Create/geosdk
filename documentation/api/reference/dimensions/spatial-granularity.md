* [Documentation Home](../../../README.md)  
  * [Web API](../../index.md)  
    * [Reference](../index.md)
        * [Dimensions](index.md)

# Spatial Granularity

The *Spatial Granularity* Dimension refers to the extension of a geographic area considered to identify *Visits* and *Travels*.
A *Spatial Granularity* Segment can represent ANY combination of the values defined hereinafter.

 - **Segment Data Model**: `[String]`. An Array of `String` indicating one or more of the defined values
 - **Segmentation Data Model**: [`SpatialGranularity-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/spatial-granularity.md)

This *Dimension* contains the following finite number of values, expressed as `String`:

- `"continent"`
- `"country"`
- `"region"`
- `"metropolis"`
- `"city"`
- `"district"`
- `"neighbouroud"`
- `"building"`
- `"bestFit"`: special value that can be used as input when performing a [Resource Selection](/api/concepts/resource-selection.md) to indicate that the desired value for the *Spatial Granularity* is the one corresponding to the extension that fits best within the geographical area in which *Resources* are going to be selected

## Segmentation Criteria

The following segmentation criteria are defined.

### By Level

Allows to create a Segment for each specific level.

#### Resulting Segments

Resulting Segments are indicated through a `String` array in which only one `String` is present, which indicates the specific value of *Spatial Granularity* which the Segment refers to.

```json
["city"]
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`SpatialGranularity-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/spatial-granularity.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
level  | `Integer` | {`1`}

```json
{
    "level": 1
}
```

#### Granularity

Allows only one value as granularity: each *Segment* refers to one specific *Spatial Granularity Level*. 
The value of the `"level"` field must be set equal to `1`. 


