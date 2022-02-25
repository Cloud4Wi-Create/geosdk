# AdministrativeArea-Segment

Data model used to indicate an [`AdministrativeArea`](/api/reference/dimensionsdimensions/administrative-area.md) Segment.

Name | Type | Allowed Values | Description
--------|--------|--------|--------
country | `String`  | Any valid [ISO 3166-1 alpha-2](https://www.iso.org/iso-3166-country-codes.html) country code | The [ISO 3166-1 alpha-2](https://www.iso.org/iso-3166-country-codes.html) code of the country of interest
area| `JSON` | Any valid JSON object according to the fields `"area.X"` listed in the following | A JSON object indicating the administrative area of interest within the indicated country
level   | `String` | The level of administrative area for which the selection is desired  | Any string value indicating a valid area level for the selected country
name    | `[String]` | Any string value | The names of the desired areas of the indicated level

## Input side

Used to indicate a [Selection Condition](/api/concepts/resource-selection.md#dimensional-selection-conditions) on the [*Administrative Area*](/api/reference/dimensionsdimensions/administrative-area.md) Dimension.

**Example Input Object**

```json
{
    "country" : "IT",
    "area":{
        "level":"regione",
        "name":["campania", "basilicata"]
    }
}
```

## Output side

Used to indicate which *Administrative Area* Segment a Resource Segment refers to when a Segmentation operation is requested on the *Administrative Area* Dimension (see [Segmentation](/api/concepts/statistics.md#segmentation-operation)).
Depending on the specific Segmentation Criterion, different fields will be provided, as detailed [here](/api/reference/dimensionsdimensions/administrative-area.md#segmentation-criteria).

