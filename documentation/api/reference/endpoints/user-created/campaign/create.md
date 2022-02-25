# Create Campaign

Endpoint to CREATE [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/campaign`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Campaign`](/api/reference/data-modelsata-models/resources/user-created/campaign.md)
    
### Examlpe Request

```
curl --request POST \
  --url https://api.geouniq.com/v1/campaigns \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"id":"campaign1","name":"my campaign","description":"my first campaign","type":"outOfHome","realTimeMonitoring":{"status":"enabled"},"period":{"start":"2020-05-01T00:00:00Z","end":"2020-05-10T00:00:00Z"},"targetPOIs":[{"custom":{"type":"FeatureCollection","features":[{"type":"Feature","properties":{"id":"Place 1","circles":[{"center":{"lat":10.0,"lng":10.0},"radius":15}]},"geometry":null}]},"standard":{"category":["category1"],"brand":["brand1"],"administrativeArea":[{"conutry":"IT","area":{"level":"Regione","name":["Campania","Basilicata"]}}]}}],"identifyExposed":{"time":{"inside":{"intervals":[{"from":{"absolute":"2020-05-01T00:00:00Z"},"to":{"absolute":"2020-05-10T00:00:00Z"}}]}},"space":{"inside":{"explicitArea":{"type":"FeatureCollection","features":[{"type":"Feature","properties":{"id":"Place 1"},"geometry":{"type":"Polygon","coordinates":[[[100.0,0.0],[101.0,0.0],[101.0,1.0],[100.0,1.0],[100.0,0.0]]]}},{"type":"Feature","properties":{"id":"Place 2"},"geometry":{"type":"Polygon","coordinates":[[[100.0,1.0],[101.0,1.0],[101.0,2.0],[100.0,2.0],[100.0,1.0]]]}}]}}},"spatialGranularity":{"inside":["exact"]}},"visitsHook":{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/visits"}},"exposedHook":{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/exposed"}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

## Successful Response

A Successful response returns the created *Campaign* Resource.

* **HTTP Status Code**: 201
* **Paginated**: NO
* **Body**: [`Campaign`](/api/reference/data-modelsata-models/resources/user-created/campaign.md)





