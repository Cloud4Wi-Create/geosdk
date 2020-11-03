## Visit-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`Visit-Segment`](/api/data-models/r-segment/visit.md) | Optional | Any valid `Visit-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Visits*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate    | [`Visit-AggregatedMetricsCondition`](/api/data-models/r-aggregated-metrics-condition/visit.md)| Mandatory | Any valid `Visit-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

