# User-created Resources


Data Models used to represent [User-created](/api/concepts/resource-definition.md) Resources.

All these Data Models contain the following fileds.

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
id | `String` | Forbidden - Output Only | N.A. | The Resource ID.
createdAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name | `String` | Optional | Any `String` of length lower than 32 characters | A name for the Resource useful to recall it in a [`UserCreatedResource-Segment`](/api/data-models/common/user-created-resource-segment.md).
description | `String` | Optional | Any `String` of length lower than 128 characters | A description for the Resource.
labels | `[String]` | Optional | At most 10 `String` elements of length lower than 16 characters | A set of labels useful to recall the Resource in a [`UserCreatedResource-Segment`](/api/data-models/common/user-created-resource-segment.md).

```json
{
    "id":"resource1",
    "name":"my resource",
    "description": "my first resource",
    "labels": ["test"]
}
```

According to the set of defined [User-created Resources](/api/resources/user-created/index.md), the following Data Models are defined.

* [Campaign](/api/data-models/resources/user-created/campaign.md)
* [Audience Analysis](/api/data-models/resources/user-created/audience-analysis.md)
* [Footfall Analysis](/api/data-models/resources/user-created/campaign-footfall.md)
* [Trigger](/api/data-models/resources/user-created/trigger.md)
* [Hook](/api/data-models/resources/user-created/hook.md)
