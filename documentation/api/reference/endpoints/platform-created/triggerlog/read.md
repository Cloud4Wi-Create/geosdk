* [Documentation Home](../../../../../README.md)
    * [Web API](../../../../index.md)  
      * [Reference](../../../index.md)  
        * [Endpoints](../../index.md)
            * [Resources endpoints](../index.md)
               * [Platform-created resources endpoints](index.md)

# Read Trigger Log

Endpoint to READ a single [*TriggerLog*](../../../resources/platform-created/triggerlog.md) resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/triggerlogs/<ID>`
* **Path parameters:** `<ID>`: indicates the ID of the TriggerLog resource 
* **Query String parameters:** None
    
### Example Request


```
curl --request GET \
  --url https://api.geouniq.com/v1/triggerlogs/<ID> \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json'
```
> Make sure to substitute `<ID>` with a valid TriggerLog ID
> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Triggerlog`](../../../data-models/resources/platform-created/triggerlog.md).

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`<Triggerlog>`](../../../data-models/resources/platform-created/triggerlog.md) object





