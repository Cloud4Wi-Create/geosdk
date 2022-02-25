# Read single Audience Analysis Resource


Endpoint to READ a single [*Audience Analysis*](/api/reference/resources/resources/user-created/audience-analysis.md) Resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/audiences/<AUDIENCE_ID>`
* **Path parameters:**
    *  **AUDIENCE_ID**: The ID of the specific *Audience Analysis* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/audience-analysis.md) field
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/audiences/AUDIENCE_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `AUDIENCE_ID` with a valid *audience Analysis* Resource ID.


## Successful Response

A Successful response returns the reuested *Audience Analysis* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Audience`](/api/reference/data-modelsata-models/resources/user-created/audience-analysis.md)





