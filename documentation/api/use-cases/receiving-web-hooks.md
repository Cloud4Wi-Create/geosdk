* [Documentation Home](../../README.md)
   * [Web API](../index.md)
        * [Use Cases](index.md)
        
# Receiving Web Hooks

## Request performed by Geouniq platform

* **METHOD**: POST

* **HEADERS**:
	* `Content-Type:application/json`
	* `Authorization:Basic <authKey>`

> if an authentication key has been provided in the [WebHook](../reference/data-models/common/hook.md#webhook), then it will be used as key to authenticate the request using the `Authorization` Header

* **BODY**

The Body will contain a [`HookEvent`](../reference/data-models/common/hook-message.md) object,
which varies according to the specific event.

> Example body when a new [TriggerLogs](../reference/resources/platform-created/triggerlog.md) is created
 
````json
{
	"eventType": "resourcesCreated",
	"resourcesCreated": {
		"resourceType": "triggerLog",
		"triggerLogs": [{
			"trigger": "5964b7d5d5f455000133fe3e",
			"device": {
				"id": "device1",
				"clientAppId": "app1",
				"customId": "my device",
				"idfa": "550e8400-e29b-41d4-a716-446655440000"
			},
			"event": {
				"type": "geofence",
				"geofence": {
					"type": "enter",
					"time": "2021-01-01T00:00:00Z"
				}
			}
		}]
	}
}
````

> Example body when new CampaignVisits are created

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


### Example body when new CampaignImpression are created

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

