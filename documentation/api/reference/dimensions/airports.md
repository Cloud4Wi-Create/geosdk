# Airports

The *Airports* Dimension refers to the set of World's Airports

 - **Resource types**: [*Flight*](/api/reference/resources/resources/platform-created/device-related/flight.md)
 - **Segment Data Model**: [`Airports-Segment`](/api/reference/data-modelsata-models/d-segment/airports.md)
 - **Selection/Segmentation Key**: `"airports"`
 - **Segmentation Data Model**: [`Airports-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/airports.md)

## Segmentation Criteria

The following segmentation criteria are defined.

### By Continent

Allows to create Segments with all the airports located in the same continent. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`Airports-Segment`](/api/reference/data-modelsata-models/d-segment/airports.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
continent  | `[String]` | Will contain only one `String` indicating the specific continent which the Segment refers to.

```json
{
    "continent": ["Europe"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Airports-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/airports.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
continent  | `Integer` | {`1`}

```json
{
    "continent": 1
}
```

#### Granularity

Allows only one value as granularity: each Segment refers to one specific contienent. 
The value of the `"continent"` field must be set equal to `1`. 

### By Country

Allows to create Segments with all the airports located in the same country. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`Airports-Segment`](/api/reference/data-modelsata-models/d-segment/airports.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
country  | `[String]` | Will contain only one `String` indicating the specific country which the Segment refers to.

```json
{
    "country": ["Italy"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Airports-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/airports.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
country  | `Integer` | {`1`}

```json
{
    "country": 1
}
```

#### Granularity

Allows only one value as granularity: each Segment refers to one specific country. 
The value of the `"country"` field must be set equal to `1`. 

### By City

Allows to create Segments with all the airports located in the same city. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`Airports-Segment`](/api/reference/data-modelsata-models/d-segment/airports.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
city  | `[String]` | Will contain only one `String` indicating the specific city which the Segment refers to.

```json
{
    "city": ["Rome"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Airports-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/airports.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
city  | `Integer` | {`1`}

```json
{
    "city": 1
}
```

#### Granularity

Allows only one value as granularity: each *Segment* refers to one specific city. 
The value of the `"city"` field must then be equal to `1`. 

### By Airport

Allows to create a Segments for each airport. 

#### Resulting Segments

Resulting Segments are indicated on the output side through a [`Airports-Segment`](/api/reference/data-modelsata-models/d-segment/airports.md) object formatted as in the following.

Name    | Type | Description
--------|----- |--------------
iataCode  | `[String]` | Will contain only one `String` indicating the [IATA code](http://www.iata.org/services/Pages/codes.aspx) of the specific airport which the Segment refers to.

```json
{
    "iataCode": ["FCO"]
}
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`Airports-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/airports.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
airport  | `Integer` | {`1`}

```json
{
    "airport": 1
}
```

#### Granularity

Allows only one value as granularity: each Segment refers to one specific airport. 
The value of the `"airport"` field must be set equal to `1`. 

