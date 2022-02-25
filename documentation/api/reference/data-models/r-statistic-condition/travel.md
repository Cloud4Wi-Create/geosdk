## Travel-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`Travel-Segment`](/api/reference/data-modelsata-models/r-segment/travel.md) | Optional | Any valid `Travel-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Travels*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate | [`Travel-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/travel.md)| Mandatory | Any valid `Travel-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

