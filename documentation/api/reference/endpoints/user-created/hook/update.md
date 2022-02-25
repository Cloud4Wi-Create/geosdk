# Update Hook

Endpoint to UPDATE *Hook* Resources.

## Request

* **HTTP Method:** `PATCH`
* **Path:** `/project/triggers/<HOOK_ID>`
* **Path parameters:**
    *  **HOOK_ID**: The ID of the specific *Hook* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/hook.md) field
* **Query String parameters:** None
* **Body:** [`Hook`](/api/reference/data-models/resources/user-created/hook.md)
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/ctfkddu920u2i2w/update.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```
curl --request PATCH \
  --url https://api.geouniq.com/v1/project/triggers/HOOK_ID \
  --header 'authorization: Bearer ACCESS_TOKEN' \
  --header 'content-type: application/json' \
  --data '{"name":"My First Hook after an update"}'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `HOOK_ID` with a valid *Hook* Resource ID.


## Successful Response

A Successful response returns the updated *Hook* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Hook`](/api/reference/data-models/resources/user-created/hook.md)




