# Read Footfall Analysis Resources Collection of a specific Campaign

Endpoint to READ the [*Footfall Analysis*](/api/reference/resources/resources/user-created/campaign-footfall.md) Resources collection related to a single [*Campaign*](/api/reference/resources/resources/user-created/campaign.md).

## Request

* **HTTP Method:** `GET`
* **Path:** `/campaigns/<CAMPAIGN_ID>`
* **Path parameters:**
    * **CAMPAIGN_ID**: The ID of the specific *Campaign* Resource whose related *Footfall Analysis* are requested
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/campaigns/<CAMPAIGN_ID> \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `<CAMPAIGN_ID>` with a valid *Campaign* Resource ID.

## Successful Response

A Successful response returns the *Footfall Analysis* Resources collection.

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](/api/reference/data-models/common/page.md) of [`FootfallAnalysis`](/api/reference/data-modelsata-models/resources/user-created/campaign-footfall.md) Objects



