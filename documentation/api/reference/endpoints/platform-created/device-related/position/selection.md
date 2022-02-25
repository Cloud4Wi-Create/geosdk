* [Documentation Home](../../../../../../README.md)
    * [Web API](../../../../../index.md)  
      * [Reference](../../../../index.md)  
        * [Endpoints](../../../index.md)
           * [Platform-created resources endpoints](../../index.md)
              * [Device-related resources endpoints](../index.md)
                * [Position endpoints](index.md)
                 
# Position Selection Endpoint

Endpoint to get a [Selection](../../../../../concepts/resource-selection.md) of 
[Position resources](../../../../resources/platform-created/device-related/position.md).

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/detected-positions`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Position-Selection`](../../../../data-models/r-selection/detected-position.md)
    
### Example Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/detected-positions \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"deviceBase":{"inside":{"deviceId":["D1"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":{"type":"Polygon","coordinates":[[[-10.0,-10.0],[10.0,-10.0],[10.0,10.0],[-10.0,10.0],[-10.0,-10.0]]]},"properties":null}}},"time":{"inside":{"intervals":[{"from":{"absolute":"2016-01-01T00:00:00Z"},"to":{"absolute":"2016-01-02T00:00:00Z"}}]}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](../../../../general-aspects/auth.md).

## Successful Response

A Successful response returns a [`Page`](../../../../general-aspects/pagination.md#page-model) of [`Position`](../../../../data-models/resources/platform-created/device-related/detected-position.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../../general-aspects/pagination.md#page-model)[`<Position>`](../../../../data-models/resources/platform-created/device-related/detected-position.md)

### Example Response Body

```json
{
    "items": [
        {
            "device": {
                "id": "5832ed167e6b5e00017a4a3b"
            },
            "detectedAt": "2017-08-28T16:23:34Z",
            "geo": {
                "Lat": 50.445718,
                "Lng": -3.560455
            },
            "speed": 3.2
        },
        {
            "device": {
                "id": "5832ed167e6b5e00017a4a3b"
            },
            "detectedAt": "2017-08-28T16:24:05Z",
            "geo": {
                "Lat": 50.446893,
                "Lng": -3.559082
            },
            "speed": 3.2
        },
        {
            "device": {
                "id": "5832ed167e6b5e00017a4a3b"
            },
            "detectedAt": "2017-08-28T16:24:20Z",
            "geo": {
                "Lat": 50.447725,
                "Lng": -3.55773
            },
            "speed": 2.3
        }
    ],
    "paging": {
        "next": {
            "link": "https://api.geouniq.com/v1/selections/detected-positions?limit=3&offset=Mw%3D%3D",
            "offset": "Mw=="
        }
    }
}
```



