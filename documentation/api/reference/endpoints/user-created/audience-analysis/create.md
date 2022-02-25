# Create Audience Analysis

Endpoint to CREATE [*Audience Analysis*](../../../../resources/user-created/audience-analysis.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/audiences`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`AudienceAnalysis`](../../../../data-models/resources/user-created/audience-analysis.md)
    
### Examlpe Request

```
curl --request POST \
  --url https://api.geouniq.com/v1/audiences/analysis \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"my audience analysis","description":"my first audience analysis","labels":["test","geoBehavioural"],"hook":{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/analysis"}},"type":"geoBehavioural","geoBehavioural":{"criteria":["live","work","passedThrough"],"pois":{"standard":{"category":["category1"],"brand":["brand1"],"administrativeArea":[{"conutry":"IT","area":{"level":"Regione","name":["Campania","Basilicata"]}}]},"custom":{"type":"FeatureCollection","features":[{"type":"Feature","properties":{"id":"Place 1","circles":[{"center":{"lat":10.0,"lng":10.0},"radius":15}]},"geometry":null}]}},"period":{"intervals":[{"from":{"absolute":"2020-01-01T00:00:00Z"},"to":{"absolute":"2020-04-01T00:00:00Z"}}]},"reachLevel":2}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../../general-aspects/auth.md).

## Successful Response

A Successful response returns the created *Audience* Resource.

* **HTTP Status Code**: 201
* **Paginated**: NO
* **Body**: [`AudienceAnalysis`](../../../../data-models/resources/user-created/audience-analysis.md)





