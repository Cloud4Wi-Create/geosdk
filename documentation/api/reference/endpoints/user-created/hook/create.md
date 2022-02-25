# Create Hook

Endpoint to CREATE *Hook* Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/project/hooks`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Hook`](/api/reference/data-models/resources/user-created/hook.md)
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/ly3u579mtktifxv/create.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```
curl --request POST \
  --url https://api.geouniq.com/v1/project/hooks \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"My First Hook","description":"A simple web hook","labels":["test"],"type":"web","web":{"url":"https://api.mydomain.com/geouniq/test"}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

## Successful Response

A Successful response returns the created *Hook* Resource.

* **HTTP Status Code**: 201
* **Paginated**: NO
* **Body**: [`Hook`](/api/reference/data-models/resources/user-created/hook.md)





