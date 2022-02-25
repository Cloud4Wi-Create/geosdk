#  Motion Type

The *Motion Type* Dimension refers to different ways of a User to move.
A *Motion Type* Segment can represent ANY possible combination of the types of motion defined hereinafter.

 - **Resource types**: [*Activity*](/api/reference/resources/resources/platform-created/device-related/activity.md)
 - **Segment Data Model**: `[String]`. An Array of `String` indicating one or more of the defined values
 - **Segment/Segmentation Key**: `"motionType"`
 - **Segmentation Data Model**: [`MotionType-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/motion-type.md)

This *Dimension* contains the following finite number of values, expressed as `String` values:

- `"stationary"` 
- `"walking"`
- `"running"`
- `"cycling"`
- `"automotive"`
- `"flying"`

## Segmentation Criteria

The following segmentation criteria are defined.

### By Type

Allows to create a *Motion Type* Segment for each of the defined values.

#### Resulting Segments

Resulting Segments are indicated through a `String` array in which only one `String` is present, which indicates the specific value of *Motion Type* which the Segment refers to.

```json
["walking"]
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`MotionType-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/motion-type.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
type  | `Integer` | {`1`}

```json
{
    "type": 1
}
```

#### Granularity

Allows only one value as granularity: each *Segment* refers to one specific value. 
The value of the `"type"` field must be set equal to `1`. 
