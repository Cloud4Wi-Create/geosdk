* [Documentation Home](../../../../../README.md)
    * [Web API](../../../../index.md)  
      * [Reference](../../../index.md)  
        * [Endpoints](../../index.md)
            * [Resources endpoints](../../index.md)
               * [Platform-created resources endpoints](../index.md)
                  * [POI endpoints](index.md)
                  
# POI Statistics Endpoints

Endpoint to get [Statistics](../../../../concepts/statistics.md) 
for [POI](../../../resources/platform-created/poi.md) resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/pois`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`POI-StatisticInput`](../../../data-models/r-statistic-input/poi.md)
    
### Example Request


```
TBD
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../general-aspects/pagination.md) 
of [`POI-StatisticOutput`](../../../data-models/r-statistic-output/poi.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../general-aspects/pagination.md)[`<POI-StatisticOutput>`](../../../data-models/r-statistic-output/poi.md)


### Example Response Body

```json
TBD
```


