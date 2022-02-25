* [Documentation Home](../../../../../../README.md)
    * [Web API](../../../../../index.md)  
      * [Reference](../../../../index.md)  
        * [Endpoints](../../../index.md)
           * [Platform-created resources endpoints](../../index.md)
              * [Device-related resources endpoints](../index.md)
                * [Visit endpoints](index.md)
                 
# Visit Selection Endpoint

Endpoint to get a [Selection](../../../../../concepts/resource-selection.md) of 
[Visit resources](../../../../resources/platform-created/device-related/visit.md).

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/visits`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Visit-Selection`](../../../../data-models/r-selection/visit.md)
    
### Example Request

```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/visits \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"deviceBase":{"inside":{"deviceId":["D1"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":{"type":"Polygon","coordinates":[[[-10.0,-10.0],[10.0,-10.0],[10.0,10.0],[-10.0,10.0],[-10.0,-10.0]]]},"properties":null}}},"time":{"intersect":{"intervals":[{"from":{"absolute":"2016-01-01T00:00:00Z"},"to":{"absolute":"2016-01-02T00:00:00Z"}}]}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../../general-aspects/pagination.md) 
of [`Visit`](../../../../data-models/resources/platform-created/device-related/visit.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../../general-aspects/pagination.md)[`<Visit>`](../../../../data-models/resources/platform-created/device-related/visit.md)

### Example Response Body
    
```json
{
	"items": [{
		"device": {
			"id": "5832ed167e6b5e00017a4a3b"
		},
		"startedAt": "2017-08-28T16:20:00Z",
		"endedAt": "2017-08-28T17:20:00Z",
		"inProgress": false,
		"duration": 3600,
		"granularityLevel": "building",
		"geo": {
			"area": {
				"type": "Feature",
				"geometry": {
					"type": "Polygon",
					"coordinates": [
						[
							[10.396500, 43.723009],
							[43.722836, 43.723009],
							[43.722836, 10.396844],
							[10.396500, 10.396844],
							[10.396500, 43.723009]
						]
					]
				},
				"properties": {
					"geohashes": ["spz2sx9s"]
				}
			}
		},
		"ReferencePosition": {
			"Lat": 50.445718,
			"Lng": -3.560455
		}
	}],
	"paging": {
		"next": {
			"link": "https://api.geouniq.com/v1/selections/visits?limit=3&offset=Mw%3D%3D",
			"offset": "Mw=="
		}
	}
}
```



