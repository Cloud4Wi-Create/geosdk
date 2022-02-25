# FlightRoute-Segment


Data model to indicate a Segment of [*Flight Route*](/api/reference/dimensionsdimensions/flight-route.md).
It is an array of `Route` Object.

## Route

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
departure | `String` | ANY valid [IATA code](http://www.iata.org/services/Pages/codes.aspx)    | A routes with departure airport indicated by the provided IATA code.
arrival | `String` | ANY valid [IATA code](http://www.iata.org/services/Pages/codes.aspx)   | A routes with arrival airport indicated by the provided IATA code.

```json
[{
	"departure": "FCO"
	"arrival": "FCO"
}]
```
