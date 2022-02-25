# GuGeoJSON

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
type | `String` |    [`"Feature"`, `"FeatureCollection"`]  | 
geometry | `JSON` |  As defined by [GeoJSON](http://geojson.org/geojson-spec.html). `null` allowed. Only geometry of type `"Polygon"`     | 
properties | [`GuGeoJSONProperites`](#gu_geo_json_properties) | As indicated by [GeoJSON](http://geojson.org/geojson-spec.html). Mandatory. `null` is allowed | Used to indicate circles and/or areas through a geohash prefix. It is also used to indicate a *PlaceID* and/or a *PlaceCategory* for each Feature for segmentation purpose (see [`GuGeoJSONProperites`](#gu_geo_json_properties)) 

**Example Feature Object**

```json
{
    "type" : "Feature",
    "geometry" : { 
        "type": "Polygon", 
        "bbox": [-10.0, -10.0, 10.0, 10.0],
        "coordinates": [
			[
				[-10.0, -10.0],
				[10.0, -10.0],
				[10.0, 10.0],
				[-10.0, 10.0],
				[-10.0, -10.0]
			]
		]
    },
    "properties" : {
        "circles" : [{
            "center": {"lat": 10.0, "lng": 10.0},
            "radius": 100
        }],
        "geohashes": ["sxdbc"]
    }
}
``` 

**Example FeatureCollection Object**

```json
{
    "type" : "FeatureCollection",
    "features": [{
        "type" : "Feature",
        "geometry" : null,
        "properties" : {
            "circles" : [{
                "center": {"lat": 10.0, "lng": 10.0},
                "radius": 100
            }],
            "id": "store 1",
            "category": "store"
        }
    },{
        "type" : "Feature",
        "geometry" : null,
        "properties" : {
            "circles" : [{
                "center": {"lat": 10.1, "lng": 10.0},
                "radius": 100
            }],
            "id": "store 2",
            "category": "store"
        }
    }]
}
``` 

<a name="gu_geo_json_properties"></a>
## GuGeoJSONProperites
Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
circles | [`[Circle]`](#circle) |    Any number of valid `Circle` objects  | indicates one or more circles 
geohashes | `[String]` |    Any number of `String` values, each of which must be a valid gehash prefix  | indicates one or more areas through the related geohash prefix 
id | `String`| Any `String` with length <= 64 | A avlue of your choice. Must be unique for the set of provided Features. Necessary in case of a space segmentation using the ["ByPlaceId"](/api/reference/dimensionsdimensions/space.md#by-place-id) criterion
category | `String`| Any `String` with length <= 64 | A category of your choice. Necessary in case of a space segmentation using the ["ByPlaceCategory"](/api/reference/dimensionsdimensions/space.md#by-place-category) criterion

```json
 {
    "circles" : [{
        "center": {"lat": 10.0, "lng": 10.0},
        "radius": 100
    }],
    "geohashes": ["sxdbc"]
}
``` 

<a name="circle"></a>
## Circle

Name        |Type      | Allowed Values |Description
------------|----------|----------------|-----------
center | [`GeoPoint`](/api/reference/data-models/common/geo-point) |     | indicates the center of the circle
radius | `Number`| Any `0 < x < X_MAX ` | indicates the radius of the circle

```json
{
    "center": {"lat": 10.0, "lng": 10.0},
    "radius": 100
}
```

