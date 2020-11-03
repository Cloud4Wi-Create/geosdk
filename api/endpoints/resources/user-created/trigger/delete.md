# Delete Trigger


Endpoint to DELETE *Trigger* Resources.

## Request

* **HTTP Method:** `DELETE`
* **Path:** `/project/triggers/<TRIGGER_ID>`
* **Path parameters:**
    * **TRIGGER_ID**. The Resource ID of the specific *Trigger*. 
* **Query String parameters:** None
* **Body:** None
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/4pphi7bh80hd5u9/delete.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```shell
curl --request DELETE \
  --url https://api.geouniq.com/v1/project/triggers/TRIGGER_ID \
  --header 'authorization: Bearer ACCESS_TOKEN'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns no content.

* **HTTP Status Code**: 204
* **Paginated**: NO
* **Body**: None



