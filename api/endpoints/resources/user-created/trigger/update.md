# Update Trigger

Endpoint to UPDATE *Trigger* Resources.

## Request

* **HTTP Method:** `PATCH`
* **Path:** `/project/triggers/<TRIGGER_ID>`
* **Path parameters:**
    *  **TRIGGER_ID**: The ID of the specific *Trigger* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/trigger.md) field
* **Query String parameters:** None
* **Body:** [`Trigger`](/api/data-models/resources/user-created/trigger.md)
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/ctfkddu920u2i2w/update.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```
curl --request PATCH \
  --url https://api.geouniq.com/v1/project/triggers/TRIGGER_ID \
  --header 'authorization: Bearer ACCESS_TOKEN' \
  --header 'content-type: application/json' \
  --data '{"name":"My First Trigger after an update"}'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/auth.md).

> Make sure to substitute `TRIGGER_ID` with a valid *Trigger* Resource ID.


## Successful Response

A Successful response returns the updated *Trigger* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Trigger`](/api/data-models/resources/user-created/trigger.md)




