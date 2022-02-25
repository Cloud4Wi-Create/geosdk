# Flight Range

The *Flight Range* Dimension refers to the the range of a flight.

 - **Resource types**: [*Flight*](/api/reference/resources/resources/platform-created/device-related/flight.md)
 - **Segment Data Model**: `[String]`.  An Array of `String` indicating one or more of the defined values
 - **Selection/Segmentation Key**: `"flightRange"`
 - **Segmentation Data Model**: [`FlightRange-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/flight-range.md)

The following values are defined: 

- `"interconntinental"`
- `"international"`
- `"national"`

## Segmentation Criteria

The following segmentation criteria are defined.

### By Range

Allows to create a Segment for each defined flight range value. 

#### Resulting Segments

Resulting Segments are indicated through a `FlightRange-Segment` (i.e., a `String` Array) with only one `String` indicating the specific value.

```json
["international"]
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`FlightRange-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/flight-range.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
range  | `Integer` | {`1`}

```json
{
    "range": 1
}
```

#### Granularity

Allows only one value as granularity: each Segment refers to one specific contienent. 
The value of the `"range"` field must be set equal to `1`. 


