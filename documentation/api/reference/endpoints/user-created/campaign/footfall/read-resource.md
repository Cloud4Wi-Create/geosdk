# Read single Footfall Analysis Resource


Endpoint to READ a single [*Footfall Analysis*](/api/reference/resources/resources/user-created/campaign-footfall.md) Resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/campaigns/<CAMPAIGN_ID>/footfall/<FOOTFALL_ID>`
* **Path parameters:**
    *  **CAMPAIGN_ID**: The ID of the specific *Campaign* Resource which the *Footfall Analysis* Resource relates to, as provided in the [`"id"`](api/data-models/resources/user-created/campaign.md) field
    *  **FOOTFALL_ID**: The ID of the specific *Footfall Analysis* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/campaign-footfall.md) field

* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/campaign/CAMPAIGN_ID/footfall/FOOTFALL_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `CAMPAIGN_ID` with a valid *Campaign* Resource ID.

> Make sure to substitute `FOOTFALL_ID` with a valid *Footfall Analysis* Resource ID.


## Successful Response

A Successful response returns the reuested *Footfall Analysis* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`*FootfallAnalysis*`](/api/reference/data-modelsata-models/resources/user-created/campaign-footfall.md)





