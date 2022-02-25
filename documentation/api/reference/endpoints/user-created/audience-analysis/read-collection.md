# Read Audience Analysis Resources Collection

Endpoint to READ the [*Audience Analysis*](/api/reference/resources/resources/user-created/audience-analysis.md) Resources collection.

## Request

* **HTTP Method:** `GET`
* **Path:** `/audiences`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/audiences \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

## Successful Response

A Successful response returns the *Audience Analysis* Resources collection.

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](/api/reference/data-models/common/page.md) of [`AudienceAnalysis`](/api/reference/data-modelsata-models/resources/user-created/audience-analysis.md) Objects
