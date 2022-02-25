* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Endpoints](../../index.md)
           * [User-created Resources Endpoints](../index.md)
              * [Trigger Endpoints](index.md)
           
# Delete Trigger


Endpoint to DELETE *Trigger* Resources.

## Request

* **HTTP Method:** `DELETE`
* **Path:** `/triggers/<TRIGGER_ID>`
* **Path parameters:**
    * **TRIGGER_ID**. The Resource ID of the specific *Trigger*. 
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request


```shell
curl --request DELETE \
  --url https://api.geouniq.com/v1/triggers/TRIGGER_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns no content.

* **HTTP Status Code**: 204
* **Paginated**: NO
* **Body**: None



