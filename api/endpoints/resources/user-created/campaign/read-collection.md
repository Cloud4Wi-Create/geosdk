# Read Campaign Resources Collection

Endpoint to READ the [*Campaign*](/api/resources/user-created/campaign.md) Resources collection.

## Request

* **HTTP Method:** `GET`
* **Path:** `/campaigns`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/campaigns \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns the *Campaign* Resources collection.

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](/api/data-models/common/page.md) of [`Campaign`](/api/data-models/resources/user-created/campaign.md) Objects