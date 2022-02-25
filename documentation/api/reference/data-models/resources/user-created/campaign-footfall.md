# Footfall Analysis

Data Model used to represent a [*Footfall Analysis*](/api/reference/resources/resources/user-created/campaign-footfall.md) Resource.

## Fields Specificcation

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
id | `String` | Forbidden - Output Only | N.A. | The Resource ID.
createdAt | [`Date`](/api/reference/data-modelsata-models/common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name | `String` | Optional | Any `String` of length lower than 32 characters | A name for the *Footfall Analysis*
description | `String` | Optional | Any `String` of length lower than 128 characters | A description for the *Footfall Analysis*
labels | `[String]` | Optional | At most 10 `String` elements of length lower than 16 characters | A set of labels associated to the *Footfall Analysis*
type | `String` | Mandatory | {`"standard"`;`"premium"`} | Indicates whether a standard or premium [*Footfall Analysis*](/api/reference/resources/resources/user-created/campaign-footfall.md) is desired
controlGroup | [`Audience`](/api/reference/data-modelsata-models/common/audience.md) | Optional | Any valid  [`Audience`](/api/reference/data-modelsata-models/common/audience.md) | Indicates a set of devices' AIDs to be used as control group for the [*Footfall Analysis*](/api/reference/resources/resources/user-created/campaign-footfall.md). If not provided, the Target Audience set for the [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) will be used as control group, if any, otherwise no comparison with a control group will be performed.
exposedPeriod | [`Time-Segment`](/api/reference/data-modelsata-models/d-segment/time.md) | Optional | Any valid [`Time-Segment`](/api/reference/data-modelsata-models/d-segment/time.md) | If provided, indicates the time period to be used to identify visits for the set of exposed Users. If not provided, the period set for the related [*Campaign*](/api/reference/resources/resources/user-created/campaign.md) Resource will be used
controlGroupPeriod | [`Time-Segment`](/api/reference/data-modelsata-models/d-segment/time.md) | Optional | Any valid [`Time-Segment`](/api/reference/data-modelsata-models/d-segment/time.md) | If provided, indicates the time period to be used to identify visits for the control group. If not provided, the same period used for exposed Users will be also used for the control group.
hook | [`Hook`](/api/reference/data-modelsata-models/common/hook.md) | Optional | Any valid [`Hook`](/api/reference/data-modelsata-models/common/hook.md) | An hook that will be used to send an alert when the analysis terminates

## Example Object

```json
{
  "id": "footfallAnalysis1",
  "name": "FF analysis for my campaign",
  "description": "A footfall analysis for my first campaign",
  "type": "standard",
  "controlGroup": {
    "type": "audienceBuilder",
    "analysisID": "abAnalysis1"
  },
  "exposedPeriod": {
    "intervals": [{
        "from":{
            "absolute":"2020-05-01T00:00:00Z"
        },
        "to":{
            "absolute":"2020-05-10T00:00:00Z"
        }
    }]
  },
  "controlGroupPeriod": {
    "intervals": [{
        "from":{
            "absolute":"2020-04-01T00:00:00Z"
        },
        "to":{
            "absolute":"2020-05-01T00:00:00Z"
        }
    }]
  },
  "hook": {
    "type": "web",
    "web": {
      "url": "https://mydomain.com/gu-hooks/ff-analysis"
    }
  }
}
```
