* [Documentation Home](../../../../../../README.md)
    * [Web API](../../../../../index.md)  
      * [Reference](../../../../index.md)  
        * [Endpoints](../../../index.md)
           * [Platform-created resources endpoints](../../index.md)
                * [Device-related resources endpoints](../index.md)
                    * [Home Location endpoints](index.md)
                    
# Statistics on Home Location Resources

Endpoint to obtain [Statistics](../../../../../concepts/statistics.md) on 
[Home Location](../../../../resources/platform-created/device-related/home-location.md) resources.

## Available Aggregated Metrics

* **Count**: Indicates the number of Resources

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/homes`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`HomeLocation-StatisticInput`](../../../../data-models/r-statistic-input/home-location.md)
    
### Example Request


```bash
curl --request POST \
  --url https://api.geouniq.com/v1/statistics/homes \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"select":{"deviceBase":{"inside":{"deviceIds":["D1","D2","D3"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":null,"properties":{"circles":[{"center":{"lat":10.0,"lng":10.0},"radius":100}]}}}}},"segmentBy":{"deviceBase":{"inside":{"device":1}},"space":{"inside":{"geohash":8}}},"compute":{"count":true}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../../general-aspects/pagination.md) of 
[`HomeLocation-StatisticOutput`](../../../../data-models/r-statistic-output/home-location.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../../general-aspects/pagination.md)[`<HomeLocation-StatisticOutput>`](../../../../data-models/r-statistic-output/home-location.md)





