# Administrative Area

The *Administrative Area* Dimension refers to geo-administrative areas.
An *Administrative Area* Segment can represent ANY sub-set of all the administrative areas of the same level within a country

 - **Resource types**: [POI](/api/reference/resources/resources/platform-created/poi.md)
 - **Segment Data Model**: [`AdministrativeArea-Segment`](/api/reference/data-modelsata-models/d-segment/administrative-area.md)
 - **Segmentation Data Model**: [`AdministrativeArea-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/administrative-area.md)

## Segmentation Criteria

The following segmentation criteria are defined for *Administrative Area*.

### By Name

Allows to segment an *Administrative Area* Segment in (sub-)Segments of one *element* each according to the name of each specific area. 

#### Resulting Segments

Resulting Segments are indicated on the output side through an [`AdministrativeArea-Segment`](/api/reference/data-modelsata-models/d-segment/administrative-area.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
level  | `String` | Will contain the the level of the administrative area which the segment refers to.
name  | `[String]` | Will Contain only one value corresponding to the name of the administrative area which the segment refers to.


```json
{
    "level": "regione",
    "name": "piemonte"
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using an [`AdministrativeArea-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/administrative-area.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
name  | `Integer` | {`1`}

```json
{
    "name": 1
}
```

#### Granularity

Allows only one value as granularity: each *Administrative Area* Segment refers to a specific *Administrative Area*. 
The value of the `"name"` field must be set equal to `1`. 