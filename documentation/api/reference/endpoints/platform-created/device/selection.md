* [Documentation Home](../../../../../README.md)
    * [Web API](../../../../index.md)  
      * [Reference](../../../index.md)  
        * [Endpoints](../../index.md)
            * [Resources endpoints](../../index.md)
               * [Platform-created resources endpoints](../index.md)
                  * [Device endpoints](index.md)
               
# Device Selection Endpoints

Endpoint to get a [Selection](../../../../concepts/resource-selection.md) of 
[Device resources](../../../resources/platform-created/device.md).

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/devices`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Device-Selection`](../../../data-models/r-selection/device.md)
    
### Example Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/devices \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"deviceBase":{"inside":{"clientAppId":["A1"]}},"time":{"inside":{"intervals":[{"from":{"absolute":"2016-01-01T00:00:00Z"},"to":{"absolute":"2016-01-02T00:00:00Z"}}]}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../general-aspects/pagination.md) of 
[`Device`](../../../data-models/resources/platform-created/device.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../general-aspects/pagination.md)[`<Device>`](../../../data-models/resources/platform-created/device.md)

### Example Response Body

```json
{
    "items": [
        {
            "id": "58bdc05e111eb2000154fa34",
            "createdAt": "2017-03-06T20:02:38Z",
            "os": {
                "name": "ios",
                "version": "10.3.3"
            },
            "clientApp": {
                "id": "587df1a7366c5d000124caf1",
                "name": "com.example.ios"
            }
        },
        {
            "id": "593d148ca4338300011879ee",
            "createdAt": "2017-06-11T09:59:40Z",
            "os": {
                "name": "android",
                "version": "6.0.1"
            },
            "clientApp": {
                "id": "59289564ed4b530001ad6ecb",
                "name": "com.example.android"
            }
        }
    ],
    "paging": {
        "next": {
            "link": "https://api.geouniq.com/v1/selections/devices?limit=3&offset=Mw%3D%3D",
            "offset": "Mw=="
        }
    }
}
```



