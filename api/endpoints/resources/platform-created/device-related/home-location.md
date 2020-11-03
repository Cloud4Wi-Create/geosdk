# Read Home Locations

Endpoint to READ [*Home Location*](api/resources/platform-created/device-related/home-location.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/homes`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`HomeLocation-Segment`](/api/data-models/r-segment/home-location.md)
    
### Examlpe Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/homes \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"deviceBase":{"inside":{"deviceId":["D1"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":{"type":"Polygon","coordinates":[[[-10.0,-10.0],[10.0,-10.0],[10.0,10.0],[-10.0,10.0],[-10.0,-10.0]]]},"properties":null}}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns a [`Page`](api/general-aspects/pagination.md) of [`HomeLocation`](/api/data-models/resources/platform-created/device-related/home-location.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](api/general-aspects/pagination.md#page-model)[`<HomeLocation>`](/api/data-models/resources/platform-created/device-related/home-location.md)

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
            "link": "https://api.geouniq.com/v1/selections/detected-positions?limit=3&offset=Mw%3D%3D",
            "offset": "Mw=="
        }
    }
}
```



