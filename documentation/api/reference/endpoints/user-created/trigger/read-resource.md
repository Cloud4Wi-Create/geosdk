* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Endpoints](../../index.md)
           * [User-created Resources Endpoints](../index.md)
              * [Trigger Endpoints](index.md)

# Read single Trigger


Endpoint to READ a single *Trigger* Resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/triggers/<TRIGGER_ID>`
* **Path parameters:**
    *  **TRIGGER_ID**: The ID of the specific *Trigger* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/trigger.md) field
* **Query String parameters:** None
* **Body:** None
    
### Example Request


```shell
curl --request GET \
  --url https://api.geouniq.com/v1/triggers/TRIGGER_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

> Make sure to substitute `TRIGGER_ID` with a valid *Trigger* Resource ID.


## Successful Response

A Successful response returns the reuested *Trigger* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Trigger`](../../../data-models/resources/user-created/trigger.md)





