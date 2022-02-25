## HomeLocation-StatisticCondition

Name | Type | Mandatory/Optional | Allowed Values | Description
------------|------------|------------|------------|------------
select    | [`HomeLocation-Segment`](/api/reference/data-modelsata-models/r-segment/home-location.md) | Optional | Any valid `HomeLocation-Segment` object **without the field `"deviceBase"`**. `null` and empty Object allowed | Indicates the  [Segment of *Home Locations*](/api/concepts/resource-definition.md#resource-segment) on which the Aggregated Metrics Condition must be evaluated.
evaluate | [`HomeLocation-AggregatedMetricsCondition`](/api/reference/data-modelsata-models/r-aggregated-metrics-condition/home-location.md)| Mandatory | Any valid `HomeLocation-AggregatedMetricsCondition` object | Indicates the algebraic condition(s) that have to be evaluated (for one or more Aggregated Metrics) for the Condition to hold true.

```json
```

