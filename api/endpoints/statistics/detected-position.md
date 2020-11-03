# Statistics on *Detected Position* Resources

Endpoint to obtain [Statistics](/api/concepts/statistics.md) on [*Detected Position*](api/resources/platform-created/device-related/detected-position.md) Resources.

## Available Aggregated Metrics

* **Count**: Indicates the number of Resources

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/detected-positions`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`DetectedPosition-StatisticInput`](/api/data-models/r-statistic-input/detected-position.md)
    
### Examlpe Request


```bash
curl --request POST \
  --url https://api.geouniq.com/v1/statistics/detected-positions \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"select":{"deviceBase":{"inside":{"deviceIds":["D1","D2","D3"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}},"time":{"inside":{"intervals":[{"from":{"relative":-100},"to":{"relative":0}}]}}},"segmentBy":{"deviceBase":{"inside":{"device":1}},"space":{"inside":{"geohash":8}},"time":{"inside":{"continuousInterval":{"count":1,"unit":"day"}}}},"compute":{"count":true},"filter":{"count":{"gt":0,"lt":10}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns a [`Page`](api/general-aspects/pagination.md) of [`DetectedPosition-StatisticOutput`](/api/data-models/r-statistic-output/detected-position.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](api/general-aspects/pagination.md#page-model)[`<DetectedPosition-StatisticOutput>`](/api/data-models/r-statistic-output/detected-position.md)





