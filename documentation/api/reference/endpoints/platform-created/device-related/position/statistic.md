* [Documentation Home](../../../../../../README.md)
    * [Web API](../../../../../index.md)  
      * [Reference](../../../../index.md)  
        * [Endpoints](../../../index.md)
           * [Platform-created resources endpoints](../../index.md)
              * [Device-related resources endpoints](../index.md)
                * [Position endpoints](index.md)
                
# Position Statistics Endpoint

Endpoint to get [Statistics](../../../../../concepts/statistics.md) 
for [Position](../../../../resources/platform-created/device-related/position.md) resources.

## Available Aggregated Metrics

* **Count**: Indicates the number of Resources

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/detected-positions`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Position-StatisticInput`](../../../../data-models/r-statistic-input/detected-position.md)
    
### Example Request


```bash
curl --request POST \
  --url https://api.geouniq.com/v1/statistics/detected-positions \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"select":{"deviceBase":{"inside":{"deviceIds":["D1","D2","D3"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}},"time":{"inside":{"intervals":[{"from":{"relative":-100},"to":{"relative":0}}]}}},"segmentBy":{"deviceBase":{"inside":{"device":1}},"space":{"inside":{"geohash":8}},"time":{"inside":{"continuousInterval":{"count":1,"unit":"day"}}}},"compute":{"count":true},"filter":{"count":{"gt":0,"lt":10}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../../general-aspects/pagination.md) of [`Position-StatisticOutput`](../../../../data-models/r-statistic-output/detected-position.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../../general-aspects/pagination.md#page-model)[`<Position-StatisticOutput>`](../../../../data-models/r-statistic-output/detected-position.md)





