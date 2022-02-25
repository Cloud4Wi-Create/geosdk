# Download results of an Audience Analysis


Endpoint to READ (download) the results of an [*Audience Analysis*](/api/reference/resources/resources/user-created/campaign-footfall.md) Resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/audiences/<AUDIENCE_ID>/results`
* **Path parameters:**
    *  **AUDIENCE_ID**: The ID of the specific *Audience Analysis* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/audience-analysis.md) field
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/audiences/AUDIENCE_ID/results \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `AUDIENCE_ID` with a valid *Audience Analysis* Resource ID.


## Successful Response

A Successful response returns a tar.gz file containing a set of csv files with the results of the analysis.

* **HTTP Status Code**: 200
* **Paginated**: NO




