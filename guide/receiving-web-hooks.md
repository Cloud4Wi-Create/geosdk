# Receiving Web Hooks

## Request performed by Geouniq platform

* **METHOD**: POST

* **HEADERS**:
	* `Content-Type:application/json`
	* `Authorization:Basic <authKey>`

> if an authentication key has been provided in the [WebHook](/api/data-models/common/hook.md#webhook), then it will be used as key to authenticate the request using the `Authorization` Header

* **BODY**

### Example body for visits related to a campaign

```json
{
	"eventType":"resourcesCreated",
	"resourcesCreated":{
		"resourceType": "campaignVisit",
		"campaignVisits":[{
			"adid":"ADID",
			"campaignID": "Campaign1",
			"startedAt":  "2020-01-01T10:00:00Z",
			"endedAt":  "2020-01-01T10:30:00Z",
			"poi": {
				"id": "poi1"
			}
		}]
	}
}
```


### Example body for impressions (expositions) related to an OOH advertising campaign

```json
{
	"eventType":"resourcesCreated",
	"resourcesCreated":{
		"resourceType": "campaignImpression",
		"campaignImpressions":[{
			"adid":"ADID",
			"campaignID": "Campaign1",
			"timestamp":  "2020-01-01T10:00:00Z",
			"poi": {
				"id": "5f6c6dae0df8000fdbab0cac"
			}
		}]
	}
}
```

