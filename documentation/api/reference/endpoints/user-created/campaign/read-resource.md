# Read single Campaign Resource


Endpoint to READ a single [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) Resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/campaigns/<CAMPAIGN_ID>`
* **Path parameters:**
    *  **CAMPAIGN_ID**: The ID of the specific *Campaign* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/campaign.md) field
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/campaign/CAMPAIGN_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `CAMPAIGN_ID` with a valid *Campaign* Resource ID.


## Successful Response

A Successful response returns the reuested *Campaign* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Campaign`](/api/reference/data-modelsata-models/resources/user-created/campaign.md)





