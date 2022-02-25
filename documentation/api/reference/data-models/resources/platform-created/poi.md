# POI

Data Model used to represent a [*POI*](/api/reference/resources/resources/platform-created/poi.md) Resource.

## Fileds Specification

Name | Type | Possible Values | Description 
--------|--------|--------|--------
id      |`String` | Any value | The Id of the POI
category|`String` | Any value | The category which the POI belongs to
brand   |`String` | Any value | The brand which the POI belongs to 
country |`String` | Any valid [ISO 3166-1 alpha-2](https://www.iso.org/iso-3166-country-codes.html) country code | The [ISO 3166-1 alpha-2](https://www.iso.org/iso-3166-country-codes.html) code of the country where the POI is loated
administrativeAreas |[`[AdministrativeArea]`](/api/reference/data-modelsata-models/common/administrative-area.md) | An [`AdministrativeArea` object](/api/reference/data-modelsata-models/common/administrative-area.md) for each different administrative area level of the specific country | The set of administrative areas which the POI belongs to


## Example POI Object

```json
{
  "id": "224981",
  "category": "CONCESSIONARI AUTO",
  "brand": "FCA",
  "country": "IT",
  "geo": {
    "lat": 42.854192554950714,
    "lng": 13.708475232124329
  },
  "administrativeAreas": [
    {
      "level": "Comune",
      "name": "Ascoli Piceno"
    },
    {
      "level": "Provincia",
      "name": "Ascoli Piceno"
    },
    {
      "level": "Regione",
      "name": "Marche"
    },
    {
      "level": "Area Nielsen",
      "name": "Centro"
    }
  ]
}
```