## Activity-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`Activity-Segment`](/api/reference/data-modelsata-models/r-segment/activity.md) | Optional | Any valid `Activity-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Activities*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate    | [`Activity-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/activity.md)| Mandatory | Any valid `Activity-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

