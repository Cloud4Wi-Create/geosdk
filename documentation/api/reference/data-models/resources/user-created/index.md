* [Documentation Home](../../../../../../README.md)  
  * [Web API](../../../../index.md)  
    * [Reference](../../../index.md)
        * [Data models](../../index.md)
            * [Resources Data models](../index.md)

# User-created Resource


Partial data model common to all [User-created](../../../../concepts/resource-definition.md) Resources.

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
id | `String` | Forbidden - Output Only | N.A. | The Resource ID.
createdAt | [`DateTime`](../../common/date.md) | Forbidden - Output Only | N.A. | The date and time when the Resource was created.
name | `String` | Optional | Any `String` of length lower than 32 characters | A name for the Resource useful to recall it in a [`UserCreatedResource-Segment`](../../common/user-created-resource-segment.md).
description | `String` | Optional | Any `String` of length lower than 128 characters | A description for the Resource.
labels | `[String]` | Optional | At most 10 `String` elements of length lower than 16 characters | A set of labels useful to recall the Resource in a [`UserCreatedResource-Segment`](../../common/user-created-resource-segment.md).

```json
{
    "id":"resource1",
    "name":"my resource",
    "description": "my first resource",
    "labels": ["test"]
}
```

According to the set of defined [User-created Resources](../../../resources/user-created/index.md), the following Data Models are defined.

* [Trigger](trigger.md)
* [Campaign](campaign.md)
* [Batch Analysis](batch-analysis.md)
    * [Insight Analysis](insights-analysis.md)
    * [Audience Analysis](audience-analysis.md)
    * [Footfall Analysis](campaign-footfall.md)

