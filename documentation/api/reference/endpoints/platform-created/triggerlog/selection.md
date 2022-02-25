* [Documentation Home](../../../../../README.md)
    * [Web API](../../../../index.md)  
      * [Reference](../../../index.md)  
        * [Endpoints](../../index.md)
            * [Resources endpoints](../../index.md)
               * [Platform-created resources endpoints](../index.md)
                  * [Trigger Log endpoints](index.md)
               
# Trigger Log Selection Endpoint

Endpoint to get a [Selection](../../../../concepts/resource-selection.md) of 
[Trigger Log resources](../../../resources/platform-created/triggerlog.md).

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/triggerlogs`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`TriggerLog-Selection`](../../../data-models/r-selection/triggerlog.md)
    
### Example Request


```
TBD
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../general-aspects/pagination.md) of 
[`TriggerLog`](../../../data-models/resources/platform-created/triggerlog.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../general-aspects/pagination.md)[`<TriggerLog>`](../../../data-models/resources/platform-created/triggerlog.md)

### Example Response Body

```json
TBD
```



