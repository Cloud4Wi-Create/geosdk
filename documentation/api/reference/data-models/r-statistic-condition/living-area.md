## LivingArea-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`LivingArea-Segment`](/api/reference/data-modelsata-models/r-segment/living-area.md) | Optional | Any valid `LivingArea-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Living Areas*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate | [`LivingArea-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/living-area.md)| Mandatory | Any valid `LivingArea-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

