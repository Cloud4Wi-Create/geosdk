# Create Trigger

Endpoint to CREATE *Trigger* Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/project/triggers`
* **Path parameters:** None
* **Query String parameters:** None
* **Body:** [`Trigger`](/api/data-models/resources/user-created/trigger.md)
    
### Examlpe Request

<iframe src="//api.apiembed.com/?source=https://www.dropbox.com/s/ly3u579mtktifxv/create.json?dl=1&targets=shell:curl,node:unirest,java:unirest,python:requests,php:curl,ruby:native,objc:nsurlsession,go:native,java:okhttp,swift:nsurlsession" frameborder="0" scrolling="no" width="100%" height="500px" seamless></iframe>

```
curl --request POST \
  --url https://api.geouniq.com/v1/project/triggers \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"My First Trigger","description":"A simple geofence for Conad Roma 1. Active only during work hours. Inactive during the weekend. Set for each Android device","labels":["geofence","conad","roma1","android"],"status":{"enabled":true},"activeOn":{"intervals":[{"from":{"absolute":"2017-01-31T00:00:00Z"},"to":null}],"periodicity":{"hoursOfTheDay":[10,11,12,13,14,15,16,17,18,19,20],"daysOfTheWeek":["monday","tuesday","wednesday","thursday","friday"]}},"targets":{"select":{"osName":["Android"]},"segmentBy":{"device":1}},"eventDefinition":{"nodeType":"visit","visit":{"select":{"spatialGranularity":{"inside":["bestFit"]},"space":{"inside":{"savedAreas":{"name":["Conad Roma Est"]}}},"time":{"intersect":{"intervals":[{"from":{"relative":0},"to":{"relative":0}}]}},"duration":{"gte":60}},"evaluate":{"count":{"gt":0}}}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

## Successful Response

A Successful response returns the created *Trigger* Resource.

* **HTTP Status Code**: 201
* **Paginated**: NO
* **Body**: [`Trigger`](/api/data-models/resources/user-created/trigger.md)





