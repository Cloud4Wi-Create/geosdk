* [Documentation Home](../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Endpoints](../../index.md)
           * [User-created Resources Endpoints](../index.md)
              * [Trigger Endpoints](index.md)
           
# Create Trigger

Endpoint to CREATE *Trigger* Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/triggers`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Trigger`](../../../data-models/resources/user-created/trigger.md)
    
### Examlpe Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"My Trigger","description":"My first Trigger","labels":["test"],"status":"enabled","period":{"intervals":[{"from":{"absolute":"2021-01-01T00:00:00Z"},"to":{"absolute":"2021-02-01T00:00:00Z"}}]},"target":{"clientAppId":["A1","A2"]},"hooks":[{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/triggers"}}],"event":{"type":"geofence","geofence":{"transitions":[{"type":"enter","enabled":true},{"type":"exit","enabled":true}],"area":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}},"dwellTime":300}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns the created *Trigger* Resource.

* **HTTP Status Code**: 201
* **Paginated**: NO
* **Body**: [`Trigger`](../../../data-models/resources/user-created/trigger.md)





