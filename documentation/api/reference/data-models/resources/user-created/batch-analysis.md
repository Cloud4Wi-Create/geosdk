# Batch Analysis

Data Model common to all [*Batch Analysis*](../../../resources/user-created/batch-analysis.md) Resources.

## Fields Specification

The `BatchAnalysis` data model contains all the fields of a [*User Created* Resource data model](../../resources/user-created/index.md).

In addition, the following fields are contained by any kind of *Analysis* data model

Name        | Type      | Mandatory/Optional | Allowed Values | Description
------------|----------|----------------|-----------|--------------
status |`String` | Forbidden - Output Only | {`"waitingforInput"`;`"submittable"`;`"starting"`;`"running"`;`"succeeded"`;`"failed"`} | Indicates the status of the analysis.
submittedAt | [`Date`](../../common/date.md) | Forbidden - Output Only | Any valid [`Date`](../../common/date.md) | The time instant when the analysis was submitted. If not submitted yet, the field will be omitted
startedAt | [`Date`](../../common/date.md) | Forbidden - Output Only | Any valid [`Date`](../../common/date.md) | The time instant when the analysis started. If not started yet, the field will be omitted
endedAt | [`Date`](../../common/date.md) | Forbidden - Output Only | Any valid [`Date`](../../common/date.md) | The time instant when the analysis terminated. If not terminated yet, the field will be omitted.
hook | [`Hook`](../../common/hook.md) | Optional | Any valid [`Hook`](../../common/hook.md) | An hook to send an alert when the analysis terminates

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
    "endedAt": "2020-01-01T01:00:00Z",
    "hook": {
        "type":"web",
        "web":{
            "url":"https://mydomain.com/gu-hooks/analysis"
        }
    }
}
```
