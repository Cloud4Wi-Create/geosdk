# Read Trigger Log

Endpoint to READ [*Triggerlog*](api/resources/platform-created/triggerlog.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/triggerlog`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Triggerlog-Segment`](/api/data-models/r-segment/triggerlog.md)
    
### Examlpe Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/triggerlogs \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"time":{"inside":{"intervals":[{"from":{"absolute":"2016-01-01T00:00:00Z"},"to":{"absolute":"2016-01-02T00:00:00Z"}}]}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns a [`Page`](api/general-aspects/pagination.md) of [`Triggerlog`](/api/data-models/resources/platform-created/triggerlog.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](api/general-aspects/pagination.md#page-model)[`<Triggerlog>`](/api/data-models/resources/platform-created/triggerlog.md)





