* [Documentation Home](../../../../../../README.md)
    * [Web API](../../../../../index.md)  
      * [Reference](../../../../index.md)  
        * [Endpoints](../../../index.md)
           * [Platform-created resources endpoints](../../index.md)
                * [Device-related resources endpoints](../index.md)
                    * [Home Location endpoints](index.md)
                    
# Home Location Selection Endpoint

Endpoint to get a [Selection](../../../../../concepts/resource-selection.md) of 
[Home Location resources](../../../../resources/platform-created/device-related/home-location.md).

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/homes`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`HomeLocation-Selection`](../../../../data-models/r-selection/home-location.md)
    
### Example Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/homes \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"deviceBase":{"inside":{"deviceId":["D1"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":{"type":"Polygon","coordinates":[[[-10.0,-10.0],[10.0,-10.0],[10.0,10.0],[-10.0,10.0],[-10.0,-10.0]]]},"properties":null}}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/reference/general-aspects/auth.md).

## Successful Response


A Successful response returns a [`Page`](../../../../general-aspects/pagination.md) 
of [`HomeLocation`](../../../../data-models/resources/platform-created/device-related/home-location.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](../../../../general-aspects/pagination.md)[`<HomeLocation>`](../../../../data-models/resources/platform-created/device-related/home-location.md)

### Example Response Body

```json
{
    "items": [
        {
            "device": {
                "id": "59ca6c1a05caf00001c4603b"
            },
            "primary": true,
            "geo": {
                "Lat": 48.82708269171417,
                "Lng": 2.4759369157254696
            }
        },
        {
            "device": {
                "id": "59915edf1788ae000169c949"
            },
            "primary": true,
            "geo": {
                "Lat": 48.82347445003688,
                "Lng": 2.47997397556901
            }
        }
    ],
    "paging": {
        "next": {
            "link": "https://api.geouniq.com/v1/selections/homes?limit=3&offset=Mw%3D%3D",
            "offset": "Mw=="
        }
    }
}
```



