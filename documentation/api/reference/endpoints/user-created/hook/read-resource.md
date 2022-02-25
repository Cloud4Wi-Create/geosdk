# Read single Hook


Endpoint to READ a single *Hook* Resource.

## Request

* **HTTP Method:** `GET`
* **Path:** `/project/hooks/<HOOK_ID>`
* **Path parameters:**
    *  **HOOK_ID**: The ID of the specific *Hook* Resource, as provided in the [`"id"`](api/data-models/resources/user-created/hook.md) field
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/6bcd626bdxpq2xh/read-resource.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```shell
curl --request GET \
  --url https://api.geouniq.com/v1/project/hooks/HOOK_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `ACCESS_TOKEN` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

> Make sure to substitute `HOOK_ID` with a valid *Hook* Resource ID.


## Successful Response

A Successful response returns the reuested *Hook* Resource.

* **HTTP Status Code**: 200
* **Paginated**: NO
* **Body**: [`Hook`](/api/reference/data-models/resources/user-created/hook.md)





