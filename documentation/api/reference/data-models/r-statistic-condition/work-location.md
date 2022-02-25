## WorkLocation-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`WorkLocation-Segment`](/api/reference/data-modelsata-models/r-segment/work-location.md) | Optional | Any valid `WorkLocation-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Work Locations*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate | [`WorkLocation-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/work-location.md)| Mandatory | Any valid `WorkLocation-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

