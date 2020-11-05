# Save geographical areas that can be recalled in requests

GeoUniq Analytics allows to create [*Saved Area*](/api/resources/user-created/saved-area.md) Resources that represents simple geographical areas.
A *Saved Area* can be recalled when performing requests to the Web API to indicate a specific area.
Indeed, when a request has to be referred to a specific area, for example to analyze *Visits* to a specific location, or to set *Triggers* like [geofences](/use-cases/geofence.md), one may indicate the area of interest by referring to a *Saved Area* instead of explicitely provide it in the request.
This is particularly useful for *Triggers*.
In fact, if several *Triggers* refer to a specific *Saved Area*, one could change the actual geographical area by updating the related *Saved Area* Resource without modifying *Triggers*.

*Saved Area* Resources can be created through the related [endpoint](/api/endpoints/resources/user-created/saved-area/create.md).
The actual geographical area is indicated through a [`GuGeoJSON`](/api/data-models/common/gu-geo-json.md) Object that is an extension of a standard [GeoJSON](http://geojson.org/geojson-spec.html) that allows to indicate circles in addition to polygons.

The following JSON object correspond to a `GuGeoJSON` representing a circle with a radius of 100 meters

```json
{
    "type" : "Feature",
    "geometry" : null,
    "properties" : {
        "circles" : [{
            "center": {"lat": 10.0, "lng": 10.0},
            "radius": 100
        }]
    }
}
```

The following request allows to create a *Saved Area* by posting a [`SavedArea`](/api/data-models/resources/user-created/saved-area.md) Object that indicates the circle above, a name, a description, and a set of labels that can be used to recall it in requests.

```shell
curl --request POST \
  --url https://api.geouniq.com/v1/project/saved-areas \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"sample area","labels":["test"],"geo":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}'
```

> Make sure to change `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/guide/obtain-access-token.md).

Once a *Saved Area* has been created, you can recall it within a [`Space-Segment`](/api/data-models/d-segment/space.md#saved-area-segment), like in the following.

```json
{
    "savedAreas": {
        "id": ["area1", "area2"],
        "name": ["Rome","Milan"],
        "labels": ["Rome", "Italy", "City"]
    }
}
```

*Saved Areas* can be recalled through:

* Their Resource IDs ([`"id"` field](/api/data-models/resources/user-created/saved-area.md))
* Their name ([`"name"` field](/api/data-models/resources/user-created/saved-area.md))
* Their labels ([`"labels"` field](/api/data-models/resources/user-created/saved-area.md))
