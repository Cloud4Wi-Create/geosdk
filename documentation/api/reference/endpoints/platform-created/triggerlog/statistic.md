* [Documentation Home](../../../../../README.md)
    * [Web API](../../../../index.md)  
      * [Reference](../../../index.md)  
        * [Endpoints](../../index.md)
            * [Resources endpoints](../../index.md)
               * [Platform-created resources endpoints](../index.md)
                  * [Trigger Log endpoints](index.md)
                  
# Trigger Log Statistics Endpoints

Endpoint to get [Statistics](../../../../concepts/statistics.md) 
for [Trigger Log](../../../resources/platform-created/triggerlog.md) resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/triggerlogs`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`TriggerLog-StatisticInput`](../../../data-models/r-statistic-input/triggerlog.md)
    
### Example Request


```
TBD
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../general-aspects/pagination.md) 
of [`TriggerLog-StatisticOutput`](../../../data-models/r-statistic-output/triggerlogs.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../general-aspects/pagination.md)[`<TriggerLog-StatisticOutput>`](../../../data-models/r-statistic-output/triggerlogs.md)


### Example Response Body

```json
TBD
```


