# Read Hook Collection

Endpoint to READ the *Hook* Collection.

## Request

* **HTTP Method:** `GET`
* **Path:** `/project/hooks`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/c9bflkf6kx0g1de/read-collection.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```shell
curl --request GET \
  --url https://api.geouniq.com/v1/project/hooks \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

## Successful Response

A Successful response returns the created *Hook* Resource.

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](/api/reference/data-models/common/page.md) of [`Hook`](/api/reference/data-models/resources/user-created/hook.md) Objects