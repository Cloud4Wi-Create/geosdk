* [Documentation Home](../../../../../README.md)
    * [Web API](../../../../index.md)  
      * [Reference](../../../index.md)  
        * [Endpoints](../../index.md)
            * [Resources endpoints](../../index.md)
               * [Platform-created resources endpoints](../index.md)
                  * [POI endpoints](index.md)

# POI Selection Endpoint

Endpoint to get a [Selection](../../../../concepts/resource-selection.md) of 
[POI resources](../../../resources/platform-created/poi.md).

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/pois`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`POI-Selection`](../../../data-models/r-selection/poi.md)
    
### Example Request


```
TBD
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../general-aspects/pagination.md) of 
[`POI`](../../../data-models/resources/platform-created/poi.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../general-aspects/pagination.md)[`<POI>`](../../../data-models/resources/platform-created/poi.md)

### Example Response Body

```json
TBD
```



