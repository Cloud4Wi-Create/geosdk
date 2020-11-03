# SavedArea

Data Model used to represent a [*Saved Area*](/api/resources/user-created/saved-area.md) Resource.

## Fields Specificcation

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
id | `String` | Forbidden - Output Only | N.A. | The Resource ID.
createdAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name | `String` | Optional | Any `String` of length lower than 32 characters | A name for the *Saved Area* useful to recall *Saved Area* Resources in a [`SavedArea-Segment`](/api/data-models/d-segment/space.md#saved-area-segment)
description | `String` | Optional | Any `String` of length lower than 128 characters | A description for the *Saved Area*. It cannot be used to recall the *Saved Area* in a [`SavedArea-Segment`](/api/data-models/d-segment/space.md#saved-area-segment).
labels | `[String]` | Optional | At most 10 `String` elements of length lower than 16 characters | A set of labels useful to recall *Saved Area* Resources in a [`SavedArea-Segment`](/api/data-models/d-segment/space.md#saved-area-segment)
geo | [`GuGeoJSON`](/api/data-models/common/gu-geo-json.md) | Mandatory | Any valid `GuGeoJSON` | The representation of the geographical area



## Example Object


```json
{
	"id": "587f61becb4bad726ccdc8ae",
	"createdAt": "2017-01-18T13:49:00Z",
	"name": "London",
	"description": "A simple mapping of tThe City of London",
	"labels": ["london", "city", "test"],
	"geo": {
		"type": "Feature",
		"geometry": {
			"type": "Polygon",
			"coordinates": [
				[
					[-0.11844635009765626,
						51.491751537714705
					],
					[-0.11844635009765626,
						51.53480425870272
					],
					[-0.06574630737304688,
						51.53480425870272
					],
					[-0.06574630737304688,
						51.491751537714705
					],
					[-0.11844635009765626,
						51.491751537714705
					]
				]
			]
		},
		"properties": null
	}
}
```