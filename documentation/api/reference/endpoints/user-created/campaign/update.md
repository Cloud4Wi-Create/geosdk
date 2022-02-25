# Update Campaign

Endpoint to UPDATE *Campaign* Resources.

## Request

* **HTTP Method:** `PATCH`
* **Path:** `/campaign/<CAMPAIGN_ID>`
* **Path parameters:**
    *  **CAMPAIGN_ID**: The ID of the specific *Campaign* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/campaign.md) field
* **Query String parameters:** None
* **Body:** [`Campaign`](/api/reference/data-modelsata-models/resources/user-created/campaign.md)
    
### Examlpe Request


```
curl --request PATCH \
  --url https://api.geouniq.com/v1/campaign/CAMPAIGN_ID \
  --header 'authorization: Bearer ACCESS_TOKEN' \
  --header 'content-type: application/json' \
  --data '{{"realTimeMonitoring":{"status":"enabled"},"targetPOIs":[{"custom":{"type":"FeatureCollection","features":[{"type":"Feature","properties":{"id":"Place 1","circles":[{"center":{"lat":10.0,"lng":10.0},"radius":15}]},"geometry":null}]},"standard":{"category":["category1"],"brand":["brand1"],"administrativeArea":[{"conutry":"IT","area":{"level":"Regione","name":["Campania","Basilicata"]}}]}}]}}'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `CAMPAIGN_ID` with a valid *Campaign* Resource ID.


## Successful Response

A Successful response returns the updated *Campaign* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Hook`](/api/reference/data-models/resources/user-created/saved-area.md)




