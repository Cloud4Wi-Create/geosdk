# Create Footfall Analysis

Endpoint to CREATE [*FootfallAnalysis*](/api/resources/user-created/campaign.md) Resources.

## Request

* **HTTP Method:** `POST`
* **Path:** `/campaigns/<CAMPAIGN_ID>/footfall`
* **Path parameters:**
    *  **CAMPAIGN_ID**: The ID of the specific *Campaign* Resource for which the *FootfallAnalysis* is desired, as provided in the [`"id"`](api/data-models/resources/user-created/campaign.md) field
* **Query String parameters:** None
* **Body:** [`FootfallAnalysis`](/api/data-models/resources/user-created/campaign-footfall.md)
    
### Examlpe Request

```
curl --request POST \
  --url https://api.geouniq.com/v1/campaign \
  --header 'authorization: Bearer <ACCESS_TOKEN>' \
  --header 'content-type: application/json' \
  --data '{"name":"FF analysis for my campaign","description":"A footfall analysis for my first campaign","type":"standard","controlGroup":{"type":"audienceBuilder","analysisID":"abAnalysis1"},"exposedPeriod":{"intervals":[{"from":{"absolute":"2020-05-01T00:00:00Z"},"to":{"absolute":"2020-05-10T00:00:00Z"}}]},"controlGroupPeriod":{"intervals":[{"from":{"absolute":"2020-04-01T00:00:00Z"},"to":{"absolute":"2020-05-01T00:00:00Z"}}]},"hook":{"type":"web","web":{"url":"https://mydomain.com/gu-hooks/ff-analysis"}}}'
```

> Make sure to substitute `<ACCESS_TOKEN>` with a valid access token obtained as described [here](/api/auth.md).

> Make sure to substitute `<CAMPAIGN_ID>` with a valid ID of a [previously created *Campaign* resource](/api/endpoints/resources/user-created/campaign/create.md).

## Successful Response

A Successful response returns the created *FootfallAnalysis* Resource.

* **HTTP Status Code**: 201
* **Paginated**: NO
* **Body**: [`FootfallAnalysis`](/api/data-models/resources/user-created/campaign-footfall.md)





