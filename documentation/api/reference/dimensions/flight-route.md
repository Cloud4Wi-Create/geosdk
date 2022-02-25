# Flight Route

The *Flight Route* Dimension refers to the origin destination airports pair of a flight.

 - **Resource types**: [*Flight*](/api/reference/resources/resources/platform-created/device-related/flight.md)
 - **Segment Data Model**: [`FlightRoute-Segment`](/api/reference/data-modelsata-models/d-segment/flight-route.md)
 - **Selection/Segmentation Key**: `"flightRoute"`
 - **Segmentation Data Model**: [`FlightRoute-Segmentation`](/api/reference/data-models/d-segmentation/flight-route.md)


## Segmentation Criteria

The following segmentation criteria are defined.

### By Route

Allows to create a Segment for each origin-destination airports pair. 

#### Resulting Segments

Resulting Segments are indicated through a [`FlightRoute-Segment`](/api/reference/data-modelsata-models/d-segment/flight-route.md) containing only one [`Route`](/api/reference/data-modelsata-models/d-segment/flight-route.md#route) object.

```json
[{
	"departure": "FCO",
	"arrival": "JFK"
}]
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`FlightRange-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/flight-range.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
route  | `Integer` | {`1`}

```json
{
    "range": 1
}
```

#### Granularity

Allows only one value as granularity: each Segment refers to one specific route. 
The value of the `"route"` field must be set equal to `1`. 

### By Roundtrip Route

Allows to create a Segment for each airports pair, considering both directions of the flight. 

#### Resulting Segments

Resulting Segments are indicated through a [`FlightRoute-Segment`](/api/reference/data-modelsata-models/d-segment/flight-route.md) containing two [`Route`](/api/reference/data-modelsata-models/d-segment/flight-route.md#route) objects.

```json
[{
	"departure": "FCO",
	"arrival": "JFK"
},
{
	"departure": "JFK",
	"arrival": "FCO"
}]
```

#### Mapping on the Segmentation object

This Criterion can be indicated using a [`FlightRange-Segmentation`](/api/reference/data-modelsata-models/d-segmentation/flight-range.md) object formatted as in the following:

Name    | Type | Allowe Values
--------|----- |--------------
roundtrip  | `Integer` | {`1`}

```json
{
    "roundtrip": 1
}
```

#### Granularity

Allows only one value as granularity: each Segment refers to one specific route. 
The value of the `"roundtrip"` field must be set equal to `1`. 


