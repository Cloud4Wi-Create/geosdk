# Pagination

This API uses pagination according to the scheme described in this section. 
Pagination is used for all the endpoints which allow to access a collection of Resources.
Endpoints that return a paginated response always return a body with a `Page` of Items of the same type `T`, which is indicated as `Page<T>`.


## Page Model

Models a `Page` of Items of a given type `T`

Name| Type | Description
----------|----------|----------
items | `[T]` | An array of resources of a given type `T`.
paging | `JSON` | Contains pagination info.
paging.next |`JSON` |Contains info to access the next page.
paging.next.offset |`String`| The offset to be provided as query string parameter to access the next page
paging.next.link |`String`| The whole URL to access the next page

### Example Response Body

```json
{
    "items": [{
        "device" : {
            "id": "56fa6815af4ecd00010b000a",
            "customId": "My first device",
            "token": "TOKEN"
        },
        "detectedAt": "2016-03-11T08:31:07Z",
        "geo": {
            "lat": 43.7228778,
            "lng": 10.3991758
        },
        "speed": 5.0
    }],
    "paging": {
        "next": {
            "link": "https://api.geouniq.com/v1/statistics/positions?offset=MTAw&limit=100",
            "offset": "MTAw"
        }
    }
}
```

## Controlling pagination

All the endpoints that return a paginated response accept the following query string parameters to control which items must be returned.

Name| Type | Default value | Allowed Value | Description
----------|----------|----------|----------|----------
offset | `String` | `""` | Only specif values that are provided in the response to a previous request | Encodes an offset to access resources belonging to a specific page
limit | `Integer` | Eendpoint dependent | Any `Integer` lower than the default value | Indicates the number of items that have to be returned in the response.

> Example Request URL: `https://api.geouniq.com/v1/endpoint-specific-path?limit=50&offset=MTAw`

When making requests to a paginated endpoint, the first request must not contain any value for `offset`.
Then, to access the next page, the value received in `"paging.next.offset"` has to be provided for `offset` or the whole URL in `"paging.next.link"` as to be used as new URL.

> If the endpoint provides for a body, then the same body as the original request should be provided on successive requests too. Otherwise, the returned Items will be incorrect

When the last page will be accessed, the response will contain `"paging.next": null`

