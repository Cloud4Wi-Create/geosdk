## DetectedPosition-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`DetectedPosition-Segment`](/api/reference/data-modelsata-models/r-segment/detected-position.md) | Optional | Any valid `DetectedPosition-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Detected Positions*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate    | [`DetectedPosition-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/detected-position.md)| Mandatory | Any valid `DetectedPosition-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

