# Statistics on *Work Location* Resources

Endpoint to obtain [Statistics](/api/concepts/statistics.md) on [*Work Location*](api/resources/platform-created/device-related/work-location.md) Resources.

## Available Aggregated Metrics

* **Count**: Indicates the number of Resources

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/works`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`WorkLocation-StatisticInput`](/api/data-models/r-statistic-input/work-location.md)
    
### Examlpe Request


```bash
curl --request POST \
  --url https://api.geouniq.com/v1/statistics/works \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"select":{"deviceBase":{"inside":{"deviceIds":["D1","D2","D3"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}}},"segmentBy":{"deviceBase":{"inside":{"device":1}},"space":{"inside":{"geohash":8}}},"compute":{"count":true}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns a [`Page`](api/general-aspects/pagination.md) of [`WorkLocation-StatisticOutput`](/api/data-models/r-statistic-output/work-location.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](api/general-aspects/pagination.md#page-model)[`<WorkLocation-StatisticOutput>`](/api/data-models/r-statistic-output/work-location.md)