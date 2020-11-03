# Read Work Locations

Endpoint to READ [*Work Location*](api/resources/platform-created/device-related/work-location.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/selections/works`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`WorkLocation-Segment`](/api/data-models/r-segment/work-location.md)
    
### Examlpe Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/selections/works \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"deviceBase":{"inside":{"deviceId":["D1"]}},"space":{"inside":{"explicitArea":{"type":"Feature","geometry":{"type":"Polygon","coordinates":[[[-10.0,-10.0],[10.0,-10.0],[10.0,10.0],[-10.0,10.0],[-10.0,-10.0]]]},"properties":null}}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns a [`Page`](api/general-aspects/pagination.md) of [`WorkLocation`](/api/data-models/resources/platform-created/device-related/work-location.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](api/general-aspects/pagination.md#page-model)[`<WorkLocation>`](/api/data-models/resources/platform-created/device-related/work-location.md)

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



