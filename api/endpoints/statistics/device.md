# Statistics on *Device* Resources

Endpoint to obtain [Statistics](/api/concepts/statistics.md) on [*Device*](api/resources/platform-created/device.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/statistics/devices`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Device-StatisticInput`](/api/data-models/r-statistic-input/device.md)
    
### Examlpe Request


```
curl --request POST \
  --url https://api.geouniq.com/v1/statistics/device \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"select":{"deviceBase":{"inside":{"clientAppId":["A1","A2","A3"]}},"time":{"inside":{"intervals":[{"from":{"relative":-100},"to":{"relative":0}}]}}},"segmentBy":{"deviceBase":{"inside":{"clientApp":1}},"time":{"inside":{"continuousInterval":{"count":1,"unit":"day"}}}},"compute":{"count":true}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns a [`Page`](api/general-aspects/pagination.md) of [`Device-StatisticOutput`](/api/data-models/r-statistic-output/device.md).

* **HTTP Status Code**: 200
* **Paginated**: YES
* **Body**: [`Page`](api/general-aspects/pagination.md#page-model)[`<Device-StatisticOutput>`](/api/data-models/r-statistic-output/device.md)


### Example Response Body

```json
{
	"items": [{
		"segment": {
			"deviceBase": {
				"inside": {
					"clientAppId": ["A1"]
				}
			},
			"time": {
				"inside": {
					"intervals": [{
						"from": {
							"absolute": "2017-01-01T00:00:00Z"
						},
						"to": {
							"absolute": "2017-01-01T01:00:00Z"
						}
					}]
				}
			}
		},
		"metrics": {
			"count": {
				"absolute": 200
			}
		}
	}],
	"paging": {
		"next": {
			"link": "https://api.geouniq.com/v1/statistics/devices?offset=MTAw&limit=100",
			"offset": "MTAw"
		}
	}
}
```


