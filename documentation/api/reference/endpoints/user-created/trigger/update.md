* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Endpoints](../../index.md)
           * [User-created Resources Endpoints](../index.md)
              * [Trigger Endpoints](index.md)
           
# Update Trigger

Endpoint to UPDATE *Trigger* Resources.

## Request

* **HTTP Method:** `PATCH`
* **Path:** `/project/triggers/<TRIGGER_ID>`
* **Path parameters:**
    *  **TRIGGER_ID**: The ID of the specific *Trigger* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/trigger.md) field
* **Query String parameters:** None
* **Body:** [`Trigger`](../../../data-models/resources/user-created/trigger.md)
    
### Examlpe Request


```
curl --request PATCH \
  --url https://api.geouniq.com/v1/triggers/TRIGGER_ID \
  --header 'authorization: Bearer ACCESS_TOKEN' \
  --header 'content-type: application/json' \
  --data '{"status":"disabled","period":{"intervals":[{"from":{"absolute":"2021-01-01T00:00:00Z"},"to":{"absolute":"2021-02-01T00:00:00Z"}}]},"target":{"clientAppId":["A1","A2"]}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

> Make sure to substitute `TRIGGER_ID` with a valid *Trigger* Resource ID.


## Successful Response

A Successful response returns the updated *Trigger* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Trigger`](../../../data-models/resources/user-created/trigger.md)




