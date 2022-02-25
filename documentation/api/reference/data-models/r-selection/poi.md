# POI-Segment

Name        |Type    | Allowed values | Description  
------------|----------|------------|----------
id      | `[String]` | Any valid POI ID | The set of IDs of the POI desired in the selection
category| `[String]` | Any string value | The set of desired categories 
brand   | `[String]` | Any string value | The set of desired brands
administrativeArea | [`[AdministrativeArea]`](/api/reference/data-modelsata-models/d-segment/administrative-area.md) | Any valid [`AdministrativeArea-Segement`](/api/reference/data-modelsata-models/d-segment/administrative-area.md). Only one element currently supported | The set of desired administrative areas 

```json
{
    "category":["category1"],
    "brand":["brand1"],
    "administrativeArea":[{
	    "conutry":"IT",
	    "area":{
		    "level":"Regione",
		    "name":["Campania", "Basilicata"]
	    }
    }]
}
```

