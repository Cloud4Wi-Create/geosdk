* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Endpoints](../../index.md)
           * [User-created Resources Endpoints](../index.md)
              * [Trigger Endpoints](index.md)
           
           
# Read Trigger Collection

Endpoint to READ the *Trigger* Collection.

## Request

* **HTTP Method:** `GET`
* **Path:** `/triggers`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/triggers \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns the created *Trigger* Resource.

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../general-aspects/pagination.md#page-model) of [`Trigger`](../../../data-models/resources/user-created/trigger.md) Objects
