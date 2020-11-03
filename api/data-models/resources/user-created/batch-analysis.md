# Analysis

Data Model used to represent an [*Analysis*](/api/resources/user-created/analysis.md) Resource.

## Fields Specification

The `Analysis` data model contains all the fields of a [*User Created* Resource data model](/api/data-models/resources/user-created/index.md).

In addition, the following fields are contained by any kind of *Analysis* data model

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
status |`String` | Forbidden - Output Only | {`"waitingforInput"`;`"submittable"`;`"starting"`;`"running"`;`"succeeded"`;`"failed"`} | Indicates the status of the analysis.
submittedAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | Any valid [`Date`](/api/data-models/common/date.md) | The time instant when the analysis was submitted. If not submitted yet, the field will be omitted
startedAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | Any valid [`Date`](/api/data-models/common/date.md) | The time instant when the analysis started. If not started yet, the field will be omitted
endeddAt | [`Date`](/api/data-models/common/date.md) | Forbidden - Output Only | Any valid [`Date`](/api/data-models/common/date.md) | The time instant when the analysis terminated. If not terminated yet, the field will be omitted.
hook | [`Hook`](/api/data-models/common/hook.md) | Optional | Any valid [`Hook`](/api/data-models/common/hook.md) | An hook to send an alert when the analysis terminates

## Example Object

```json
{
    "id":"analysis1",
    "name":"my analysis",
    "description": "my first analysis",
    "labels": ["test"],
    "status": "succeeded",
    "startedAt": "2020-01-01T00:00:00Z",
    "submittedAt": "2020-01-01T00:01:00Z",
    "startedAt": "2020-01-01T00:02:00Z",
    "endedAt": "2020-01-01T01:00:00Z",
    "hook": {
        "type":"web",
        "web":{
            "url":"https://mydomain.com/gu-hooks/analysis"
        }
    }
}
```